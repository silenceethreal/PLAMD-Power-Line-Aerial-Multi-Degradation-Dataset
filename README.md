# UAV-PowerLine-Degradation-Dataset
> [!IMPORTANT]
> ## 📦 Dataset Upload in Progress
> The dataset is currently being uploaded to Zenodo and BaiduNetdisk. The download link will be updated here as soon as the upload is complete. Please **Watch** this repository or check back shortly. Thank you for your patience!
---
## Overview
The **UAV PowerLine Degradation Dataset** is designed for benchmarking
image restoration and enhancement algorithms in the context of **unmanned
aerial vehicle (UAV) power line inspection**. It contains synthetically
degraded images simulating seven real-world degradation scenarios, with
paired clean references and unpaired test targets to support multiple
training and evaluation paradigms.
## Key Features
- **7 Degradation Tasks**: A unified clean-paired benchmark covering haze,
  rain, snow, motion blur, defocus blur, noise, and dark (low-light)
  conditions.
- **Realistic UAV Perspective**: All images are sourced from actual UAV
  power line inspection footage, ensuring domain relevance.
- **Dual Benchmark Support**: The dataset structure supports both
  **full-reference (paired)** and **no-reference (unpaired)** evaluation
  protocols.
- **Fine-Grained Severity Labels**: Each degradation type includes three
  severity levels: **Light (L1), Moderate (L2), and Severe (L3)**,
  enabling controlled difficulty escalation.
- **Object Detection Ready**: Annotations for power line components are
  provided in YOLO TXT format, with detection performance evaluable via
  the **Pseudo-Pseudo-I2I Metric (PPI2I)**.
