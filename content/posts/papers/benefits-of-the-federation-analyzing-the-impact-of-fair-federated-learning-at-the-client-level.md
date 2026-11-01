---
author: lucacorbucci
title: "Benefits of the Federation? Analyzing the Impact of Fair Federated Learning at the Client Level"
date: 2025-06-23
description: "An analysis of whether fair federated-learning methods improve outcomes for individual clients with heterogeneous data and fairness needs."
tags: [Federated Learning, Fairness, Privacy]
keywords: [fair federated learning, client-level fairness, federation benefits]
draft: false
---

## TL;DR

**Benefits of the Federation? Analyzing the Impact of Fair Federated Learning at the Client Level** asks whether joining a fair federated system benefits every client, rather than only improving a global metric.

## Problem

Federated learning brings together clients with different data distributions and potentially different fairness requirements. A fairness intervention that helps the federation overall may still reduce utility or fairness for a particular client.

## What did we do?

We studied the client-level effects of fair federated learning and compared methods including FedMinMax, PUFFLE, and reweighting strategies. The experiments evaluate both global outcomes and the performance and fairness experienced by individual clients.

## Main findings

Global fairness improvements do not automatically translate into benefits for every client. The results show that client heterogeneity can create trade-offs: a method can improve an aggregate objective while leaving some clients with worse local outcomes.

## Resources

- [Read the paper](https://dl.acm.org/doi/full/10.1145/3715275.3732152)

## Cite this paper

```bibtex
@inproceedings{10.1145/3715275.3732152,
author = {Corbucci, Luca and Heilmann, Xenia and Cerrato, Mattia},
title = {Benefits of the Federation? Analyzing the Impact of Fair Federated Learning at the Client Level},
year = {2025},
isbn = {9798400714825},
publisher = {Association for Computing Machinery},
address = {New York, NY, USA},
url = {https://doi.org/10.1145/3715275.3732152},
doi = {10.1145/3715275.3732152},
booktitle = {Proceedings of the 2025 ACM Conference on Fairness, Accountability, and Transparency},
pages = {2232–2248},
numpages = {17},
keywords = {Federated Learning, Fairness in Machine Learning, Bias, Algorithmic Fairness},
location = {Athens, Greece},
series = {FAccT '25}
}
```
