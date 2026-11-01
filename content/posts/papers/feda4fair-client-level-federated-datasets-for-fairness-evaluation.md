---
author: lucacorbucci
title: "FeDa4Fair: Client-Level Federated Datasets for Fairness Evaluation"
date: 2026-06-25
description: "FeDa4Fair is a collection of client-level federated datasets and benchmarks for evaluating fairness under heterogeneous and conflicting client biases."
tags: [Federated Learning, Fairness, Datasets]
keywords: [FeDa4Fair, federated datasets, client-level fairness, fairness evaluation]
draft: false
---


## TL;DR

**FeDa4Fair: Client-Level Federated Datasets for Fairness Evaluation** introduces a benchmark and a library for studying fairness in Federated Learning when clients have different and potentially conflicting biases.

## Problem

When training Federated Learning models, we usually evaluate fairness with metrics aggregated across the whole federation. These global scores can hide the individual clients. A model may appear fair overall while treating some clients much worse than others because of their data distributions, sensitive attributes, or fairness requirements differ.

## What did we do?

We created **FeDa4Fair**, a collection of benchmark datasets designed for client-level fairness evaluation. The datasets model heterogeneous client populations and make it possible to compare fairness-aware Federated-Learning methods under controlled and reproducible conditions. The clients considered in the benchmark datasets may have attribute-level or value-level conflicting preferences.

Moreover, we also introduce a library that allows to easily create datasets with certain unfairness distributions simulating both attribute- and value-level conflicting unfairness.

## Resources

- [Read the paper](https://dl.acm.org/doi/abs/10.1145/3805689.3812291)
- [FeDa4Fair datasets on Hugging Face](https://huggingface.co/datasets/lucacorbucci/FeDa4Fair)
- [Code and documentation](https://github.com/xheilmann/FeDa4Fair)

## Cite this paper

```bibtex
@inbook{10.1145/3805689.3812291,
author = {Heilmann, Xenia and Corbucci, Luca and Cerrato, Mattia and Monreale, Anna},
title = {FeDa4Fair: Client-Level Federated Datasets for Fairness Evaluation},
year = {2026},
isbn = {9798400725968},
publisher = {Association for Computing Machinery},
address = {New York, NY, USA},
url = {https://doi.org/10.1145/3805689.3812291},
booktitle = {Proceedings of the 2026 ACM Conference on Fairness, Accountability, and Transparency},
pages = {2462–2501},
numpages = {40}
}
}
```
