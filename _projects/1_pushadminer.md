---
layout: project
title: PushAdMiner
description: Measuring the rise of (malicious) web push advertising
img: assets/img/projects/pushadminer_attack.png
excerpt: Ad networks turned Web Push Notifications into an ad channel that keeps reaching users after they leave a site. We built a crawler to follow that journey end to end, and found that half of these ads were malicious.
approach: Subscription-to-click crawling
venue: "IMC 2020"
domains: [Web]
importance: 1
category: hidden by design
paper: https://doi.org/10.1145/3419394.3423631
code: https://github.com/karthikaS03/PushAdMiner
citation: "Karthika Subramani, Xingzi Yuan, Omid Setayeshfar, Phani Vadrevu, Kyu Hyung Lee, Roberto Perdisci. When Push Comes to Ads: Measuring the Rise of (Malicious) Push Advertising. ACM Internet Measurement Conference (IMC), 2020."
---

Web Push Notifications (WPNs) were designed to let sites send users timely updates even after the tab is closed. That same property made them attractive to ad networks looking for a channel that ad blockers did not yet cover. Once a user clicks "Allow" on a permission prompt, the site can keep pushing messages to their desktop or phone, and a single click on one of those messages can lead straight to a scam.

<div class="pa-figure">
{% include figure.html path="assets/img/projects/pushadminer_attack.png" alt="Six-step example of a malicious push ad leading to a tech-support scam" caption="A malicious push ad in the wild: after a user allows notifications, a later push message leads to a tech-support scam page." zoomable=true %}
</div>

### How we measured it

The abuse only becomes visible across the full *subscribe, receive, click, land* journey, which a conventional crawler never completes. We built **PushAdMiner** to automate that journey at scale:

- Instrumented Chromium-based crawlers register for push notifications on thousands of websites, then log every notification and the pages it leads to, with screenshots.
- Each notification is described by its metadata (title, body, target URL, landing domain, images, WHOIS and more).
- Multi-stage clustering groups the notifications into ad campaigns, and meta-clustering links related campaigns together.
- URL blocklists and manual analysis then flag malicious and suspicious campaigns.

<div class="pa-figure">
{% include figure.html path="assets/img/projects/pushadminer_overview.png" alt="PushAdMiner system overview with data collection and data analysis modules" caption="PushAdMiner's data collection and data analysis modules." zoomable=true %}
</div>

<div class="pa-keyfindings" markdown="1">
#### Key findings
- We collected and analyzed **21,541** WPN messages from thousands of websites.
- PushAdMiner identified **572** WPN ad campaigns, totaling **5,143** ads pushed by a variety of ad networks.
- **51%** of all WPN ads we collected were malicious.
- Traditional ad blockers and URL filters were mostly unable to block them, leaving a significant abuse vector unchecked.
</div>

### Why it matters

This was the first in-depth look at push notifications as an ad-delivery channel. It showed that a feature built for engagement had quietly become a malvertising channel outside the view of existing defenses. It also motivated our follow-up work on the broader service worker attack surface ([Service Worker SoK]({{ '/projects/2_service-worker-sok/' | relative_url }})).
