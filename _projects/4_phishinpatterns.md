---
layout: project
title: PhishInPatterns
description: Measuring elicited user interactions at scale on phishing websites
img: assets/img/projects/phishinpatterns_overview.png
excerpt: Modern phishing sites spread data collection across multi-page flows and gate their payloads behind interactions that stop automated crawlers. We built a smart crawler that plays along, and studied more than 50,000 phishing sites from the user's point of view.
approach: Multi-step interaction analysis
venue: "IMC 2022"
domains: [Web]
importance: 4
category: obscured by complexity
paper: https://doi.org/10.1145/3517745.3561467
code: https://github.com/karthikaS03/PhishInPattern
citation: "Karthika Subramani, William Melicher, Oleksii Starov, Phani Vadrevu, Roberto Perdisci. PhishInPatterns: Measuring Elicited User Interactions at Scale on Phishing Websites. ACM Internet Measurement Conference (IMC), 2022."
---

Phishing is extensively studied, yet it keeps reaching all-time highs. Attacks increasingly rely on modern web design patterns to look legitimate and, at the same time, to evade phishing detectors and security crawlers. A crawler that loads only the first page misses most of what a victim actually experiences.

### A crawler that plays along

We built an intelligent crawler that combines browser automation, machine learning, and visual analysis to simulate the interactions phishing sites expect from their victims:

- A **field parser** and **field classifier** find input fields and work out what each one asks for (email, name, card number, and so on).
- A **page interactor** fills the fields with appropriate fake data and moves through multi-page flows.
- A **trait analyzer** then studies what each site did: CAPTCHAs, multi-factor authentication prompts, multi-stage data collection, and the campaigns the sites belong to.

<div class="pa-figure">
{% include figure.html path="assets/img/projects/phishinpatterns_overview.png" alt="PhishInPatterns overview with Smart Crawler and Trait Analyzer modules" caption="The Smart Crawler module interacts with suspected phishing pages; the Trait Analyzer module characterizes what they elicit." zoomable=true %}
</div>

<div class="pa-keyfindings" markdown="1">
#### Key findings
- Across **51,859** phishing sites we identified **8,472** campaigns.
- **45%** of sites collected data across multiple pages, mimicking the experience of legitimate sites.
- **5.6%** of sites used click-through gating to hide data-collection pages behind preliminary interactions.
- Phishing sites often impersonate a brand *without* closely copying its design, embed modern user-verification systems such as CAPTCHAs, and sometimes end by reassuring victims that their data is safe.
</div>

### Why it matters

These behaviors directly undermine detectors that assume phishing pages are single-page clones of a brand's login form. Understanding phishing from the user's perspective points toward more robust detection. It also shaped our later work on [CAPTCHA-bypass services]({{ '/projects/5_c-frame/' | relative_url }}) and [in-browser defenses]({{ '/projects/6_pp3d/' | relative_url }}).
