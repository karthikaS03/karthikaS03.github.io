---
layout: project
title: C-Frame
description: Characterizing and measuring in-the-wild CAPTCHA attacks
img: assets/img/projects/cframe_overview.png
excerpt: CAPTCHA-solving farms sell human labor to bypass bot defenses. Rather than studying them one site at a time, C-Frame observes them from inside a solving farm, giving the first cross-organization view of the ecosystem.
approach: Observation within solving farms
venue: "IEEE S&P 2024"
domains: [Web]
importance: 5
category: obscured by complexity
citation: "Hoang Dai Nguyen, Karthika Subramani, Bhupendra Acharya, Roberto Perdisci, Phani Vadrevu. C-Frame: Characterizing and Measuring In-the-Wild CAPTCHA Attacks. IEEE Symposium on Security and Privacy (S&P), 2024."
---

CAPTCHAs are meant to separate humans from bots. CAPTCHA-bypass-for-hire services defeat them by routing each challenge to human workers in a *solving farm*. Because every farm serves many customers, looking at any single targeted website shows only a sliver of the activity. Earlier work had studied the ecosystem only site by site.

### Measuring from the inside

C-Frame extends our interaction-driven measurement approach from [PhishInPatterns]({{ '/projects/4_phishinpatterns/' | relative_url }}) to this ecosystem. It observes the CAPTCHA tasks that solving farms hand to their workers, recording which websites the tasks target before they reach the CAPTCHA service.

<div class="pa-figure">
{% include figure.html path="assets/img/projects/cframe_overview.png" alt="C-Frame design: observing tasks between CAPTCHA farms and their workers" caption="C-Frame observes CAPTCHA tasks as they flow from solving farms to workers, and records the targeted sites." zoomable=true %}
</div>

<div class="pa-keyfindings" markdown="1">
#### Key contributions
- The first **cross-organization view** of CAPTCHA attacks, measured from inside solving farms.
- A characterization of which websites and CAPTCHA services these farms target in the wild.
</div>
