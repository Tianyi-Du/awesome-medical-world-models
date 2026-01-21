# Awesome Medical World Models

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)
[![Last Update](https://img.shields.io/badge/last%20update-January%202025-blue)]()

> A curated list of **World Models for Healthcare**: prediction, simulation, counterfactual reasoning, and clinical decision support.
>
> 医学世界模型论文精选列表：预测、模拟、反事实推理与临床决策支持

<p align="center">
  <img src="figures/overview.png" width="700">
</p>

---

## Table of Contents

- [What is Medical World Model?](#what-is-medical-world-model)
- [Capability Levels (L1-L4)](#capability-levels-l1-l4)
- [Survey \& Review](#survey--review)
- [Papers by Application](#papers-by-application)
  - [Medical Imaging \& Diagnostics](#medical-imaging--diagnostics)
  - [Surgical Vision \& Robotics](#surgical-vision--robotics)
  - [Disease Progression (EHR)](#disease-progression-ehr)
  - [Treatment Planning](#treatment-planning)
- [Capability Matrix](#capability-matrix)
- [Foundation World Models](#foundation-world-models)
- [Datasets \& Benchmarks](#datasets--benchmarks)
- [Open-Source Projects](#open-source-projects)
- [Reading Roadmap](#reading-roadmap)
- [Contributing](#contributing)
- [Citation](#citation)

---

## What is Medical World Model?

**World Model（世界模型）** 是一种学习环境动态的内部模拟器，核心是学习状态转移函数：

```
p(s_{t+1} | s_t, a_t)
```

给定当前状态 `s_t` 和动作 `a_t`，预测下一个状态 `s_{t+1}`。

### Why Healthcare Needs World Models? 为什么医学需要世界模型？

| 传统AI (Traditional AI) | World Model (世界模型) |
|------------------------|----------------------|
| 静态预测："这是肿瘤" | 动态模拟："治疗后肿瘤会如何变化" |
| Static: "This is a tumor" | Dynamic: "How will the tumor evolve after treatment" |
| 单一输出 | 多步rollout，可视化轨迹 |
| Single output | Multi-step rollout, visualize trajectory |
| 无法回答 what-if | 支持反事实推理 |
| Cannot answer what-if | Supports counterfactual reasoning |
| 黑盒决策 | 可解释的规划过程 |
| Black-box decision | Interpretable planning process |

### World Model vs Generative Model 世界模型 vs 生成模型

```
生成模型 (Generative Model, e.g., Diffusion):
  Input: Noise → Output: Realistic image
  Goal: Visual fidelity (视觉保真度)

世界模型 (World Model):
  Input: State + Action → Output: Next state
  Goal: Dynamic consistency + Causal correctness (动态一致性 + 因果正确性)
```

---

## Capability Levels (L1-L4)

基于 [Qazi et al., 2025](https://arxiv.org/abs/2511.16333) 提出的能力分级框架：

| Level | Name | Capability | Example |
|-------|------|------------|---------|
| **L1** | Temporal Prediction | 预测未来状态 | Predict future medical images |
| **L2** | Action-Conditioned | 基于动作的条件预测 | Predict based on treatment/probe movement |
| **L3** | Counterfactual Rollouts | 反事实推理，决策支持 | "What if we use drug A instead of B?" |
| **L4** | Planning & Control | 闭环规划，实时控制 | Autonomous surgical planning |

```
L1 ──────► L2 ──────► L3 ──────► L4
时序预测    动作条件    反事实推演   规划控制
Temporal   Action     Counterfactual  Planning
```

---

## Survey & Review

| Title | Venue | Year | Links |
|-------|-------|------|-------|
| **Beyond Generative AI: World Models for Clinical Prediction, Counterfactuals, and Planning** | NeurIPS Workshop | 2025 | [[PDF](https://arxiv.org/abs/2511.16333)] |

---

## Papers by Application

### Medical Imaging & Diagnostics

#### Radiology (X-ray / CT)

**X-WIN: Building Chest Radiograph World Model via Predictive Sensing.** [Nov 2025]<br>
*Zefan Yang, Ge Wang, James Hendler, Mannudeep K. Kalra, Pingkun Yan.*<br>
`L1-L2` `X-ray` `CT` `JEPA-style` `3D Knowledge Distillation`<br>
[[PDF](https://arxiv.org/abs/2511.14918)]

> 从3D CT蒸馏知识到2D X光世界模型，通过预测不同角度的投影来学习3D解剖结构。

**CheXWorld: Exploring Image World Modeling for Radiograph Representation Learning.** [CVPR 2025]<br>
*Yang Yue, Yulin Wang, Chenxin Tao, Pan Liu, Shiji Song, Gao Huang.*<br>
`L1` `X-ray` `JEPA-style` `Representation Learning`<br>
[[PDF](https://arxiv.org/abs/2504.13820)]

> 使用JEPA风格的预测学习目标，学习X光片的局部解剖、全局布局和领域变化表示。

**Xray2Xray: World Model from Chest X-rays with Volumetric Context.** [Jun 2025]<br>
*Zefan Yang, Xinrui Song, Xuanang Xu, et al.*<br>
`L1` `X-ray` `Volumetric` `Projection Transition`<br>
[[PDF](https://arxiv.org/abs/2506.19055)]

> 通过建模投影转换动态学习3D体积上下文。

---

#### MRI & Tumor Modeling

**CLARITY: Medical World Model for Guiding Treatment Decisions by Modeling Context-Aware Disease Trajectories in Latent Space.** [Dec 2025]<br>
*Tianxingjian Ding, Yuanhao Zou, Chen Chen, Mubarak Shah, Yu Tian.*<br>
`L4` `MRI` `Glioma` `Latent-space` `Treatment Planning` `Survival Analysis`<br>
[[PDF](https://arxiv.org/abs/2512.08029)] [[Project](https://dingtianxingjian.github.io/clarity-project-page/)]

> 在latent空间建模疾病演变轨迹，整合时间和临床上下文，通过逆向生存评估实现预测到决策的闭环。

**MeWM: Medical World Model for Tumor Evolution Simulation.** [Jun 2025]<br>
*Yijun Yang, Zhao-Yang Wang, Qiuping Liu, et al.*<br>
`L3` `CT` `Tumor` `Diffusion-based` `Treatment Simulation`<br>
[[PDF](https://arxiv.org/abs/2506.02327)]

> 动作条件3D生成器，模拟治疗后肿瘤状态，用于方案选择。

**TaDiff: Treatment-aware Diffusion Probabilistic Model for Longitudinal MRI Generation.** [Sep 2023]<br>
*Q. Liu, et al.*<br>
`L2-L3` `MRI` `Glioma` `Diffusion` `Longitudinal`<br>
[[PDF](https://arxiv.org/abs/2309.05406)]

> 治疗感知的扩散模型，预测弥漫性胶质瘤在不同治疗方案下的纵向MRI演变。

**mi-GAN: Multi-Information GAN for Alzheimer's Disease Progression Prediction.** [2021]<br>
*Y. Zhao, B. Ma, P. Jiang, et al.*<br>
`L1` `MRI` `Alzheimer` `GAN` `Progression`<br>
[[PDF](https://ieeexplore.ieee.org/document/9311194)]

> 多信息GAN从基线扫描预测未来3D脑部MRI，建模阿尔茨海默病进展。

---

#### Ultrasound

**EchoWorld: Learning Motion-Aware World Models for Echocardiography Probe Guidance.** [CVPR 2025]<br>
*Yang Yue, Yulin Wang, Haojun Jiang, Pan Liu, Shiji Song, Gao Huang.*<br>
`L2` `Ultrasound` `Cardiac` `Probe Guidance` `Motion-Aware`<br>
[[PDF](https://arxiv.org/abs/2504.xxxxx)]

> 运动感知的心脏超声世界模型，编码解剖结构和探头运动效果，降低平面引导误差。

**Cardiac Copilot: Automatic Probe Guidance for Echocardiography with World Model.** [MICCAI 2024]<br>
*Haojun Jiang, Zhenguo Sun, Ning Jia, et al.*<br>
`L2` `Ultrasound` `Cardiac` `Navigation` `Real-time`<br>
[[PDF](https://arxiv.org/abs/2406.xxxxx)]

> 引入"Cardiac Dreamer"世界模型，latent空间特征提供导航地图，实现实时探头引导。

---

### Surgical Vision & Robotics

**Surgical Vision World Model.** [Sep 2025]<br>
*Saurabh Koju, Saurav Bastola, Prashant Shrestha, Sanskar Amgain, Yash Raj Shrestha, Rudra P.K. Poudel, Binod Bhattarai.*<br>
`L2-L3` `Surgical Video` `Latent Action` `da Vinci` `Unlabeled Data`<br>
[[PDF](https://arxiv.org/abs/2503.02904)] [[Github](https://github.com/bhattarailab/Surgical-Vision-World-Model)]

> 首个手术视觉世界模型，从无标注手术视频学习latent动作，实现动作可控的手术数据生成。

**World Models for General Surgical Grasping.** [May 2024]<br>
*Guangyao Lin, Xinyue Yan, Yuzhou Hu, et al.*<br>
`L4` `Surgical Robotics` `Grasping` `Reinforcement Learning` `Sim-to-Real`<br>
[[PDF](https://arxiv.org/abs/2405.17940)]

> 基于世界模型的强化学习控制器，实现通用手术抓取，对物体变化和扰动具有鲁棒性。

---

### Disease Progression (EHR)

**Foresight: A Generative Pretrained Transformer for Modelling Patient Timelines.** [Lancet Digital Health, 2024]<br>
*Zeljko Kraljevic, Dan Bean, Anthony Shek, et al.*<br>
`L1` `EHR` `Transformer` `Event Forecasting` `Large-scale`<br>
[[PDF](https://www.thelancet.com/journals/landig/article/PIIS2589-7500(24)00025-6/fulltext)]

> 生成式Transformer，将临床文本转换为编码概念，自回归预测未来疾病、手术、用药等事件。

**CoMET: Generative Medical Event Models Improve with Scale.** [Aug 2025]<br>
*Shane Waxler, Paul Blazek, Davis White, et al. (Microsoft/Epic)*<br>
`L1` `EHR` `Scaling Laws` `Billions of Events` `Epic Cosmos`<br>
[[PDF](https://arxiv.org/abs/2508.12104)]

> 在数十亿医疗事件上训练decoder-only Transformer，展示scaling laws，改进多任务预测。

---

### Treatment Planning

**CLARITY** (见上方 MRI & Tumor Modeling 部分)<br>
`L4` `Treatment Planning` `Inverse Survival Evaluation`

**MeWM** (见上方 MRI & Tumor Modeling 部分)<br>
`L3` `Protocol Selection` `Action-Conditioned`

---

## Capability Matrix

一目了然地比较各论文的能力等级：

| Paper | L1 | L2 | L3 | L4 | Domain | Architecture |
|-------|:--:|:--:|:--:|:--:|--------|--------------|
| CheXWorld | ✅ | | | | Radiology | JEPA |
| X-WIN | ✅ | ✅ | | | Radiology | JEPA |
| Xray2Xray | ✅ | | | | Radiology | Transformer |
| EchoWorld | | ✅ | | | Ultrasound | World Model |
| Cardiac Copilot | | ✅ | | | Ultrasound | WM + Nav |
| MeWM | | ✅ | ✅ | | Tumor/CT | Diffusion |
| TaDiff | | ✅ | ✅ | | MRI/Glioma | Diffusion |
| CLARITY | | ✅ | ✅ | ✅ | MRI/Treatment | Latent Dynamics |
| mi-GAN | ✅ | | | | MRI/Alzheimer | GAN |
| Surgical Vision WM | | ✅ | ✅ | | Surgery | VQ-VAE + Transformer |
| WM-Grasp | | | | ✅ | Surgical Robotics | Dreamer-style |
| Foresight | ✅ | | | | EHR | Transformer |
| CoMET | ✅ | | | | EHR | Transformer |

---

## Foundation World Models

通用领域的世界模型奠基工作，对理解医学应用至关重要：

| Paper | Year | Venue | Key Contribution |
|-------|------|-------|------------------|
| [World Models](https://arxiv.org/abs/1803.10122) | 2018 | NeurIPS | VAE + RNN 架构原型 |
| [Dreamer](https://arxiv.org/abs/1912.01603) | 2019 | ICLR | Latent imagination for RL |
| [DreamerV2](https://arxiv.org/abs/2010.02193) | 2020 | ICLR | Discrete latents |
| [MuZero](https://www.nature.com/articles/s41586-020-03051-4) | 2020 | Nature | Planning without environment model |
| [DreamerV3](https://arxiv.org/abs/2301.04104) | 2023 | ICLR | Mastering diverse domains |
| [A Path Towards AMI (JEPA)](https://openreview.net/pdf?id=BZ5a1r-kVsf) | 2022 | OpenReview | Predict latent, not pixels |
| [V-JEPA](https://arxiv.org/abs/2404.08471) | 2024 | arXiv | Video understanding via JEPA |
| [Genie](https://arxiv.org/abs/2402.15391) | 2024 | ICML | Generative interactive environments |

---

## Datasets & Benchmarks

| Dataset | Modality | Size | Task | Availability |
|---------|----------|------|------|--------------|
| [SurgToolLoc-2022](https://surgtoolloc.grand-challenge.org/) | Surgical Video | 24,695 clips | Tool Localization | 🔓 Public |
| [MIMIC-CXR](https://physionet.org/content/mimic-cxr/2.0.0/) | Chest X-ray | 377K images | Diagnosis | 🔐 Credentialed |
| [NLST](https://cdas.cancer.gov/nlst/) | Chest CT | 32K scans | Lung Screening | 🔐 Application |
| [MU-Glioma-Post](https://www.cancerimagingarchive.net/) | Brain MRI | 203 patients | Tumor Progression | 🔓 Public |
| [UCSF-ALPTDG](https://www.cancerimagingarchive.net/) | Brain MRI | 298 patients | Glioma Follow-up | 🔓 Public |
| [I-SPY2](https://www.ispytrials.org/) | Breast MRI + Clinical | Multi-center | Treatment Response | 🔐 Application |

---

## Open-Source Projects

| Project | Description | Code | Stars |
|---------|-------------|------|-------|
| Surgical Vision World Model | 动作可控手术视频生成 | [Github](https://github.com/bhattarailab/Surgical-Vision-World-Model) | ![](https://img.shields.io/github/stars/bhattarailab/Surgical-Vision-World-Model?style=social) |
| CLARITY | 治疗决策世界模型 | 🔜 Coming Soon | - |
| CheXWorld | X光表示学习 | 🔜 Coming Soon | - |

---

## Reading Roadmap

### 新手入门路线 (For Beginners)

```
Step 1: 理解 World Model 基础概念
        ├── Ha & Schmidhuber, "World Models" (2018) ⭐ 必读
        └── LeCun, "A Path Towards Autonomous Machine Intelligence" (2022)

Step 2: 了解医学领域的应用场景
        └── Qazi et al., "Beyond Generative AI" (2025) ⭐ 必读

Step 3: 根据兴趣深入具体方向
        ├── 影像诊断 → CheXWorld, X-WIN
        ├── 手术机器人 → Surgical Vision WM, WM-Grasp
        ├── 肿瘤治疗 → CLARITY, MeWM
        └── 疾病预测 → Foresight, CoMET
```

### 代码复现指南 (For Reproduction)

| Paper | Code Availability | Difficulty | Framework |
|-------|-------------------|------------|-----------|
| Surgical Vision WM | ✅ Full | ⭐⭐ Medium | PyTorch |
| CheXWorld | ✅ Available | ⭐⭐ Medium | PyTorch |
| CLARITY | 🔜 Coming | ⭐⭐⭐ Hard | PyTorch |
| MeWM | ❓ Unknown | - | - |
| Foresight | ✅ Available | ⭐⭐ Medium | PyTorch |

---

## Contributing

欢迎贡献新论文！请参阅 [CONTRIBUTING.md](CONTRIBUTING.md)

### 快速添加论文

提交 Issue 或 PR，包含以下信息：
- 论文标题、作者、年份
- arXiv/会议链接
- 能力等级 (L1-L4)
- 应用领域标签
- Github链接（如有）

---

## Citation

如果这个列表对您的研究有帮助，请考虑引用：

```bibtex
@misc{awesome-medical-world-models,
  author = {Your Name},
  title = {Awesome Medical World Models},
  year = {2025},
  publisher = {GitHub},
  url = {https://github.com/YOUR_USERNAME/awesome-medical-world-models}
}
```

---

## Acknowledgments

感谢所有论文作者的贡献，以及 [awesome-medical-vision-language-models](https://github.com/yangzhou12/awesome-medical-vision-language-models) 提供的格式参考。

---

<div align="center">
  <b>Made with ❤️ for the Medical AI Community</b>
  <br><br>
  <a href="#awesome-medical-world-models">⬆️ Back to Top</a>
</div>
