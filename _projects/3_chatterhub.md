---
layout: project
title: ChatterHub
description: Privacy invasion via smart-home hubs
img: assets/img/projects/chatterhub_overview.png
excerpt: Smart-home hubs encrypt their traffic, but the timing and shape of that traffic still leak what is happening inside a home. ChatterHub infers device identities and user actions without decrypting anything.
approach: Encrypted traffic analysis
venue: "IEEE SMARTCOMP 2021; Pervasive and Mobile Computing 2022"
domains: [Network]
importance: 3
category: hidden by design
paper: https://doi.org/10.1016/j.pmcj.2022.101675
code: https://github.com/karthikaS03/ChatterHub
citation: "Omid Setayeshfar, Karthika Subramani, Xingzi Yuan, Raunak Dey, Dezhi Hong, Kyu Hyung Lee, In Kee Kim. ChatterHub: Privacy Invasion via Smart Home Hub. IEEE SMARTCOMP, 2021; extended as Privacy Invasion via Smart-Home Hub in Personal Area Networks, Pervasive and Mobile Computing 85, 2022."
---

Smart-home hubs sit between low-power devices (door locks, motion sensors, smart bulbs) and the cloud. Their traffic is encrypted, which is often assumed to keep a household's activity private. ChatterHub shows that this blind spot persists even behind encryption: an adversary who can only *observe* the hub's encrypted traffic can still learn which devices are in the home and what they are doing.

<div class="pa-figure">
{% include figure.html path="assets/img/projects/chatterhub_overview.png" alt="ChatterHub overview: offline training and model generation, and attack phase on encrypted traffic" caption="ChatterHub: an offline training phase builds models from labeled traffic, and the attack phase applies them to a target home's encrypted traffic." zoomable=true %}
</div>

### How it works

- **Offline training.** Packet traces from a hub are labeled with ground-truth device events.
- **Segmentation.** A packet filter and *dynamic change-point detection* isolate the bursts of traffic caused by individual device events.
- **Classification.** Models (sequence-to-sequence, LSTM, and random forest) learn to map each burst to a device and an action.
- **Attack.** The trained model is applied to a target home's encrypted traffic, observed by a nearby sniffer, a compromised router, or an Internet service provider.

<div class="pa-keyfindings" markdown="1">
#### Key findings
- Device identity and user actions can be inferred from encrypted hub traffic **without decryption**.
- The attack needs **no prior knowledge** of which devices are installed in the home.
- The results highlight the need for traffic-shaping defenses in smart-home ecosystems.
</div>
