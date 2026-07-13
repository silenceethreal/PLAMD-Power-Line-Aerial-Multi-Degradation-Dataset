# UAV-PowerLine-Degradation-Dataset
> [!IMPORTANT]
> ## 📦 Dataset Upload in Progress
> The dataset is currently being uploaded to Zenodo and BaiduNetdisk(finished). The download link will be updated here as soon as the upload is complete. Please **Watch** this repository or check back shortly. Thank you for your patience!
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
- **Fine-Grained Severity Labels**: Each degradation type includes random three
  severity levels: **Light (L1), Moderate (L2), and Severe (L3)**,
  enabling controlled difficulty escalation.
- **Object Detection Ready**: Annotations for power line components are
  provided in YOLO TXT format, with detection performance evaluable via
  the **Pseudo-Pseudo-I2I Metric (PPI2I)**.

## Download links
Zenodo: still being uploaded
BaiduNetdisk:通过网盘分享的文件：PLAMD_Power Line Aerial Multi-Degradation Dataset
链接: https://pan.baidu.com/s/1JUn03mTiTKXxSdXSjFs0Aw?pwd=8age 提取码: 8age 
--来自百度网盘超级会员v7的分享

## How to Build an All-in-One Training Set

Since PLAMD is organized by degradation type, researchers can
construct an All-in-One training set by sampling from each category.
A recommended mixing ratio is provided below as a starting point:

| Degradation | Suggested Ratio |
|-------------|:---:|
| Haze | 25% |
| Rain | 20% |
| Snow | 15% |
| Blur | 15% |
| Low-Light | 15% |
| Noise | 5% |
| Inpainting | 5% |

The mixing ratio can be adjusted based on specific deployment
requirements (e.g., higher snow ratio for winter operations).

## Dataset Statistics

| Property | Value |
|----------|-------|
| Total degradation types | 7 |
| blur | 38,865 |
| haze | 38,865 |
| inpainting | 39,699 |
| lowlight | 38,865 |
| noise | 27,802] |
| rain | 39,699 |
| snow | 39,699 |
| File format | JPG |
| Compression | ZIP |

## Intended Use

1. **Single-task restoration**: training and evaluating models on
   individual degradation types (dehazing, deraining, etc.)
2. **All-in-One restoration**: mixing multiple categories to train
   a unified model handling diverse degradations
3. **Domain adaptation validation**: comparing models trained on
   PLAMD vs. generic datasets to demonstrate the necessity of
   power-domain-specific data
4. **Downstream task evaluation**: assessing whether restored
   images improve power asset detection/segmentation performance

Note on Class Balance: Due to the stochastic nature of the data augmentation pipeline, a small subset of generated images exhibited suboptimal quality and were manually filtered out during post-processing. As a result, the seven degradation tasks exhibit minor sample count discrepancies. Specifically, the noisy subset contains the fewest images due to file-size-limitaion, while the other six tasks differ by no more than 5% from one another. These variations are negligible for standard training workflows but should be noted in fairness-aware or class-balanced evaluation settings.



## Citation

If you use PLAMD in your research, please cite:

@dataset{plamd2025, title = {PLAMD: A Comprehensive Multi-Degradation Dataset for UAV Power Line Image Restoration}, author = {[Jingke Yang]}, year = {2025}, publisher = {Zenodo}, doi = {[10.5281/zenodo.21321669]}, }
