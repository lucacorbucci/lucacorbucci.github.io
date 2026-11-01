---
author: lucacorbucci
title: "Rashomon Sets and Model Multiplicity in Federated Learning"
date: 2026-06-25
description: "How Rashomon sets and predictive multiplicity can be defined, estimated, and analyzed when machine-learning models are trained with federated learning."
tags: [Federated Learning, Fairness, Model Multiplicity]
keywords: [Rashomon set, model multiplicity, federated learning, predictive multiplicity]
draft: false
---

## TL;DR

**Rashomon Sets and Model Multiplicity in Federated Learning** studies what happens when several Federated models perform almost equally well in terms of privacy but differently in terms of other metrics such as fairness.

## Problem

Federated Learning usually produces one global model by averaging updates from many clients. That model can hide important differences between clients: a model that performs well on average may still fail on a particular client or group of clients. In centralized Machine Learning, the collection of similarly accurate but behaviorally different models is known as a **Rashomon set**. In this paper we studied how to define and study those sets without collecting clients' raw data in the Federated Learning setting.

## What did we do?

We formalized three federated perspectives:

- **Global Rashomon set:** models that satisfy a performance constraint across aggregated client data.
- **t-agreement Rashomon set:** models that satisfy the constraint for a chosen fraction of clients.
- **Individual Rashomon set:** models that each client considers sufficiently accurate for its own data.

We also designed a privacy-compatible pipeline for generating candidate models. The pipeline requires at most two additional communication rounds beyond standard training.

## Main findings

Experiments on Dutch Census, ACS Income, and MNIST show that global evaluation can hide large differences in local model behavior. Increasing the client-agreement threshold makes the set smaller and filters out models that only perform well on average. Individual clients can also observe multiplicity patterns that are very different from global averages.

## Resources

- [Published Paper 📓](https://dl.acm.org/doi/10.1145/3805689.3812290)
- [Code 🧑🏻‍💻](https://github.com/xheilmann/FederatedLearningMultiplicity)

## Cite this paper

```bibtex
@inbook{10.1145/3805689.3812290,
author = {Heilmann, Xenia and Corbucci, Luca and Cerrato, Mattia},
title = {Rashomon Sets and Model Multiplicity in Federated Learning},
year = {2026},
isbn = {9798400725968},
publisher = {Association for Computing Machinery},
address = {New York, NY, USA},
url = {https://doi.org/10.1145/3805689.3812290},
booktitle = {Proceedings of the 2026 ACM Conference on Fairness, Accountability, and Transparency},
pages = {2434–2461},
numpages = {28}
}

```
