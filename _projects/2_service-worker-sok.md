---
layout: project
title: Service Worker SoK
description: "Workerounds: categorizing service worker attacks and mitigations"
img: assets/img/projects/sw_overview.png
excerpt: Service workers run in the background of the browser, largely out of the user's view. We systematized the attacks that abuse them, measured how well browsers mitigate them, and built a forensics engine to spot anomalous service worker behavior.
approach: Abuse analysis and browser forensics
venue: "IEEE EuroS&P 2022"
domains: [Web]
importance: 2
category: hidden by design
paper: https://doi.org/10.1109/EuroSP53844.2022.00041
code: https://github.com/karthikaS03/SW_Sec_Project
citation: "Karthika Subramani, Jordan Jueckstock, Alexandros Kapravelos, Roberto Perdisci. SoK: Workerounds - Categorizing Service Worker Attacks and Mitigations. IEEE European Symposium on Security and Privacy (EuroS&P), 2022."
---

Service workers are the engine behind Progressive Web Apps (PWAs). They power offline support, background sync, and push notifications. Because they run in the background, independently of any open page, they are also a natural place for abuse to hide. After [PushAdMiner]({{ '/projects/1_pushadminer/' | relative_url }}) showed one such abuse, we asked a broader question: *what else can go wrong with service workers, and how well do browsers defend against it?*

### Systematizing the attack surface

This systematization of knowledge (SoK) categorizes previously published and newly discovered service worker attacks, and maps each one to the mitigations browsers have (or have not) deployed. We tested the attacks across browsers to see which mitigations actually hold in practice.

### Making background behavior observable

To study how service workers behave in the wild, we built **SWAT**, a Chromium-based forensics engine that logs service worker lifecycle events:

- Instrumented Chromium, driven by Puppeteer, records the activity of top legitimate PWAs to learn baseline behavior and derive policies.
- An anomaly detection stage checks service workers against those policies.
- When a policy is violated, the mitigation stage can stop or unregister the offending service worker.

<div class="pa-figure">
{% include figure.html path="assets/img/projects/sw_overview.png" alt="SWAT system overview: forensics, policy analysis, anomaly detection and threat mitigation stages" caption="SWAT: learning policies from legitimate PWAs to detect and mitigate anomalous service workers." zoomable=true %}
</div>

<div class="pa-keyfindings" markdown="1">
#### Key findings
- Anomalous service worker behavior correlates strongly with social engineering and unauthorized tracking.
- Our disclosure led Firefox to patch the extension-API flaw behind the **ExtensionHijack** attack.
- Most attacks remained unmitigated. Defending against them requires broader controls on service worker execution and permissions, not isolated fixes.
</div>
