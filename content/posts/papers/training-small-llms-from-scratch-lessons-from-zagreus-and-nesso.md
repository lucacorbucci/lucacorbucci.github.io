---
author: lucacorbucci
title: "Training Small LLMs from Scratch: Lessons from Zagreus and Nesso"
date: 2026-09-14
description: "Zagreus and Nesso are openly released small language models for Romance languages, trained from scratch and fine-tuned for instruction following."
tags: [Language Models, Small Language Models, Multilingual NLP]
keywords: [small language models, Zagreus, Nesso, Romance languages, pre-training, mii-llm]
draft: false
---

## TL;DR

**Training Small LLMs from Scratch: Lessons from Zagreus and Nesso** introduces two families of openly released sub-billion-parameter language models for Italian, Spanish, Portuguese and French, together with the full recipe used to build them. This is a collaboration with the MiiLLM project.

## Problem

Small Language Models are attractive for consumer hardware, edge devices and privacy-sensitive applications, but most open efforts focus on English and a few high-resource languages. Romance languages have few openly available models trained from scratch, and few transparent, reproducible baselines.

## What did we do?

We trained Zagreus, four bilingual foundation models pairing English with Italian, Spanish, Portuguese and French. Each has about 400 million parameters and was trained from scratch on roughly one trillion tokens. Nesso extends these models with supervised fine-tuning for instruction following and agentic function calling, including a fully open variant trained only on public data. The paper describes the whole pipeline: data curation, tokenizer design, architecture, distributed pre-training, post-training and evaluation.

## Main findings

Carefully curated data and transparent training practices let sub-billion-parameter models stay competitive with larger baselines of comparable class. Nesso-0.4B-instruct matches or exceeds Qwen3-0.6B on several Italian and English benchmarks, and Zagreus-0.4B-por outperforms Qwen3-0.6B-Base on the Portuguese leaderboard. Structured prediction and discriminative classification remain targets for future data augmentation and alignment work.

## Resources

- [Read the paper](/papers/training-small-llms-from-scratch-lessons-from-zagreus-and-nesso.pdf)
- [Models on Hugging Face](https://huggingface.co/collections/mii-llm/zagreus-nesso-fine-tuned)

## Cite this paper

```bibtex
@inproceedings{ercolani2026zagreus,
  title = {Training Small LLMs from Scratch: Lessons from Zagreus and Nesso},
  author = {Ercolani, Alessandro and Federici, Edoardo and Bentivogli, Luisa and Corbucci, Luca},
  booktitle = {Proceedings of the Twelfth Italian Conference on Computational Linguistics (CLiC-it 2026)},
  year = {2026}
}
```
