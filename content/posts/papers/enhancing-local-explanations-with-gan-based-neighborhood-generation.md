---
author: lucacorbucci
title: "Enhancing Local Explanations with GAN-Based Neighborhood Generation"
date: 2025-10-05
description: "FIRE360 uses GAN-generated neighborhoods to improve local, model-agnostic explanations with feature importance, rules, and examples."
tags: [Explainable AI, Generative Models, Machine Learning]
keywords: [FIRE360, local explanations, GAN, explainable AI, counterfactual explanations]
draft: false
---

## TL;DR

**Enhancing Local Explanations with GAN-Based Neighborhood Generation** presents **FIRE360**, a local and model-agnostic explanation method for tabular machine-learning models.

## Problem

Local explainers need a neighborhood of examples around the instance being explained. If that neighborhood is generated poorly, the explanation can contain unrealistic samples and become difficult to trust. Standard perturbation strategies may also struggle with mixed or structured tabular data.

## What did we do?

FIRE360 uses a generative adversarial network to create a reusable synthetic neighborhood around the data distribution. It then provides several complementary views of a model decision:

- Feature-importance information;
- Factual and counterfactual rules;
- Representative exemplars;
- Counter-exemplars showing how nearby decisions differ.

The method is model-agnostic and is intended to provide more than a single ranking of features.

## Main findings

FIRE360 combines feature importance, factual and counterfactual rules, and representative examples so that an explanation can show both why a prediction was made and how it could change.

## Resources

- [Read the paper](https://link.springer.com/chapter/10.1007/978-3-032-05461-6_21)

## Cite this paper

```bibtex
@InProceedings{10.1007/978-3-032-05461-6_21,
author="Corbucci, Luca
and Naretto, Francesca
and Monreale, Anna",
editor="D{\v{z}}eroski, Sa{\v{s}}o
and Levati{\'{c}}, Jurica
and Pio, Gianvito
and Simidjievski, Nikola",
title="Enhancing Local Explanations with GAN-Based Neighborhood Generation",
booktitle="Discovery Science",
year="2025",
publisher="Springer Nature Switzerland",
address="Cham",
pages="316--331",
isbn="978-3-032-05461-6"
}
```
