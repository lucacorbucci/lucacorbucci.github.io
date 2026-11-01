---
author: lucacorbucci
title: "Differentially Private FastSHAP for Federated Learning Model Explainability"
date: 2025-06-30
description: "A federated FastSHAP approach that applies differential privacy to model explainability without sharing client data."
tags: [Federated Learning, Explainable AI, Privacy]
keywords: [FastSHAP, differential privacy, federated explainability, model explanations]
draft: false
---

## TL;DR

**Differentially Private FastSHAP for Federated Learning Model Explainability** combines federated learning, model explanations, and differential privacy.

## Problem

Explainability methods often require access to training data or synthetic samples. In federated learning, sharing those data can violate the privacy assumptions that motivated federation in the first place. Explanations therefore need their own privacy-aware training process.

## What did we do?

We adapt FastSHAP to a federated setting and add sample-level differential privacy during the training of the explainer. Clients contribute to the explanation model without sharing their raw data. The resulting system can produce feature-attribution explanations for a collaboratively trained model while limiting information leakage from the explanation process.

## Main findings

Model explanations should be treated as a potential privacy channel. Adding differential privacy to the federated explainer makes it possible to study the utility–privacy trade-off rather than assuming that explanations are automatically safe.

## Resources

- [Read the PDF](https://ieeexplore.ieee.org/abstract/document/11227553)

## Cite this paper

```bibtex
@INPROCEEDINGS{11227553,
  author={Bonsignori, Valerio and Corbucci, Luca and Naretto, Francesca and Monreale, Anna},
  booktitle={2025 International Joint Conference on Neural Networks (IJCNN)}, 
  title={Differentially Private FastSHAP for Federated Learning Model Explainability}, 
  year={2025},
  volume={},
  number={},
  pages={1-8},
  keywords={Training;Privacy;Differential privacy;Adaptation models;Federated learning;Closed box;Training data;Regulation;Protection;Testing;Federated Learning;Explainable AI;Privacy-Preserving Machine Learning},
  doi={10.1109/IJCNN64981.2025.11227553}}
```
