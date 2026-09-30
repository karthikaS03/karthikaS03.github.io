---
layout: project
title: Domain Fronting
description: Discovering and measuring CDNs prone to domain fronting
img: assets/img/projects/domainfronting_attack.png
excerpt: Domain fronting lets malware hide its real destination behind a reputable domain on a CDN. We found which CDNs allow it, using passive DNS and targeted crawling instead of paid CDN accounts or global test infrastructure.
approach: DNS analysis and targeted crawling
venue: "WWW 2024 (oral)"
domains: [Web, Network]
importance: 7
category: expensive by convention
citation: "Karthika Subramani, Roberto Perdisci, Pierros-Christos Skafidas, Manos Antonakakis. Discovering and Measuring CDNs Prone to Domain Fronting. The ACM Web Conference (WWW), 2024."
---

In a domain fronting attack, a client connects to a CDN using a reputable domain in the TLS handshake (SNI) but asks for a different, attacker-controlled domain in the encrypted HTTP `Host` header. To a network observer, the traffic looks like it is going to the legitimate site, while the CDN quietly forwards it to the attacker's server. Malware uses this to hide its command-and-control traffic.

<div class="pa-figure">
{% include figure.html path="assets/img/projects/domainfronting_attack.png" alt="Domain fronting: TLS SNI shows legitsite.com while the HTTP Host header targets evilsite.com" caption="Domain fronting: the TLS SNI names a legitimate site, while the encrypted HTTP Host header points to the attacker's server." zoomable=true %}
</div>

### Measuring without the usual cost

Finding which CDNs allow fronting is usually assumed to require paid accounts on each CDN or globally distributed test infrastructure. We designed a measurement system that avoids both:

- **Domain discovery.** Passive and active DNS analysis identifies domains served by each CDN.
- **URL discovery.** A Puppeteer-based crawler visits those domains and records the resource URLs they load.
- **Fronting tester.** Candidate (front, target) domain pairs are generated and tested automatically to see whether the CDN routes by the `Host` header.

<div class="pa-figure">
{% include figure.html path="assets/img/projects/domainfronting_overview.png" alt="Domain fronting measurement system: domain discovery, URL discovery, fronting tester" caption="Our measurement pipeline for discovering CDNs that support domain fronting." zoomable=true %}
</div>

<div class="pa-keyfindings" markdown="1">
#### Key contributions
- A low-cost methodology based on **passive DNS and targeted crawling**, with no paid CDN subscriptions.
- A measurement of which CDNs can be used to conceal a communication's true destination.
- Selected for **oral presentation** at The Web Conference 2024 (20% acceptance rate).
</div>
