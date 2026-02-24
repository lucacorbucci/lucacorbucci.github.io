---
author: lucacorbucci
title: Rashomon Sets and Model Multiplicity in Federated Learning
date: 2026-03-03
description:
math: true
draft: true
---

Authors: [Xenia Heilmann](https://scholar.google.com/citations?user=NVkHQnAAAAAJ&hl=it&oi=ao), [Luca Corbucci](https://scholar.google.com/citations?user=TXjmMzAAAAAJ&hl=it), [Mattia Cerrato](https://scholar.google.com/citations?user=F3KJBuAAAAAJ&hl=it&oi=ao)

Paper 📓: [Rashomon Sets and Model Multiplicity in Federated Learning](https://arxiv.org/pdf/2602.09520)

Code 🧑🏻‍💻: [Federated Learning Multiplicity](https://github.com/xheilmann/FederatedLearningMultiplicity)

# TL;DR: In this paper, we provide the first formalization of Rashomon sets for Federated Learning (FL). We define three main perspectives: 1) Global Rashomon Set, 2) t-agreement Rashomon Set and 3) Individual Rashomon Set. Moreover, we show how the standard multiplicity metrics can be computed under FL privacy constraints.

# Introduction

When training Machine Learning models, we make a lot of arbitrary decisions, from hyperparameter tuning to random seed selection. These different choices can lead to multiple distinct models that achieve near-identical overall accuracy while relying on different internal logic for predictions. This phenomenon is known as Rashomon Effect, the set of these models is called the Rashomon Set and the research field that studies this phenomenon is called model multiplicity. Model multiplicity has gained attention in centralized ML, its implication for Federated Learning has not been explored yet.
In this paper we fill this gap by providing the first formalization of Rashomon sets for Federated Learning. 

Federated Learning (FL) allows multiple clients to collaboratively train a model without sharing raw data. Clients trains a model on their local data and then share it with an aggregator server. The standard approach is to average these local updates into one a single model for a certain number of rounds. In the end, a single global model is deployed to all clients, this one can lead to the following issues:
- Predictive behavior homogeneization across diverse datasets.
- Bias amplification for minority groups.
- Silent failures on individual clients whose local data distributions differs from the global majority.

## Methodology:

To address this, we provide a first formalization of Rashomon sets for FL. We introduce three distinct perspectives to measure model multiplicity:

- Global Rashomon Set: Evaluates models based on aggregated statistics across all clients, aligning with standard FL evaluation practices.
- t-agreement Rashomon Set: Requires models to meet performance thresholds across a specific fraction (t) of individual clients, filtering out models that only look good on average but fail locally.
- Individual Rashomon Set: Empowers each client to maintain their own set of high-performing models based on their specific, local data distribution.

To put these definitions into practice, we designed an end-to-end pipeline that integrates Rashomon set analysis into FL. It requires at most two extra communication rounds beyond standard training and consists of three stages:

1) Candidate Generation: Instead of training just one model, the server orchestrates the training of multiple FL models (using a re-training strategy with varying configurations, seeds, or client participation rates) to serve as a pool of candidates.

2) Rashomon Set Construction: Candidate models are evaluated on client data. For the Global and t-agreement sets, clients evaluate models locally and share the aggregated performance results with the server, which then determines which models make the cut. For the Individual set, clients filter the models entirely locally.

3) Multiplicity Analysis: Finally, we compute predictive multiplicity metrics on the surviving models in the Rashomon set to understand exactly how their behaviors diverge.

## Experiments & Key Findings

To understand how these three definitions operate in practice, we implemented a complete multiplicity-aware FL pipeline and evaluated it on three benchmark datasets: the Dutch Census, ACS Income, and MNIST datasets.

We constructed our candidate models using a standard re-training strategy and evaluated them across varying performance constraints (using accuracy as our baseline metric). Here is what we found when comparing the different Rashomon sets:

1) The Global Rashomon set generally yields higher multiplicity metrics and a larger pool of models. In contrast, the t-agreement definition acts as a strict filter. As the agreement threshold t increases, the Rashomon set shrinks significantly, filtering out models that only perform well on average but fail on local distributions.
2) When we looked at the Individual Rashomon sets, we found that local multiplicity metrics often deviated wildly from the global averages. This proves that global aggregation completely fails to capture the heterogeneity of model behavior on specific clients.
3) Interestingly, when compared to a traditional centralized machine learning baseline, deploying Rashomon sets within an FL setting actually reduced the discrepancy (prediction volatility) between models.


## Conclusion

The standard FL paradigm of deploying a single "best" model is insufficient for diverse, decentralized networks. It creates an illusion of optimal performance while hiding local failures and biases. Our work establishes the theoretical and practical foundations necessary to define Rashomon sets and evaluate predictive multiplicity in FL settings. By adopting a multiplicity-aware approach, we can move toward more transparent, accountable, and highly customizable FL systems.