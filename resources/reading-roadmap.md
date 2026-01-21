# 📚 Reading Roadmap 阅读路线图

本文档帮助不同背景的读者找到适合自己的学习路径。

---

## 🎯 新手入门 (Complete Beginner)

**目标**：理解什么是 World Model，为什么医学需要它

### Week 1-2: 基础概念

| 顺序 | 论文 | 为什么要读 | 难度 |
|------|------|-----------|------|
| 1 | [World Models (Ha & Schmidhuber, 2018)](https://arxiv.org/abs/1803.10122) | 世界模型的开山之作，概念清晰 | ⭐⭐ |
| 2 | [A Path Towards AMI (LeCun, 2022)](https://openreview.net/pdf?id=BZ5a1r-kVsf) | JEPA架构，预测latent而非pixel的思想 | ⭐⭐⭐ |

### Week 3: 医学应用综述

| 顺序 | 论文 | 为什么要读 | 难度 |
|------|------|-----------|------|
| 3 | [Beyond Generative AI (Qazi et al., 2025)](https://arxiv.org/abs/2511.16333) | 医学世界模型的全面综述，提出L1-L4框架 | ⭐⭐ |

### Week 4+: 选择方向深入

根据你的兴趣选择一个方向：

---

## 🩻 方向A: 医学影像 (Medical Imaging)

**适合人群**：对放射科、影像诊断感兴趣

### 核心论文

| 顺序 | 论文 | 能力等级 | 重点 |
|------|------|---------|------|
| 1 | CheXWorld | L1 | JEPA在X光的应用，表示学习 |
| 2 | X-WIN | L1-L2 | 从CT蒸馏3D知识到X光 |
| 3 | MeWM | L3 | 肿瘤演变模拟，Diffusion架构 |
| 4 | CLARITY | L4 | 完整的预测-决策闭环 |

### 技术栈

```
需要掌握：
├── Vision Transformer (ViT)
├── JEPA / Contrastive Learning
├── Diffusion Models
└── Medical Image Processing
```

---

## 🔬 方向B: 手术机器人 (Surgical Robotics)

**适合人群**：对手术、机器人控制感兴趣

### 核心论文

| 顺序 | 论文 | 能力等级 | 重点 |
|------|------|---------|------|
| 1 | Dreamer系列 | - | 先理解通用领域的WM-based RL |
| 2 | Surgical Vision WM | L2-L3 | 从无标注视频学习latent动作 |
| 3 | WM-Grasp | L4 | 完整的控制闭环 |

### 技术栈

```
需要掌握：
├── Reinforcement Learning
├── World Model (Dreamer架构)
├── Video Prediction
├── VQ-VAE / Tokenization
└── Sim-to-Real Transfer
```

---

## 📋 方向C: 疾病进展预测 (Disease Progression / EHR)

**适合人群**：对临床数据、电子病历感兴趣

### 核心论文

| 顺序 | 论文 | 能力等级 | 重点 |
|------|------|---------|------|
| 1 | Foresight | L1 | Transformer在EHR时序建模 |
| 2 | CoMET | L1 | Scaling laws，大规模训练 |
| 3 | Dynamic DeepHit | - | 动态生存分析（背景知识） |

### 技术栈

```
需要掌握：
├── Transformer / GPT架构
├── Survival Analysis
├── EHR Data Processing
└── Temporal Modeling
```

---

## 💊 方向D: 治疗规划 (Treatment Planning)

**适合人群**：对临床决策支持、治疗优化感兴趣

### 核心论文

| 顺序 | 论文 | 能力等级 | 重点 |
|------|------|---------|------|
| 1 | MeWM | L3 | 治疗方案比较 |
| 2 | TaDiff | L2-L3 | 治疗感知的预测 |
| 3 | CLARITY | L4 | 完整的决策闭环 |

### 技术栈

```
需要掌握：
├── Latent Space Modeling
├── Survival Analysis
├── Causal Inference (建议)
└── Clinical Domain Knowledge
```

---

## 🛠️ 代码复现指南

### 优先复现（有完整代码）

| 论文 | 难度 | 预计时间 | 硬件需求 |
|------|------|---------|---------|
| Surgical Vision WM | ⭐⭐ | 1-2周 | 1x A100 |
| CheXWorld | ⭐⭐ | 1-2周 | 1x A100 |
| Foresight | ⭐⭐ | 1周 | CPU/GPU |

### 建议顺序

```
1. 先跑通 Surgical Vision WM
   └── 理解 VQ-VAE tokenizer + Latent Action + Dynamics

2. 然后尝试 CheXWorld
   └── 理解 JEPA-style 预测学习

3. 最后挑战 CLARITY (代码开源后)
   └── 理解完整的预测-决策闭环
```

---

## 📖 补充阅读材料

### 背景知识

| 主题 | 推荐资源 |
|------|---------|
| World Models | [WorldModels.github.io](https://worldmodels.github.io/) |
| JEPA | [LeCun's Talk on JEPA](https://www.youtube.com/watch?v=DokLw1tILlw) |
| Medical AI | [AI in Medicine (Nature Reviews)](https://www.nature.com/collections/medical-ai) |

### 相关课程

| 课程 | 平台 | 内容 |
|------|------|------|
| Deep RL | Berkeley CS285 | 强化学习基础 |
| Medical Image Analysis | Coursera | 医学影像处理 |

---

## ❓ FAQ

**Q: 没有医学背景可以入门吗？**
A: 可以。建议从 Surgical Vision WM 开始，手术视频比较直观。

**Q: 没有强化学习背景可以吗？**
A: 可以。L1-L3的论文不需要RL知识，只有L4需要。

**Q: 需要什么硬件？**
A: 大多数论文需要至少1张A100 40GB GPU。部分推理可以在消费级GPU上运行。

---

[← 返回主页](../README.md)
