# Contributing to Awesome Medical World Models

感谢你对这个项目的兴趣！我们欢迎任何形式的贡献。

Thank you for your interest in contributing! We welcome all forms of contributions.

---

## 如何添加新论文 (How to Add a Paper)

### 方式一：提交 Issue

1. 点击 [New Issue](../../issues/new)
2. 使用以下模板填写信息：

```markdown
### 论文信息 (Paper Information)

**标题 (Title):**
**作者 (Authors):**
**年份 (Year):**
**发表venue (Venue):**
**PDF链接 (PDF Link):**
**Github链接 (Github Link):** （如有）

### 分类信息 (Classification)

**能力等级 (Capability Level):** L1 / L2 / L3 / L4
**应用领域 (Application Domain):**
- [ ] Medical Imaging (Radiology/MRI/Ultrasound)
- [ ] Surgical Vision & Robotics
- [ ] Disease Progression (EHR)
- [ ] Treatment Planning
- [ ] Other: ___

**技术架构 (Architecture):**
- [ ] JEPA-style
- [ ] Diffusion-based
- [ ] Transformer
- [ ] VAE/Latent Dynamics
- [ ] Other: ___

### 简要描述 (Brief Description)

（一句话描述这篇论文的主要贡献）
```

### 方式二：提交 Pull Request

1. Fork 这个仓库
2. 在 `README.md` 的相应位置添加论文
3. 使用以下格式：

```markdown
**论文标题.** [月份 年份] [会议/期刊, 年份]<br>
*作者1, 作者2, 作者3, et al.*<br>
`L能力等级` `领域1` `领域2` `架构`<br>
[[PDF](链接)] [[Github](链接)]

> 一句话描述论文贡献（可选）
```

4. 提交 PR，描述你添加的内容

---

## 能力等级定义 (Capability Level Definitions)

| Level | 定义 | 判断标准 |
|-------|------|----------|
| **L1** | Temporal Prediction | 模型能预测未来状态，但不依赖于特定动作 |
| **L2** | Action-Conditioned | 预测结果依赖于输入的动作/条件 |
| **L3** | Counterfactual Rollouts | 能进行"what-if"分析，比较不同方案 |
| **L4** | Planning & Control | 能自主规划或实时控制 |

---

## 论文收录标准 (Inclusion Criteria)

✅ **应该收录：**
- 明确建模状态转移动态 p(s_{t+1} | s_t, a_t)
- 支持多步rollout或轨迹预测
- 应用于医学/临床场景
- 支持某种形式的规划或决策支持

⚠️ **边界情况（需讨论）：**
- 纯粹的医学视频预测（无动作条件）
- 传统的疾病进展统计模型
- 医学图像的时序预测但无世界模型框架

❌ **不应收录：**
- 静态诊断/分类模型
- 纯粹的图像生成模型（无动态建模）
- 与医学无关的世界模型

---

## 代码规范 (Code Style)

- 使用 Markdown 格式
- 论文按时间倒序排列（最新的在前）
- 保持格式一致性
- 链接需要有效可访问

---

## 其他贡献方式 (Other Ways to Contribute)

- 🐛 报告错误链接或信息
- 📝 改进文档描述
- 🌐 翻译内容
- 💡 建议新的分类方式
- 📊 添加新的数据集信息

---

## 行为准则 (Code of Conduct)

- 保持友善和尊重
- 欢迎建设性的讨论
- 尊重原作者的工作

---

感谢你的贡献！🙏

Thank you for contributing! 🙏
