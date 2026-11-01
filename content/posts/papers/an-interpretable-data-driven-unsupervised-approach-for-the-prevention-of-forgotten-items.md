---
author: lucacorbucci
title: "An Interpretable Data-Driven Unsupervised Approach for the Prevention of Forgotten Items"
date: 2025-10-21
description: "An interpretable unsupervised approach for predicting products that shoppers are likely to forget during a shopping trip."
tags: [Explainable AI, Recommender Systems, Machine Learning]
keywords: [forgotten item prediction, unsupervised learning, interpretable AI, next basket prediction]
draft: false
---

## TL;DR

**An Interpretable Data-Driven Unsupervised Approach for the Prevention of Forgotten Items** introduces methods for reminding shoppers about products they may have intended to buy but omitted.

## Problem

Shopping-recommendation systems often focus on suggesting new products. A different and practical problem is predicting a **forgotten item**: a product a person is likely to need or buy regularly but did not include in the current basket.

## What did we do?

We formalized forgotten-item prediction as an unsupervised learning problem. The proposed methods, **XMT** and **TXMT**, combine signals such as purchase recurrence, time between purchases, seasonality, co-purchases, and sequential shopping patterns.

The approach is designed to remain interpretable. Instead of returning only a score, it can expose the behavioral signals that support a reminder, such as a product's usual purchase interval or its relationship with the current basket.

## Main findings

The experiments compare the proposed methods with next-basket and forgotten-item baselines on real retail data. The data-driven models improve prediction quality while retaining human-readable reasons for their recommendations.

## Resources

- [Read the paper](https://dx.doi.org/10.3233/faia250912)

## Cite this paper

```bibtex
@inproceedings{corbucci2025forgotten,
  title = {An Interpretable Data-Driven Unsupervised Approach for the Prevention of Forgotten Items},
  author = {Corbucci, Luca and Borges Legrottaglie, Javier Alejandro and Spinnato, Francesco and Monreale, Anna and Guidotti, Riccardo},
  booktitle = {Proceedings of the 28th European Conference on Artificial Intelligence},
  year = {2025},
  doi = {10.3233/FAIA250912}
}
```
