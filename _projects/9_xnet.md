---
layout: project
title: XNET
description: Intelligent dynamic sampling for 100 Gbps network security monitoring
img:
excerpt: Monitoring security-relevant traffic at 100 Gbps usually needs specialized hardware. XNET uses Linux's eXpress Data Path to prioritize the traffic that matters, on commodity machines.
approach: XDP-based dynamic sampling
venue: "Under review"
domains: [Network]
importance: 9
category: expensive by convention
---

High-speed links make full-fidelity security monitoring expensive. Uniform sampling reduces the load, but the rare, security-relevant traffic that analysts care about most tends to disappear along with the rest.

### Approach

XNET uses Linux's **eXpress Data Path (XDP)** to dynamically prioritize security-relevant traffic directly in the kernel's fast path, on commodity hardware. Traffic that matters for detection is kept at higher fidelity, while bulk traffic is sampled down.

<div class="pa-keyfindings" markdown="1">
#### Early results
- In a real-world deployment, XNET reduced traffic volume by up to **84%** while increasing the visibility of otherwise negligible traffic **fivefold**.
- Controlled tests scale to **100 Gbps**.
</div>

*This work is currently under review; more details will be shared after publication.*
