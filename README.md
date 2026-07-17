# PLAMD: Power Line Aerial Multi-Degradation Dataset
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.21321669.svg)](https://zenodo.org/records/21321669)
[![License](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
> **A comprehensive multi-degradation benchmark for UAV power line image restoration.**
---
## 📖 Overview
**PLAMD (Power Line Aerial Multi-Degradation Dataset)** is a large-scale synthetic dataset designed for benchmarking image restoration and enhancement algorithms in the context of **unmanned aerial vehicle (UAV) power line inspection**. It covers **seven realistic degradation scenarios** with paired clean references, supporting full-reference evaluation paradigms.
Source images are drawn from two public UAV power line inspection datasets — **InsPLAD** [<sup data-citation='{&quot;id&quot;:1,&quot;url&quot;:&quot;https://doi.org/10.1080/01431161.2023.2283900&quot;,&quot;title&quot;:&quot;InsPLAD: A Dataset and Benchmark for Power Line Asset Inspection in UAV Images&quot;,&quot;content&quot;:&quot;InsPLAD: A Dataset and Benchmark for Power Line Asset Inspection in UAV Images International Journal of Remote Sensing, 2023 57 citations Power line maintenance and inspection are essential to avoid p&quot;}'>1</sup>](https://doi.org/10.1080/01431161.2023.2283900) and **TTPLA** [<sup data-citation='{&quot;id&quot;:2,&quot;url&quot;:&quot;https://arxiv.org/abs/2311.01619&quot;,&quot;title&quot;:&quot;InsPLAD: A Dataset and Benchmark for Power Line Asset ...&quot;,&quot;content&quot;:&quot;InsPLAD: A Dataset and Benchmark for Power Line Asset Inspection in UAV Images arXiv Cornell University, 2023 Preprint 1 citation Power line maintenance and inspection are essential to avoid power sup&quot;}'>2</sup>](https://arxiv.org/abs/2311.01619) — ensuring strong domain relevance for the power industry. Each image is then synthetically degraded using physically motivated or learning-based generation pipelines.
---
## ✨ Key Features
| Feature | Description |
|---------|-------------|
| **7 Degradation Types** | Blur (motion), Haze, Inpainting, Low-light, Noise, Rain, Snow |
| **Realistic UAV Perspective** | All source images from real UAV power line inspection footage (InsPLAD + TTPLA) |
| **Full-Reference Evaluation** | Each degraded image has a paired clean reference |
| **3 Severity Levels** | Random parameter ranges during generation, yielding Light / Moderate / Severe degradation per image |
| **Fine-Grained Component Subsets** | 20 categories organized by power line component type for targeted research |
| **Intact & Defect Coverage** | Both normal-condition and defect-present component images included |
### Degradation Types
| Degradation | Simulated Scenario |
|-------------|-------------------|
| **Blur (Motion)** | Camera shake during UAV flight: physics-based random trajectory synthesis |
| **Haze** | Atmospheric scattering with depth-aware fog concentration |
| **Inpainting** | Partial occlusion: irregular, stripe, and mixed mask patterns |
| **Low-light** | Dusk/dawn or inadequate illumination simulation |
| **Noise** | Realistic camera sensor noise (signal-dependent + signal-independent) |
| **Rain** | Rain streaks with tunable density, length, angle, and opacity |
| **Snow** | 5 snow conditions: streaking snow, fine snow, fluffy snow, and light ice accumulation |
---
## 📂 Dataset Structure
PLAMD is distributed as **7 compressed archives**, one per degradation type. Each archive shares an identical internal hierarchy organized by **power line component category**. Images are provided as **degraded–clean pairs** for full-reference training and evaluation.
{degradation_type}.zip            # e.g., haze.zip, rain.zip, snow.zip ...
│
├── {degradation_type}/           # All degraded images (e.g., haze/, rain/, snow/ ...)
│   ├── component_mix_1K/
│   ├── damper-preformed/
│   ├── damper-stockbridge/
│   ├── glass-insulator/
│   ├── glass-insulator-big-shackle/
│   ├── glass-insulator-small-shackle/
│   ├── glass-insulator-tower-shackle/
│   ├── lightning-rod-shackle/
│   ├── lightning-rod-suspension/
│   ├── overallL_2K/
│   ├── plate/
│   ├── polymer-insulator/
│   ├── polymer-insulator-lower-shackle/
│   ├── polymer-insulator-tower-shackle/
│   ├── polymer-insulator-upper-shackle/
│   ├── vari-grip/
│   ├── yoke/
│   └── yoke-suspension/
│
└── original/                     # Original clean reference images (identical structure)
    ├── component_mix_1K/
    ├── damper-preformed/
    ├── damper-stockbridge/
    ├── glass-insulator/
    ├── glass-insulator-big-shackle/
    ├── glass-insulator-small-shackle/
    ├── glass-insulator-tower-shackle/
    ├── lightning-rod-shackle/
    ├── lightning-rod-suspension/
    ├── overallL_2K/
    ├── plate/
    ├── polymer-insulator/
    ├── polymer-insulator-lower-shackle/
    ├── polymer-insulator-tower-shackle/
    ├── polymer-insulator-upper-shackle/
    ├── vari-grip/
    ├── yoke/
    └── yoke-suspension/
---
### Design Notes
- **`component_mix_1K`**: a curated subset containing mixed component images at approximately **1K resolution**, useful for quick prototyping and lightweight experiments.
- **`overallL_2K`**: wide-view overall-scene images at approximately **2K resolution** (e.g., full transmission towers, multi-component line spans). Ideal for context-aware or scene-level restoration models.
- All other categories contain images at **varying resolutions** depending on the original source crops.
- Each category folder contains subfolders `clean/` (reference) and `degraded/` (degraded at random severity levels). The three severity levels (Light / Moderate / Severe) are controlled by **random parameter ranges during generation** rather than by explicit L1/L2/L3 subfolders.
- Each category includes both **intact** (完好) and **defect** (缺损) component images sourced from InsPLAD and TTPLA, enabling research on restoration quality across varying asset conditions.
---
## 📊 Dataset Statistics
| Property | Value |
|----------|-------|
| Total degradation types | 7 |
| Blur (motion) | 38,865 |
| Haze | 38,865 |
| Inpainting | 39,699 |
| Low-light | 38,865 |
| Noise | 27,802 |
| Rain | 39,699 |
| Snow | 39,699 |
| **Total images** | **~302,500** (degraded–clean pairs) |
| Severity levels per type | 3 (random parameter ranges) |
| Image format | JPG |
| Component categories | 20 |
| Source datasets | InsPLAD [1] + TTPLA [2] |
> **Note on class balance**: Due to the stochastic nature of the data augmentation pipeline, a small subset of generated images exhibited suboptimal quality and were manually filtered out. The noisy subset contains the fewest images due to file-size limitations, while the other six tasks differ by no more than 5% from one another. These variations are negligible for standard training workflows.
---
## 🛠️ Degradation Synthesis Methods
All degradations are applied synthetically to clean source images, ensuring **pixel-aligned degraded–clean pairs**.
| Degradation | Method | Description |
|-------------|--------|-------------|
| **Haze** | Atmospheric Scattering Model [3] + Monodepth2 [4] | Depth-aware fog/haze at various concentrations; Monodepth2 estimates depth maps from single images to modulate transmission maps |
| **Rain** | Rain-Generation-Python [5] | Streak-based rain rendering with tunable density, length, angle, and opacity |
| **Snow** | AutoSnow [6] | Synthetic winter image generation framework supporting 5 snow conditions: streaking snow, fine snow, fluffy snow, and light ice accumulation |
| **Motion Blur** | Camera Shake Blur (CSB) generator | Physics-based random camera shake trajectory synthesis producing realistic motion blur kernels |
| **Low-Light** | Gamma correction + Poisson-Gaussian noise | Low-illumination evening/dusk scene simulation via non-linear intensity attenuation and realistic noise injection |
| **Noise** | NoiseDiff (TPAMI 2025) [7] | Dark noise diffusion model for realistic sRGB noise synthesis (signal-dependent + signal-independent) |
| **Inpainting** | OpenCV-based random mask generation | Irregular shapes, stripes, and mixed mask patterns simulating partial occlusion |
---
## 📥 Download
| Platform | Link |
|----------|------|
| **Zenodo** | [https://zenodo.org/records/21321669](https://zenodo.org/records/21321669) |
| **Baidu Netdisk** | [链接](https://pan.baidu.com/s/1JUn03mTiTKXxSdXSjFs0Aw?pwd=8age) 提取码: `8age` |
---
## 🧪 How to Build an All-in-One Training Set
Since PLAMD is organized by degradation type, construct an **All-in-One** training set by sampling from each category. A recommended mixing ratio:
| Degradation | Suggested Ratio |
|-------------|:---:|
| Haze | 25% |
| Rain | 20% |
| Snow | 15% |
| Blur | 15% |
| Low-Light | 15% |
| Noise | 5% |
| Inpainting | 5% |
Adjust based on deployment requirements (e.g., higher snow ratio for winter operations, higher low-light ratio for nighttime inspection).
---
## 🎯 Intended Use
1. **Single-task restoration**: Train and evaluate on individual degradation types (dehazing, deraining, desnowing, deblurring, denoising, low-light enhancement, inpainting).
2. **All-in-One restoration**: Mix categories to train a unified model handling diverse degradations.
3. **Fine-grained component analysis**: Use component-level subsets to study restoration quality on specific assets (glass insulator, polymer insulator, damper, yoke, etc.).
4. **Intact vs. Defect study**: Investigate whether degraded restoration disproportionately affects defect visibility — a critical safety concern for power line inspection.
5. **Domain adaptation validation**: Compare models trained on PLAMD vs. generic datasets to demonstrate the necessity of power-domain-specific data.
---
## 📄 License
This dataset is licensed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license. You are free to share and adapt the data, provided you give appropriate credit.
---
## 📝 Citation
If you use PLAMD in your research, please cite:
```bibtex
@dataset{yang2025plamd,
  author       = {Jingke Yang},
  title        = {{PLAMD}: A Comprehensive Multi-Degradation Dataset for
                   {UAV} Power Line Image Restoration},
  year         = {2025},
  publisher    = {Zenodo},
  doi          = {10.5281/zenodo.21321669},
  url          = {https://doi.org/10.5281/zenodo.21321669}
}
---
🙏 Acknowledgement
PLAMD builds upon two publicly available UAV power line inspection datasets. Please also cite:
InsPLAD [1]:
@article{InsPLAD2023,
  author    = {André Luiz Buarque Vieira e Silva and Heitor de Castro Felix
               and Franscisco Paulo Magalhães Simões and Veronica Teichrieb
               and Michel dos Santos and Hemir Santiago and Virginia Sgotti
               and Henrique Lott Neto},
  title     = {{InsPLAD}: A Dataset and Benchmark for Power Line Asset
               Inspection in {UAV} Images},
  journal   = {International Journal of Remote Sensing},
  volume    = {44},
  number    = {23},
  pages     = {1--27},
  year      = {2023},
  publisher = {Taylor \& Francis},
  doi       = {10.1080/01431161.2023.2283900}
}

TTPLA [2]:
@inproceedings{TTPLA2020,
  author    = {Abdelfattah, Rabab and Wang, Xiaofeng and Wang, Song},
  title     = {{TTPLA}: An Aerial-Image Dataset for Detection and
               Segmentation of Transmission Towers and Power Lines},
  booktitle = {Proceedings of the Asian Conference on Computer Vision (ACCV)},
  year      = {2020}
}
[3] Narasimhan, S. G., & Nayar, S. K. (2002). Vision and the atmosphere. IJCV, 48(3), 233–254.

[4] Godard, C., Mac Aodha, O., Firman, M., & Brostow, G. J. (2019). Digging into self-supervised monocular depth estimation. ICCV 2019.

[5] Shen Zheng. Rain-Generation-Python. https://github.com/ShenZheng2000/Rain-Generation-Python

[6] Amardeep Sarang. AutoSnow: A Synthetic Winter Image Generator Framework. https://github.com/AmardeepSarang/AutoSnow-A-synthetic-winter-image-generator-framework

[7] NoiseDiff: Dark Noise Diffusion — Noise Synthesis for Low-Light Image Denoising (TPAMI 2025). IVRL. https://github.com/IVRL/NoiseDiff



