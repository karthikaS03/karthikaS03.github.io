---
layout: project
title: PP3D
description: An in-browser, vision-based defense against web behavior manipulation attacks
img: assets/img/projects/pp3d_overview.png
excerpt: Scareware and similar attacks manipulate users with what they show on screen. PP3D detects these pages directly in the browser from visual and textual cues, with over 99% detection at a 1% false-positive rate and no data leaving the device.
approach: Local visual and text-based defense
venue: "ACSAC 2025"
domains: [Web]
importance: 6
category: obscured by complexity
citation: "Spencer King, Irfan Ozen, Karthika Subramani, Saranyan Senthivel, Phani Vadrevu, Roberto Perdisci. PP3D: An In-Browser Vision-Based Defense Against Web Behavior Manipulation Attacks. Annual Computer Security Applications Conference (ACSAC), 2025."
---

Behavior-manipulation attacks, such as fake virus alerts, scareware, and deceptive software downloads, work by showing users something alarming or enticing. What these pages *look like* is often more telling than their code or URL. PP3D builds on the behavioral indicators from our measurement work to turn that observation into a practical defense.

### From discovery to defense

PP3D has three parts:

- **Discovery.** Instrumented browsers on different device types visit suspicious pages. The screenshots are clustered and labeled to build an attack dataset.
- **Detection.** A multimodal model combines visual features from a MobileNetV3 image encoder with text features from OCR-extracted page text (BERT-mini) to classify a screenshot.
- **Defense.** The model is converted to run entirely *in the browser*, with ONNX Web Runtime for the model and Tesseract.js (WASM) for OCR, so pages are checked locally.

<div class="pa-figure">
{% include figure.html path="assets/img/projects/pp3d_overview.png" alt="PP3D framework: discovery, detection model, and in-browser defense" caption="The PP3D framework: attack discovery, the multimodal detection model, and in-browser deployment." zoomable=true %}
</div>

<div class="pa-keyfindings" markdown="1">
#### Key findings
- Over **99%** detection at a **1%** false-positive rate.
- Detection runs locally in the browser, **preserving user privacy**: screenshots never leave the device.
</div>
