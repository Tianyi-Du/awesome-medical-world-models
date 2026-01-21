# Contributing to Awesome Medical World Models

Thank you for your interest in contributing! We welcome all forms of contributions.

---

## How to Add a Paper

### Option 1: Submit an Issue

1. Click [New Issue](../../issues/new)
2. Fill in the information using this template:

```markdown
### Paper Information

**Title:**
**Authors:**
**Year:**
**Venue:**
**PDF Link:**
**Github Link:** (if available)

### Classification

**Capability Level:** L1 / L2 / L3 / L4
**Application Domain:**
- [ ] Medical Imaging (Radiology/MRI/Ultrasound)
- [ ] Surgical Vision & Robotics
- [ ] Disease Progression (EHR)
- [ ] Treatment Planning
- [ ] Other: ___

**Architecture:**
- [ ] JEPA-style
- [ ] Diffusion-based
- [ ] Transformer
- [ ] VAE/Latent Dynamics
- [ ] Other: ___

### Brief Description

(One sentence describing the main contribution of this paper)
```

### Option 2: Submit a Pull Request

1. Fork this repository
2. Add the paper in the appropriate section of `README.md`
3. Use this format:

```markdown
**Paper Title.** [Month Year] [Conference/Journal, Year]<br>
*Author1, Author2, Author3, et al.*<br>
`LCapability` `Domain1` `Domain2` `Architecture`<br>
[[PDF](link)] [[Github](link)]

> One sentence describing the paper's contribution (optional)
```

4. Submit a PR describing your additions

---

## Capability Level Definitions

| Level | Definition | Criteria |
|-------|------------|----------|
| **L1** | Temporal Prediction | Model predicts future states without depending on specific actions |
| **L2** | Action-Conditioned | Predictions depend on input actions/conditions |
| **L3** | Counterfactual Rollouts | Can perform "what-if" analysis, compare different scenarios |
| **L4** | Planning & Control | Autonomous planning or real-time control |

---

## Inclusion Criteria

✅ **Should be included:**
- Explicitly models state transition dynamics p(s_{t+1} | s_t, a_t)
- Supports multi-step rollout or trajectory prediction
- Applied to medical/clinical scenarios
- Supports some form of planning or decision support

⚠️ **Edge cases (need discussion):**
- Pure medical video prediction (no action conditioning)
- Traditional disease progression statistical models
- Medical image temporal prediction without world model framework

❌ **Should not be included:**
- Static diagnosis/classification models
- Pure image generation models (no dynamics modeling)
- World models unrelated to medicine

---

## Code Style

- Use Markdown format
- Papers listed in reverse chronological order (newest first)
- Maintain format consistency
- Links must be valid and accessible

---

## Other Ways to Contribute

- Report broken links or incorrect information
- Improve documentation descriptions
- Translate content
- Suggest new categorization methods
- Add new dataset information

---

## Code of Conduct

- Be kind and respectful
- Welcome constructive discussions
- Respect original authors' work

---

Thank you for contributing!
