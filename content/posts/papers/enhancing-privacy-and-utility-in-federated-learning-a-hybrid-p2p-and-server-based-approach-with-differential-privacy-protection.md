---
author: lucacorbucci
title: "Enhancing Privacy and Utility in Federated Learning: A Hybrid P2P and Server-Based Approach with Differential Privacy Protection"
date: 2024-07-08
description: "A hybrid peer-to-peer and server-based federated-learning architecture that studies privacy, utility, and differential-privacy noise."
tags: [Federated Learning, Privacy, Distributed Systems]
keywords: [federated learning, peer-to-peer, differential privacy, privacy utility trade-off]
draft: false
---

## TL;DR

**Enhancing Privacy and Utility in Federated Learning: A Hybrid P2P and Server-Based Approach with Differential Privacy Protection** explores a federated architecture that combines peer-to-peer communication with server-based aggregation.

## Problem

The central server in a traditional federated-learning system simplifies coordination but can become a privacy and scalability bottleneck. Differential privacy can protect updates, but the additional noise may reduce model utility.

## What did we do?

We designed a hybrid architecture in which clients can exchange information through peer-to-peer connections while retaining server-based coordination where it is useful. We also studied how differential-privacy protection affects model performance in this setting.

The experiments compare privacy and utility under different configurations and analyze how the architecture changes the cost of privacy protection.

## Main findings

Federated learning does not have to rely on a single communication pattern. Combining peer-to-peer and server-based mechanisms can offer another point in the design space for balancing privacy, communication, and model utility.

## Resources

- [Read the paper](https://www.scitepress.org/PublishedPapers/2024/128636/)

## Cite this paper

```bibtex
@conference{corbucci2024hybrid,
author={Luca Corbucci and Anna Monreale and Roberto Pellungrini},
title={Enhancing Privacy and Utility in Federated Learning: A Hybrid P2P and Server-Based Approach with Differential Privacy Protection},
booktitle={Proceedings of the 21st International Conference on Security and Cryptography - Volume 1: SECRYPT},
year={2024},
pages={592-602},
publisher={SciTePress},
organization={INSTICC},
doi={10.5220/0012863600003767},
isbn={978-989-758-709-2}}
}
```
