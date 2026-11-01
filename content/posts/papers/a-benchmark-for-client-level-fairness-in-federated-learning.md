---
author: lucacorbucci
title: "A Benchmark for Client-Level Fairness in Federated Learning"
date: 2025-06-30
description: "A benchmark for evaluating fairness in federated learning globally and at the level of individual clients."
tags: [Federated Learning, Fairness, Benchmarking]
keywords: [client-level fairness, federated learning benchmark, fairness metrics]
draft: false
---

## TL;DR

**A Benchmark for Client-Level Fairness in Federated Learning** proposes a benchmark for measuring whether fairness improvements in a federated model benefit individual clients.

## Problem

Federated learning combines data from many clients without moving their raw records to a central server. This creates a tension in evaluation: global metrics are easy to report, but they can hide poor outcomes for particular clients.

## What did we do?

We propose a client-level benchmarking framework that compares global fairness with fairness measured separately for each client. The benchmark considers heterogeneous client datasets and differences in sensitive-attribute distributions, making it possible to test whether an algorithm is robust to realistic client variation.

The evaluation can be used to compare federated-learning methods, fairness metrics, and mitigation strategies under the same experimental setup.

## Main findings

A single federation-wide score is not enough to understand fairness. Reporting client-level results reveals when a method improves the average while leaving some clients behind.

## Resources

- [Read the paper](https://proceedings.mlr.press/v294/heilmann25a.html)

## Cite this paper

```bibtex
@InProceedings{pmlr-v294-heilmann25a,
  title = 	 {A Benchmark for Client-level Fairness in Federated Learning},
  author =       {Heilmann, Xenia and Corbucci, Luca and Cerrato, Mattia},
  booktitle = 	 {Proceedings of Fourth European Workshop on Algorithmic Fairness},
  pages = 	 {434--438},
  year = 	 {2025},
  editor = 	 {Weerts, Hilde and Pechenizkiy, Mykola and Allhutter, Doris and Corrêa, Ana Maria and Grote, Thomas and Liem, Cynthia},
  volume = 	 {294},
  series = 	 {Proceedings of Machine Learning Research},
  month = 	 {30 Jun--02 Jul},
  publisher =    {PMLR},
  pdf = 	 {https://raw.githubusercontent.com/mlresearch/v294/main/assets/heilmann25a/heilmann25a.pdf},
  url = 	 {https://proceedings.mlr.press/v294/heilmann25a.html},
}
```
