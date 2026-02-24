---
author: lucacorbucci
title: "Notes on LLMs papers"
date: 2026-02-17
description:
math: true
draft: true
---

**This is a continuously updated post with notes on LLMs papers that I read. The different sections correspond to different models and are sorted based on the reading date. These are notes taken while reading the technical reports and may contain typos or errors.**


## GLM-4.5 

**Report link**: [GLM-4.5: Agentic, Reasoning, and Coding (ARC) Foundation Models](https://arxiv.org/abs/2508.06471)

**Main contributions**: GLM 4.5 is a MoE LLM with 335B parameters and 32B activated parameters. It is an hybrid reasoning model able to answer both with immediate responses and with a more complex reasoning process. 

**Training**: First a pre-training composed of two phases: 1) a General Pre-training phase on documents from web pages and 2) a Code & reasoning continual pre-training phase with data from GitHub, math and science. Then they did a mid-training phase using 1) data from GitHub repositories, PR, concatenated code 2) Reasoning traces 3) Long context documents. 
Then, they did a post-training phase with SFT to 1) learn basic chat abilities, reasoning and tool use, 2) learn to be more general, they balance training data with long COT with answers that are shorter to train a model that is an hybrid reasoning model able to answer both with immediate responses and with a more complex reasoning process. Data for SFT is generated using Agents, MCP, tool calls, traces generation and then evaluate the quality of the data.
A second post-training phase is done with RL. They add capabilities in domains that demands deduction and problem solving. The RL stage is done using a 2 stage approach, first a stage with moderate difficult data and then with extremely difficult data.

**Other Notes**: When developing the model they identified three critical capabilities to measure generalist models: Agentic abilities, REasoning for multi step problems and Coding skills. In terms of model architecture, it is deeper compared with Kimi K2 and Deepseek because they found that deeper models are better in terms of reasoning. 

## Minimax M1

**Report link**: [MiniMax-M1: Scaling Test-Time Compute Efficiently with Lightning Attention](https://arxiv.org/abs/2506.13585)

**Main contributions**: MiniMax-M1 is a LLM that uses a lighning attention mechanism and a hybrid MoE architecture to scale test-time compute efficiently (50% less of the FLOPs at a generation length of 64K tokens compared with Deepseek R1). They also proposed a new RL algorithm called CISPO.

**Training**: Minimax M1 is based on the previous model called MiniMax-Text-01, they continue prepretraining it using 7.5T tokens. This stage is done to improve the model quality by training it on more high quality data and to extend the context length. Then, they did a SFT stage to instill reasoning into the model by showing CoT reflections.SFT is followed by a RL stage.

**Other Notes**: Attention is a quadratic problem. There are a few mitigations 1) Sparse attention 2) Linear Attention 3) Linear attention with weight decay 4) State space models. These approaches have not been validated in real large scale reasoning models. They propose MiniMax M1 that instead is based on a hybrid MoE architecture and on Lightning Attention wich is an implementation of a linear attention variant. In the model they have a traditional transformer block (with standard attention) every seven transnormer blocks (which use the lightning attention). This is why the architecture is considered hybrid.
Their architeture consumes 50% less of the FLOPs at a generation length of 64K tokens compared with Deepseek R1.

In the paper they propose a new RL algorithm called CISPO. Consider the PPO objective:

![PPO objective](/img/stories/LLMs/Screenshot%202026-02-17%20at%2016.57.20.png)

In the PPO objective, a clipping operation is used to stabilize training, if a specific token probability changes too much then the gradient is clipped. The min operation then returns the minimum between an unclipped value and a clipped value. When the minimim is the clipped value then the gradient is zero. This means that if the probability of a token changes too much then the model stops learning from that token. This is a problem because it can lead to a situation where the model stops learning from less common tokens associated with reflective behaviours such as "However", "Wait", "Aha". These tokens are crucial to facilitate scalable RL and they have a high importance sampling score because they represent a fork in the reasoning path.
Therefore they propose CISPO, a new RL algorithm that is based on PPO but it has a different clipping mechanism. 
![CISPO objective](/img/stories/LLMs/Screenshot%202026-02-17%20at%2017.03.18.png)
The difference is that in CISPO the clipping do not cancel the gradient because outside of the clipping there is still a log term that allows the model to learn. When computing the derivative, the gradient is not zero in this case, therefore the model can still learn from tokens that have a high importance sampling score. Differently from PPO that loses the $\theta$, CISPO scales the it.

Thanks to the use of the Lightning attention, they also show that MiniMax M1 can scale output length efficiently. Originally, the model was trained with a output length of 40K tokens, then they extended this to 80K using RL. This result is achieved thanks to the use of the Lightning attention that offers a near linear scaling. This Lightning attention is also useful in the inference phase during RL as it allows to efficiently generate new tokens used in the evaluation of the policy. 



## Qwen3-Omni

**Report link**: [Qwen3-Omni Technical Report](https://arxiv.org/abs/2509.17765)

**Main contributions**: They update their multimodal model based on the Thinker-Talker architecture starting from Qwen3. The thinker and talker are MoE now. They have a new audio encoder and improvements in the voice generation in the talker. The model supports up to 40 minutes audio input and they expanded the language coverage too. Lastly, the thinker model has now reasoning abilities. 

**Training**: The training process includes both unimodal and cross-modal data from the early pre-training stages. In the pre-training, they start with 1) training of the encoders while keeping the LLM frozen, 2) unfreeze the LLM while training with multimodal data and 3) use longer inputs to make the model more stabile and aware of the new data types. 
In the post-training, the thinker is first trained using SFT to learn downstream tasks, in a second phase they use first an off-policy distillation, given a teacher reasoning model they teach the model how to reason. Then there is a second on-policy distillation phase where the student generates responses and then logits are aligned with the teacher model. The last phase is RL using GSPO to enhance model capabilities. 
For the talker, in the post-training phase, they start the training with a lot of data performing a continual pre-training, then they have a DPO phase with preferences sampled from different multilingual speech samples. Lastly they have a speaker fine tuning phase. 

**Other Notes**: They want to show how to train a multimodal model that can achieve parity across all modalities (similar accuracy without performance degradation). Both the thinker and the talker are now MoE models. The talker, instead of receiving the hidden state produced by the thinker, receives directly the embeddings of the text input or the latent representations of the multimodal features. The talker is conditioned on the thinker outputs then it learns a complete representation of acoustic details, lastly, a convnet reconstructs this information into the output.

The other new feature is the Audio Transformer. They have trained an audio encode-decoder, a transformer based auto regressive model. Now they have this encoder to encode the input audio, a Qwen tokenizer for text and a Vision encoder from Qwen3-VL for images. 

## Qwen2.5-Omni

**Report link**: [Qwen2.5-Omni Technical Report](https://arxiv.org/abs/2503.20215)

**Main contributions**: They propose a Thinker-Talker architecture for Multimodal LLMs. The Thinker is an LLM that generates text. Its outputs go to the talker who is an autoregressive model that uses this representation to produce audio tokens as outputs. Moreover they introduce a new position embedding approach called TMRoPE.

**Training**: The pre-training is done in 3 parts: 1) vision ancoder and audio encoder trainign with frozen LLM 2) training of all the parameters using multimodal data 3) training with data with longer length to improve model ability on longer sequences. In the post-trainign phase, the talker is trained with 1) a first phase to learn context continuation (speech continuation task through next token predictions), 2) DPO to improve stability of speech generation (they use a dataset with <input text, good generated answer, bad generated answer>) and 3) a last phase to improve speech naturaleness and control on the speech responses and voices. 

**Other Notes**: Qwen 2.5-Omni is a multimodal LLM that jointly trains on different data modalities while ensuring that when you train on text you do not reduce the quality of the other data modalities and viceversa. Moreover, they want to ensure that the model is able to have real time understanding of multimodal information and efficient audio output streaming. 
To do this introduces a new embedder architecture called TMRoPE, a Thinker-Talker architecture and use a dual track auto-regressive model that generate speech tokens and a second model that convert them into waveform to enable streaming audio.

![Qwen2.5-Omni architecture](/img/stories/LLMs/Screenshot%202026-02-20%20at%2012.04.37.png)

The model is based on a new Thinker-Talker architecture. The thinker is an LLM responsible for processing and understanding inputs from text, audio and video. This is a transformer decoder with an encoder for audio and images. The thinker generates text embedding that must also encode information about context tone and attitude so that the talker can generate voice accordingly. The talker instead is a dual track autoregressive transformer decoder, this means that the transformer generates both the text and the sound of the text (with discrete tokens representing the sound). The talker receives the thinker representation adn then generates the output.

They also propose a new position embedding approach that is based on the RoPE called TMRope. This is used to include positional information. TMRope encodes information using 3 components: temporal, height and width. The temporal component is used to know when the thin happens, the height and width are used to know the position. For instance, for text, you have an increasing temporal ID while the width and the height are constant. For images, the temporal ID is constant for the different parts of the image while the width and height are different, representing the token positions in the image. For audio, a new temporal ID is assigned every 40ms. For videos: a mix of audio and images, audio is threated with one position ID every 40ms while the video is split into images with position ID increasing for each image. Width and height follow the same logic as images. 
To represent video with audio, they have a time interleaving method, they interleave video information with audio information (video-audio-video-audio).

To guarantee a quick inference and real time understanding/output, they use chunked-prefills. Instead of processing the whole input, they split it into chunks of 2 seconds so that the model starts thinking while the user is still talking. They use a sliding window attention for human voice creation because they can reduce computation needed by looking only at a limited context. 




## NVIDIA Nemotron 3

**Report link**: 

**Main contributions**:

**Other Notes**: 

## Kimi K2 and K2.5

**Report link**: 

**Main contributions**:

**Other Notes**: 



## GPT3: "Language Models are Few-Shot Learners"

