## 🤖 机器人视觉-语言-动作（VLA）模型评测榜（RoboChallenge）

> **平台链接**：[RoboChallenge 官网](https://robochallenge.cn/home)  
> *一个面向真实世界任务的开放式机器人策略评测基准，支持多机器人、长视野、复杂操作任务。*

| 排名 | 模型 / 团队 | 得分 | 成功率 | 简介 |
|------|-------------|------|--------|------|
| 🥇 1 | **Spirit-v1.5**<br>（千寻智能） | 66.09 | 50.33% | 基于高质量合成数据训练的高性能 VLA 模型，在 RoboChallenge Table30 榜单排名第一。 |
| 🥈 2 | **π₀.₅**<br>（Physical Intelligence） | 61.84 | 42.67% | 通过异构任务共训练实现强泛化能力，支持跨家庭、长时程家务操作。 |
| 🥉 3 | **wall-oss-v0.1**<br>（自变量） | 55.30 | 35.33% | 开源 VLA 模型，强调模块化与可复现性。 |

---

## 🔍 主流 VLA 模型概览

### 1. **Spirit-v1.5**（千寻智能）
- **论文/博客**：[Spirit-v1.5: Clean Data Is the Enemy of Great Robot Foundation Models](https://www.spirit-ai.com/en/blog/spirit-v1-5)
- **代码仓库**：[GitHub - Spirit-AI-Team/spirit-v1.5](https://github.com/Spirit-AI-Team/spirit-v1.5)
- **核心技术**：
  - 基于 Qwen-VL 视觉语言主干 + DiT 动作头
  - 针对 RoboChallenge 任务微调（如 `move_objects_into_box`）
  - 强调“少而精”的高质量训练数据策略
- **适用场景**：高精度桌面操作、指令跟随、竞赛级部署

---

### 2. **π₀.₅**（Physical Intelligence）
- **论文**：[π₀.₅: A Vision-Language-Action Model with Open-World Generalization](https://arxiv.org/abs/2504.16054)
- **代码仓库**：[GitHub - Physical-Intelligence/openpi](https://github.com/Physical-Intelligence/openpi)
- **核心技术**：
  - 在 π₀ 基础上引入**知识隔离**（Knowledge Insulation）与**多源共训练**
  - 融合机器人实采数据、Web 多模态数据、语义子任务监督
  - 支持 JAX / PyTorch 双后端，提供 DROID、ALOHA、LIBERO 等多个微调版本
- **突出能力**：在**未见过的真实家庭环境**中完成长达 15 分钟的复杂任务（如整理卧室、清洁厨房）

---

### 3. **wall-x**（自变量）
- **代码仓库**：[GitHub - X-Square-Robot/wall-x](https://github.com/X-Square-Robot/wall-x)
- **状态**：开源早期版本（`wall-oss-v0.1`），暂无论文公开
- **特点**：注重工程落地与模块解耦，适合二次开发与教育用途

---

## 🧊 前馈式 3D 感知：Depth Anything 3（DA3）

- **论文**：[Depth Anything 3: Recovering the Visual Space from Any Views](https://arxiv.org/abs/2511.10647)
- **代码仓库**：[GitHub - ByteDance-Seed/Depth-Anything-3](https://github.com/ByteDance-Seed/Depth-Anything-3)
- **研发单位**：字节跳动 Seed 团队
- **核心突破**：
  - **统一架构**：仅用一个普通 Transformer（如 DINO）即可处理单目、多视角、带/不带位姿的深度估计
  - **深度射线表示**（Depth-Ray）：替代传统多任务学习，简化训练目标
  - **SOTA 性能**：在相机位姿估计上超越 VGGT **44.3%**，几何精度提升 **25.1%**
- **模型系列**：
  - **Any-view 系列**（DA3-Giant/Large/Base/Small）：支持深度、位姿、3D Gaussian 同步输出
  - **Metric 系列**（DA3Metric-Large）：输出真实尺度（米制）深度
  - **Nested 系列**（如 DA3NESTED-GIANT-LARGE）：结合 Any-view 与 Metric 模型，实现高保真度新视角合成

> 💡 **应用场景**：SLAM、NeRF 初始化、机器人导航、AR/VR 重建、视频 3D 化

---

