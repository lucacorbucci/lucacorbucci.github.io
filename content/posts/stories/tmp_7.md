---
author: lucacorbucci
title: "Notes on Mixture of Experts"
date: 2025-11-04
description:
math: true
draft: true
---

{{< katex >}}

Mixture of Experts (MoE) is an architecture that aims to increase the model performance while keeping the inference cost low. This architecture has been used in some recent LLMs such as Qwen and Deepseek but it is now also used in a lot of other models.
Differently from the standard Transformer, you take the original Feed-Forward layer (FFN) and replace it with a sparse version creating multiple copies. Behind these copies there is a router that selects which of these experts to use for each token in each forward pass at inference time.
This approach allows the model to increase the number of parameters contained in the model while learning, consequently decreasing the loss. At the same time, obviously, this will require more memory and parameters to store. 
At inference time, only a subset of these parameters will be used for each token, keeping the inference cost low. In terms of FLOPS, the MoE model allows to have more parameters per FLOPS compared to a dense model.

The other benefit we can have with MoE is the parallelization that we can obtain, each expert can be store in a different device. The router will then be responsible to get tht token and activate the correct expert on the correct device.