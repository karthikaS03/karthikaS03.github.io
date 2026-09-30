---
layout: project
title: IXmon
description: Detecting and measuring in-the-wild DRDoS attacks at Internet exchange points
img: assets/img/projects/ixmon_overview.png
excerpt: IXmon detects distributed reflective denial-of-service attacks using the flow statistics networks already collect. Over 21 months at a real Internet exchange, it detected more than 900 attacks against 31 victim networks.
approach: Flow-based attack detection
venue: "DIMVA 2021"
domains: [Network]
importance: 8
category: expensive by convention
paper: https://doi.org/10.1007/978-3-030-80825-9_3
citation: "Karthika Subramani, Roberto Perdisci, Maria Konte. Detecting and Measuring In-The-Wild DRDoS Attacks at IXPs. Detection of Intrusions and Malware, and Vulnerability Assessment (DIMVA), 2021."
---

Distributed reflective denial-of-service (DRDoS) attacks bounce traffic off misconfigured servers (memcached, CLDAP, and others) to overwhelm a victim. They have produced some of the largest DDoS attacks ever recorded, such as 1.3 Tbps against GitHub and 2.3 Tbps against Amazon AWS. They are well known, yet still largely unmitigated.

Internet exchange points (IXPs) see traffic from many networks at once, which makes them a natural vantage point. But deep packet inspection at IXP scale is expensive.

### Detecting attacks from flow statistics

**IXmon** is an open-source DRDoS detection system designed for IXP-like network hubs. Instead of new infrastructure, it uses the NetFlow data the network already collects:

- It aggregates flow records into per-destination traffic statistics for protocols commonly abused for reflection.
- It runs online time-series anomaly detection on those statistics.
- A DRDoS detection stage confirms attacks and raises alerts about the victim network.

<div class="pa-figure">
{% include figure.html path="assets/img/projects/ixmon_overview.png" alt="IXmon system overview: NetFlows from the IXP feed traffic statistics, anomaly detection, and DRDoS detection" caption="IXmon: from IXP NetFlow records to DRDoS alerts." zoomable=true %}
</div>

<div class="pa-keyfindings" markdown="1">
#### Key findings
- Deployed at **Southern Crossroads (SoX)**, which serves more than 20 research and education networks in the South-East US, for about **21 months**.
- Detected **over 900** DRDoS attacks against **31** victim ASes.
- Most attacks are short-lived, lasting only a few minutes, but large-volume, long-lasting, and highly distributed attacks against research and education networks are not uncommon.
- The results enable *surgical*, low-collateral mitigation at the IXP, before attack traffic overwhelms the victim's links, instead of blunt filtering.
</div>
