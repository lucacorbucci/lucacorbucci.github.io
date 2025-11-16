---
author: lucacorbucci
title: "Notes on Transformers"
date: 2025-11-04
description:
math: true
draft: true
---

{{< katex >}}

In the past few months, I've started learning more about Transformers architecture and LLMs. I already had some knowledge about Transformers because of a class I took during my master. However, some years passed since then and a lot of things changed (LLMs did not exist back then). Therefore, I decided to start learning Transformers from scratch using different resources that I'll list at the end of this post. 

In this post I want to summarize some of the things I learned about Transformers for two main reasons: first, to have a reference for myself in the future; second, writing helps me to better understand concepts. I'll try as much as I can to include some images and figures drawn by me that could help in understanding the concepts.

# A bit of history

In 2017 Vaswani et al. published the paper "Attention Is All You Need", which introduced the Transformer architecture and revolutionized the field of Natural Language Processing (NLP). 
The transformer architecture went beyond the previous architectures used in NLP, such as Recurrent Neural Networks (RNNs). 

![The architecture of a RNN, image from Wikipedia](/img/stories/6/rnn.png)

The latter, before the Transformer, were the state-of-the-art models for classification, multi classification and text generation tasks. However, they had some limitations, the computation was very slow because of their sequential nature i.e. to compute the output you had to process all the input token before and compute the hidden states before. This hidden state is the second problem of RNNs, in fact, it tends to forget the previous information coming from tokens that are far away in the sequence. This problem is called vanishing gradient and it makes RNNs unable to capture long-term dependencies in the data.

![Transformer architecture from the original paper "Attention Is All You Need"](/img/stories/6/paper.png)

The idea that made transformer so successful is the attention mechanism. This mechanism allows to solve the long range dependencies problem by having direct links between all the tokens in the input sequence. Specifically, Transformer rely on a self-attention mechanism that allows each token to attend to all the other tokens in the sequence, regardless of their position.

In the next sections I'll try to explain the main components of the Transformer architecture and how they work.

# Transformer Architecture

The original Transformer architecture introduced in the paper "Attention Is All You Need" consists of an encoder-decoder structure. 
In the case of machine translation, the encoder takes as input a sequence of words (I'll also call them tokens). Inside the encoder, the attention mechanism allows to compute the representation of the tokens in the text as a function of the other tokens in the sequence. 
The encoder then, outputs a representation of the input sequence that is passed to the decoder. 
The decoder takes as input the representation from the encoder and generates the output sequence one token at a time.

![](/img/stories/6/architecture.png)

## The Attention Mechanism

### Self Attention



### Multi-Head Attention



### Masked Attention

![](/img/stories/6/masked.jpg)

The Masked Attention (also known as Causal Attention) is used in the decoder part of the Transformer. In the original Transformer correspond to the Masked Multi-Head Attention block (see figure above). 
Masked Attention ensures that the output for a certain position in the sequence is only based on the known previous output.
For instance, if we have the sentence "The cat is sleeping", we first mask the contribution of all the words, then we unmask the first word "The" and compute its representation, then we unmask the second word "cat" and compute its representation using also the representation of "The", and so on.
Modern LLMs like GPT are trained using only the decoder part of the Transformer with Masked Attention to generate text autoregressively, i.e. one token at a time from left to right.

This is a simple implementation of Masked Attention in PyTorch:

```

```

## Encoder

## Decoder

## A simple example

### The input sequence

### Tokenization

### Embeddings

### Positional Encoding

Differently from RNNs, Transformers do not have a built-it notion of position of the tokens. Therefore, it is needed to add dedicated embedding to encode the position of each token in the input sequence. 

There have been different approaches to encode positional information. These first proposal are called Absolute Positional Embeddings. A first idea from the ["Attention is all you need"](https://arxiv.org/abs/1706.03762) paper is to have a positional embedding for each position, each one is summed to the embeddding of each token. This positional embedding can be both learned or static. When it is learned, it depends a lot on what you have in input. Moreover, you can only learn position embeddings up to the lenght of the sequence of your dataset. This means that at inference time, if you have a longer sequence, you won't have positional embeddings for the new positions.

The second idea is to have an arbitrary formula for each positional embedding, this is pre-determined and does not depend on the data. The most famous one is the sinusoidal positional encoding introduced in the [original Transformer paper](https://arxiv.org/abs/1706.03762).

![](/img/stories/6/sinusoidal.png)

As show in the image above, each position in the vector has a value that depends on the position of the token and on a value $w = 10000^{-\frac{2i}{d_{model}}}$. Specifically, as shown above, the even positions of the vector are computed using the sine function while the odd positions using the cosine function. This elegant solution allows to represent positions so that tokens that are closer should be more related than tokens that are far away.

Now, we have to remember a trigonometry formula: $$cos(a-b) = cos(a)cos(b) + sin(a)sin(b)$$

Having this in mind, we can consider position m and n and compute the dot product between their positional encodings:

$$PE(m, 2i+1) \cdot PE(n, 2i+) = cos(mw_i)cos(nw_i) + sin(mw_i)sin(nw_i) = cos((m-n)w_i)$$

If we consider all the dimensions of the positional encoding, we first compute the product of each position and then we sum them. This sum is the sum of multiple $cos((m-n)w_i)$ terms.
If we consider that $cos(0) = 1$ and $cos(1) = 0$ then we can say that if m and n are close ($m \sim n), the dot product will be high because most of the terms will be close to 1. This means that this solution captures the notion of proximity. On the other hand, if m and n are far away, the dot product will be low because most of the terms will be close to 0.

The results obtained with this solution are similar to the learned positional embeddings but with the advantage of being able to generalize to longer sequences. 

Initially, in the first attention paper, the resulting positional encoding was summed to the token embeddings. Recently, this changed, the positional embeddings are not summed anymore to the token embeddings but are instead used in the self-attention computation. This solution is called Relative Positional Embeddings, one first proposal is the T5 Bias model. T5 introduces a bias in the attention computation that depends on the distance between the tokens:

$$Softmax(\frac{QK^T + B}{\sqrt{d_k}} + bias(m, n))$$

where bias(m, n) represents the distance between token m and n. If two tokens are far away, the bias will be negative, instead if they are close the bias will be positive. Here, the problem of this approach could rely on the way the bias is learned. The bias could be overfitted to the training data and not generalize well to new sequences of tokens.

Most papers nowadays use [Rope Embeddings (RoPE)](https://arxiv.org/abs/2104.09864). This approach works again in the self-attention computation. The idea is to rotate the query and key vectors using a rotation matrix.

As in the image above, suppose that we are considering the token in position m and the token in position n. On the left, we have the query vector of the position m and on the right the key vector of position n. 
Both the two vectors are rotated by a quantity that is function of the position itself. Because of this rotations, ROPE encodes the relative distance between the two tokens when we compute the dot product between the two vectors:
$$q_m k_n^T = X_m W_q R_{\theta, n-m} W_k^T X_n^T$$

The dot product above depends on the relative distance between the two tokens (n-m) because of the rotation matrix $R_{\theta, n-m}$.



### Attention computation

### Feed Forward Network

### Using the decoder: Generating text autoregressively

### Putting everything together



# Conclusions



# References

- [CME 295 - Transformers & Large Language Models](https://cme295.stanford.edu/syllabus/)
- [CS336: Language Modeling from Scratch](https://stanford-cs336.github.io/spring2025/)
- [Understanding and Coding Self-Attention, Multi-Head Attention, Causal-Attention, and Cross-Attention in LLMs](https://magazine.sebastianraschka.com/p/understanding-and-coding-self-attention)
