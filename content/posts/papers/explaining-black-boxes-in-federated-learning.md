---
author: lucacorbucci
title: "Explaining Black-Boxes in Federated Learning"
date: 2023-07-26
description: "A federated explainability method that aggregates local feature attributions to explain predictions from a collaboratively trained model."
tags: [Federated Learning, Explainable AI]
keywords: [federated explainability, SHAP, black-box models, feature attribution]
draft: false
---

## TL;DR

**Explaining Black-Boxes in Federated Learning** adapts feature-attribution explanations to models trained collaboratively across multiple clients.

## Problem

Federated learning protects data locality, but this makes it difficult to apply centralized explainability methods. A server cannot simply collect all client data to explain the global model, and explanations produced independently by different clients may not be directly comparable.

## What did we do?

We designed a method that computes local explanations at the clients and combines the resulting feature attributions to explain predictions from the federated model. The approach builds on SHAP-style explanations while keeping the data on the clients.

## Main findings

A federated model can be explained without centralizing the records used to train it. Aggregating local attribution information provides a global view while preserving the distributed nature of the learning process.

## Resources

- [Read the paper](https://link.springer.com/chapter/10.1007/978-3-031-44067-0_8)

## Cite this paper

```bibtex
@InProceedings{10.1007/978-3-031-44067-0_8,
author="Corbucci, Luca
and Guidotti, Riccardo
and Monreale, Anna",
editor="Longo, Luca",
title="Explaining Black-Boxes in Federated Learning",
booktitle="Explainable Artificial Intelligence",
year="2023",
publisher="Springer Nature Switzerland",
address="Cham",
pages="151--163",
isbn="978-3-031-44067-0"
}
```
