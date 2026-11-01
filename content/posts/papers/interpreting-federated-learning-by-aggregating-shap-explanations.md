---
author: lucacorbucci
title: "Interpreting Federated Learning by Aggregating SHAP Explanations"
date: 2026-01-01
description: "iFLASH is a privacy-preserving framework that aggregates local SHAP explanations from federated-learning clients."
tags: [Federated Learning, Explainable AI, Privacy]
keywords: [iFLASH, SHAP, federated explainability, privacy-preserving explanations]
draft: false
---

## TL;DR

**Interpreting Federated Learning by Aggregating SHAP Explanations** introduces **iFLASH**, a framework for producing global explanations from local SHAP explainers without centralizing client data.

## Problem

Federated learning keeps training data on local clients, but conventional explainability methods often assume centralized access to that data. Simply averaging local explanations can also be misleading when clients have different data distributions or model quality.

## What we did

In iFLASH, clients compute and evaluate SHAP explanations locally. Instead of sharing raw data, models, or gradients, clients send feature-importance information and performance-based quality measures to the server. The server then uses aggregation strategies that weight client contributions according to model performance and explanation quality.

We evaluate the framework in both cross-silo settings with a small number of clients and cross-device settings with many clients, including heterogeneous data distributions.

## Main findings

Quality-aware aggregation improves explanation faithfulness over naive uniform averaging in cross-silo experiments. The resulting explanations align closely with centralized explanations in feature-importance ranking and directionality. In cross-device settings, quality-aware methods remain competitive as the larger number of clients creates a stronger averaging effect.

## Resources

- [Read the paper](https://ieeexplore.ieee.org/abstract/document/11534187/)

## Cite this paper

```bibtex
@article{bonsignori2026iflash,
  title = {Interpreting Federated Learning by Aggregating SHAP Explanations},
  author = {Bonsignori, Valerio and Corbucci, Luca and Naretto, Francesca and Guidotti, Riccardo and Monreale, Anna},
  journal = {IEEE Access},
  year = {2026},
  doi = {10.1109/ACCESS.2026.3696009}
}
```
