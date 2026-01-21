# Reading Roadmap

This document helps readers from different backgrounds find appropriate learning paths.

---

## Getting Started (Complete Beginner)

**Goal**: Understand what World Models are and why healthcare needs them

### Week 1-2: Foundational Concepts

| Order | Paper | Why Read It | Difficulty |
|-------|-------|-------------|------------|
| 1 | [World Models (Ha & Schmidhuber, 2018)](https://arxiv.org/abs/1803.10122) | The seminal work on world models, clear concepts | ⭐⭐ |
| 2 | [A Path Towards AMI (LeCun, 2022)](https://openreview.net/pdf?id=BZ5a1r-kVsf) | JEPA architecture, predicting latent instead of pixels | ⭐⭐⭐ |

### Week 3: Medical Applications Survey

| Order | Paper | Why Read It | Difficulty |
|-------|-------|-------------|------------|
| 3 | [Beyond Generative AI (Qazi et al., 2025)](https://arxiv.org/abs/2511.16333) | Comprehensive survey of medical world models, proposes L1-L4 framework | ⭐⭐ |

### Week 4+: Choose a Direction

Based on your interests, choose a direction to dive deeper:

---

## Direction A: Medical Imaging

**Target Audience**: Those interested in radiology and imaging diagnostics

### Core Papers

| Order | Paper | Capability Level | Focus |
|-------|-------|------------------|-------|
| 1 | CheXWorld | L1 | JEPA applied to X-rays, representation learning |
| 2 | X-WIN | L1-L2 | Distilling 3D knowledge from CT to X-rays |
| 3 | MeWM | L3 | Tumor evolution simulation, Diffusion architecture |
| 4 | CLARITY | L4 | Complete prediction-to-decision closed-loop |

### Technical Stack

```
Prerequisites:
├── Vision Transformer (ViT)
├── JEPA / Contrastive Learning
├── Diffusion Models
└── Medical Image Processing
```

---

## Direction B: Surgical Robotics

**Target Audience**: Those interested in surgery and robotic control

### Core Papers

| Order | Paper | Capability Level | Focus |
|-------|-------|------------------|-------|
| 1 | Dreamer Series | - | First understand WM-based RL in general domain |
| 2 | Surgical Vision WM | L2-L3 | Learning latent actions from unlabeled video |
| 3 | WM-Grasp | L4 | Complete control closed-loop |

### Technical Stack

```
Prerequisites:
├── Reinforcement Learning
├── World Model (Dreamer architecture)
├── Video Prediction
├── VQ-VAE / Tokenization
└── Sim-to-Real Transfer
```

---

## Direction C: Disease Progression / EHR

**Target Audience**: Those interested in clinical data and electronic health records

### Core Papers

| Order | Paper | Capability Level | Focus |
|-------|-------|------------------|-------|
| 1 | Foresight | L1 | Transformer for EHR temporal modeling |
| 2 | CoMET | L1 | Scaling laws, large-scale training |
| 3 | Dynamic DeepHit | - | Dynamic survival analysis (background) |

### Technical Stack

```
Prerequisites:
├── Transformer / GPT Architecture
├── Survival Analysis
├── EHR Data Processing
└── Temporal Modeling
```

---

## Direction D: Treatment Planning

**Target Audience**: Those interested in clinical decision support and treatment optimization

### Core Papers

| Order | Paper | Capability Level | Focus |
|-------|-------|------------------|-------|
| 1 | MeWM | L3 | Treatment protocol comparison |
| 2 | TaDiff | L2-L3 | Treatment-aware prediction |
| 3 | CLARITY | L4 | Complete decision closed-loop |

### Technical Stack

```
Prerequisites:
├── Latent Space Modeling
├── Survival Analysis
├── Causal Inference (recommended)
└── Clinical Domain Knowledge
```

---

## Code Reproduction Guide

### Priority (Full Code Available)

| Paper | Difficulty | Est. Time | Hardware |
|-------|------------|-----------|----------|
| Surgical Vision WM | ⭐⭐ | 1-2 weeks | 1x A100 |
| CheXWorld | ⭐⭐ | 1-2 weeks | 1x A100 |
| Foresight | ⭐⭐ | 1 week | CPU/GPU |

### Recommended Order

```
1. Start with Surgical Vision WM
   └── Understand VQ-VAE tokenizer + Latent Action + Dynamics

2. Then try CheXWorld
   └── Understand JEPA-style predictive learning

3. Finally challenge CLARITY (when code is released)
   └── Understand complete prediction-to-decision closed-loop
```

---

## Supplementary Materials

### Background Knowledge

| Topic | Recommended Resource |
|-------|---------------------|
| World Models | [WorldModels.github.io](https://worldmodels.github.io/) |
| JEPA | [LeCun's Talk on JEPA](https://www.youtube.com/watch?v=DokLw1tILlw) |
| Medical AI | [AI in Medicine (Nature Reviews)](https://www.nature.com/collections/medical-ai) |

### Related Courses

| Course | Platform | Content |
|--------|----------|---------|
| Deep RL | Berkeley CS285 | Reinforcement learning fundamentals |
| Medical Image Analysis | Coursera | Medical image processing |

---

## FAQ

**Q: Can I get started without a medical background?**
A: Yes. We recommend starting with Surgical Vision WM as surgical videos are relatively intuitive.

**Q: Can I get started without reinforcement learning background?**
A: Yes. L1-L3 papers don't require RL knowledge; only L4 does.

**Q: What hardware do I need?**
A: Most papers require at least one A100 40GB GPU. Some inference can run on consumer-grade GPUs.

---

[← Back to Home](../README.md)
