---
author: lucacorbucci
title: "Semantic Enrichment of Explanations of AI Models for Healthcare"
date: 2023-10-09
description: "A healthcare explainability approach that connects model explanations with clinical concepts and information from patient notes."
tags: [Explainable AI, Healthcare, Natural Language Processing]
keywords: [healthcare AI, explainable AI, clinical notes, SNOMED CT, semantic enrichment]
draft: false
---

## TL;DR

**Semantic Enrichment of Explanations of AI Models for Healthcare** connects Machine Learning explanations with the clinical language used by clinicians.

## Problem

Feature-importance explanations can identify which variables influenced a prediction, but they do not always provide enough context for a clinician. In healthcare, the relevant evidence may be expressed in clinical notes using concepts and terminology that are not directly represented by the model features.

## What did we do?

We enriched explanations using medical ontologies, including SNOMED CT, and natural-language processing of clinical notes. The method links features that contribute to a prediction with semantically related information in the patient's notes.

## Main findings

Adding clinical semantics can make model explanations more informative than a list of feature names or scores. It helps connect a model's internal evidence with concepts that healthcare experts already use.

## Resources

- [Read the paper](https://link.springer.com/content/pdf/10.1007/978-3-031-45275-8_15.pdf)

## Cite this paper

```bibtex
@inproceedings{corbucci2023semantic,
  title = {Semantic Enrichment of Explanations of AI Models for Healthcare},
  author = {Corbucci, Luca and Monreale, Anna and Panigutti, Cecilia and Natilli, Michela and Smiraglio, Simona and Pedreschi, Dino},
  booktitle = {Discovery Science},
  year = {2023},
  doi = {10.1007/978-3-031-45275-8_15}
}
```
