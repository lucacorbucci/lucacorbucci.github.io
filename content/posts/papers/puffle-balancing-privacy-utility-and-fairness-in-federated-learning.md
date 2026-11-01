---
author: lucacorbucci
title: "PUFFLE: Balancing Privacy, Utility, and Fairness in Federated Learning"
date: 2024-10-19
description: "PUFFLE studies how privacy, utility, and fairness can be balanced in federated learning with differential privacy."
tags: [Federated Learning, Privacy, Fairness]
keywords: [PUFFLE, federated learning, differential privacy, fairness, privacy utility trade-off]
draft: false
---

## TL;DR

**PUFFLE: Balancing Privacy, Utility, and Fairness in Federated Learning** introduces a method for studying the trade-offs between privacy protection, model utility, and fairness while training Federated Learning models.

## Problem

Federated learning keeps data local, but model updates can still reveal information. Differential privacy can reduce that risk, yet adding noise may lower accuracy or affect groups differently. Optimizing privacy and utility alone can therefore create new fairness problems.

## What did we do?

PUFFLE incorporates privacy, utility, and fairness into the federated-learning objective. The method uses tunable parameters to control the relative importance of these goals and evaluates how the trade-offs change across different client distributions.

## Main findings

There is no single setting that is optimal for every federation. The right balance depends on the privacy budget, the data distribution, and the fairness objective. Making those choices explicit helps practitioners understand the consequences of a deployment.

## Resources

- [Read the paper](https://doi.org/10.3233/FAIA240671)
- [Preprint on arXiv](https://arxiv.org/abs/2407.15224)

## Cite this paper

```bibtex
@inproceedings{corbucci2024puffle,
  title = {PUFFLE: Balancing Privacy, Utility, and Fairness in Federated Learning},
  author = {Corbucci, Luca and Heikkilä, Mikko A. and Solans Noguero, David and Monreale, Anna and Kourtellis, Nicolas},
  booktitle = {ECAI 2024},
  year = {2024},
  volume = {392},
  doi = {10.3233/FAIA240671}
}
```
