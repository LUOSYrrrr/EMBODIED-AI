# 📚 Future Reading — 待读资源库（分阶段）

> **使用原则**：
> 1. **主线第一**，任何资源都不能挤掉 `master_plan.md` 里的任务
> 2. **按阶段看**，不要提前跳——疲劳状态下看超前资源等于浪费
> 3. **"收藏 ≠ 学会"**，每周限定"新增收藏不超过 2 个"
> 4. **遇到好资源就加到对应 Week**，不要放"综合区"让它沉底

**最后更新**：2026-04-19（Day 2 结束）

---

## 🎯 阶段规划速查表

| Week | 主题 | 推荐资源数 |
|---|---|---|
| Week 1 | Isaac Lab 入门 | 2 |
| Week 2 | SO-101 URDF + LeRobot + Locomotion Ch1-2 | 3 |
| Week 3 | ROS 2 基础 + Locomotion Ch3-4 | 2 |
| Week 4 | π₀ 真机（**零新资源**） | 0 |
| Week 5 | Isaac Lab 仿真 + Locomotion Ch5-7 | 2 |
| Week 6 | Sim-to-Real + **Evo-RL 加分** | 1 |
| Week 7-8 | 投递 + 面试（**零新资源**） | 0 |

---

## 📍 Week 1（本周）：Isaac Lab 入门

### ⭐ 核心任务用的资源

#### 1. Isaac Lab 中文教程（B 站系列）
- **链接**：https://www.bilibili.com/video/BV1pLYAz1EH3/
- **UP 主**：IsaacLab（非官方但持续更新）
- **看哪几集**：
  - 0.2 IsaacLab 概述（5-10 分钟）
  - 1.1 IsaacLab 代码框架（⭐ Day 3 核心）
  - 1.2.1 + 1.2.2 Environment（Day 5 核心）
- **预计时长**：40-60 分钟
- **配套**：对照官方中文文档一起读

#### 2. Isaac Lab 官方中文文档
- **链接**：https://docs.robotsfan.com/isaaclab/
- **必读页面**：
  - [快速入门指南](https://docs.robotsfan.com/isaaclab/source/setup/quickstart.html)
  - [Tutorial 00 - 设置仿真](https://docs.robotsfan.com/isaaclab/source/tutorials/00_sim/create_empty.html)
  - [核心概念](https://docs.robotsfan.com/isaaclab/source/overview/core-concepts/index.html)
- **用法**：Day 3-5 的"查手册"，不要一次从头读到尾

### 🦿 Locomotion 辅线（本周穿插）

#### 3. 四足机器人强化学习综述
- **先看哪个**：知乎"RL 做足式机器人运控的经典必读文章（带私货）"
  - 链接：https://zhuanlan.zhihu.com/p/29806809248
  - 作用：扫读，记下 3-4 个论文名字
  - ⚠️ 不用读懂，只是建立索引

---

## 📍 Week 2（04-27 ~ 05-03）：SO-101 URDF + LeRobot 基础

### ⭐ 核心任务用的资源

#### 1. LeRobot 官方文档
- **链接**：https://huggingface.co/docs/lerobot
- **重点**：Dataset API、Policy 抽象、ACT / Diffusion Policy / π₀ 实现
- **配套 GitHub**：https://github.com/huggingface/lerobot

#### 2. Isaac Lab URDF 导入指南
- **链接**：https://isaac-sim.github.io/IsaacLab/main/source/how-to/import_new_asset.html
- **配套中文**：https://docs.robotsfan.com/isaaclab/ → "如何导入新资产"

#### 3. SO-101 硬件文档（HuggingFace）
- **链接**：https://github.com/huggingface/lerobot/tree/main/lerobot/common/robot_devices
- **用处**：URDF 文件、舵机参数、接线说明

### 🦿 Locomotion 辅线

#### 4. 强化学习+机器人运动控制入门（B 站系列）⭐
- **UP 主**：二营长向强化学习开炮
- **合集播放**：8.6 万
- **合集总集数**：13 集
- **看哪几集（Week 2）**：
  - Chapter 1：legged_gym + rsl_rl 框架介绍（16 分钟）
  - Chapter 2：Isaac 相关（35 分钟）
- **Week 2 总时长**：51 分钟

#### 5. "Learning to Walk in Minutes" 论文精读
- **论文链接**：https://arxiv.org/abs/2109.11978
- **项目主页**：https://leggedrobotics.github.io/legged_gym/
- **精读范围（Week 2）**：Introduction + Method
- **SCQA 笔记模板**：
  - Situation：为什么传统 RL locomotion 训练慢？
  - Complication：单机训练几天，集群贵
  - Question：能否在单 GPU 几分钟训完？
  - Answer：Isaac Gym + 4096 并行 + PPO + Terrain Curriculum

---

## 📍 Week 3（05-04 ~ 05-10）：ROS 2 基础 + SO-101 通信

### ⭐ 核心任务用的资源

#### 1. ROS 2 Humble 官方文档
- **链接**：https://docs.ros.org/en/humble/Tutorials.html
- **必做**：Beginner: CLI tools 全部教程
- **必做**：Beginner: Client libraries → Writing a simple publisher and subscriber (Python)

#### 2. 古月居 / 鱼香 ROS（中文）
- **鱼香 ROS 一键安装**：`wget http://fishros.com/install -O fishros && . fishros`
- **古月居 ROS 2 教程**：https://www.guyuehome.com/

#### 3. The Construct（免费在线 ROS 课程）
- **链接**：https://www.theconstruct.ai/
- **用处**：不用配环境，浏览器里跑 ROS 2

### 🦿 Locomotion 辅线

#### 4. 强化学习+机器人运动控制入门（B 站系列）续
- **Chapter 3**：Isaac 相关（45 分钟）
- **Chapter 4**：Isaac 相关（33 分钟）
- **Week 3 总时长**：78 分钟

#### 5. "Learning to Walk in Minutes" 论文精读（后半）
- Experiments + Domain Randomization 部分
- 练习：用自己的话给"完全不懂 locomotion 的朋友"讲懂这篇（500 字）

---

## 📍 Week 4（05-11 ~ 05-17）：π₀ 真机冲刺 🚀

### ⚠️ 本周零新资源 —— 集中精力打通主线里程碑 M4

**只允许用**：

#### 1. π₀ 原始论文
- **链接**：https://www.physicalintelligence.company/blog/pi0
- **你已经读过，只需要回顾**

#### 2. LeRobot π₀ 集成
- **代码位置**：https://github.com/huggingface/lerobot/tree/main/lerobot/common/policies/pi0

#### 3. HuggingFace π₀ 权重
- **链接**：https://huggingface.co/lerobot

**绝对不要**：
- ❌ 看新的 VLA 论文
- ❌ 研究 Evo-1 / Evo-RL
- ❌ 刷 Locomotion 视频

**只有一个目标**：SO-101 真机上跑出 π₀ demo 视频

---

## 📍 Week 5（05-18 ~ 05-24）：Isaac Lab 仿真训练 + Locomotion 实战

### ⭐ 核心任务用的资源

#### 1. Isaac Lab Manager-based Env 深度教程
- **官方**：https://isaac-sim.github.io/IsaacLab/main/source/tutorials/03_envs/index.html
- **博客**：https://blog.csdn.net/weixin_46300916/article/details/141256600（NVIDIA Isaac Lab 入门教程）

#### 2. CSDN「IsaacLab 最新 2025 教程」系列（Clam_dw）
- **链接**：https://blog.csdn.net/Clam_dw/article/details/145502703
- **配套 B 站**：https://space.bilibili.com/xxx
- **用处**：自定义 Scene 配置，对应 Day 29-30 任务

### 🦿 Locomotion 实战

#### 3. 强化学习+机器人运动控制入门（B 站系列）完结
- **Chapter 5**：框架（56 分钟）
- **Chapter 6**：地形（19 分钟）
- **Chapter 7**：地形（46 分钟）
- **Week 5 总时长**：121 分钟
- **配合**：在 Isaac Lab 跑 G1 / Anymal 训练，**边跑边看**

#### 4. Legged Gym 代码详解（B 站）
- **时长**：43:44
- **播放量**：2.7 万，收藏 2215
- **看这个的时机**：跑过至少一次 G1 训练之后
- **用处**：理解 legged_gym 代码组织，对应 Week 5 locomotion 实战

---

## 📍 Week 6（05-25 ~ 05-31）：Sim-to-Real + 简历打磨

### 🔥 加分项：Evo-RL（可选但强烈推荐）

#### 1. MINT-SJTU / Evo-RL ⭐⭐⭐
- **GitHub**：https://github.com/MINT-SJTU/Evo-RL
- **机构**：上海交大机器智能与交互实验室
- **定位**：SO-101 上的真实世界 offline RL baseline
- **基础**：LeRobot
- **时间线**：
  - 2026-02-26：首个 SO101 baseline
  - 2026-03-07：加入 AgileX PiPER 支持
- **为什么加分**：
  - ✅ 原生支持 SO-101
  - ✅ 基于 LeRobot（你 Week 4 已打通）
  - ✅ Offline RL 是 VLA 领域差异化路线
  - ✅ 学术前沿（简历能写"跟踪 2026 最新工作"）
- **使用方法**：
  - Week 6 一天内跑通 baseline
  - 和 Week 4 的 π₀ 做对比实验
  - 简历写："在 SO-101 上同时评估 IL（π₀）和 Offline RL（Evo-RL）"

#### 2. Isaac Sim ROS 2 Bridge 文档
- **链接**：https://docs.omniverse.nvidia.com/isaacsim/latest/ros2_tutorials/index.html
- **用处**：Week 6 Sim-to-Real pipeline

---

## 📍 Week 7-8：投递 + 面试

### ⚠️ 本两周零新学习资源 —— 全部精力投入简历和面试准备

**只允许用**：

#### 1. π₀ 架构深度回顾
- 你 Week 4 的笔记
- HuggingFace Transformers 文档（如果被问 VLM）

#### 2. LeetCode Hot 100
- https://leetcode.cn/problem-list/2cktkvj/

#### 3. 面试八股
- Transformer、Attention
- PPO、Flow Matching、Diffusion Policy（一句话原理）

---

## 🔖 非时间线的参考资源（查手册用）

### 权威参考
- **Isaac Lab 官方文档（英文）**：https://isaac-sim.github.io/IsaacLab/
- **Isaac Sim 官方文档**：https://docs.omniverse.nvidia.com/isaacsim/
- **ROS 2 Humble 文档**：https://docs.ros.org/en/humble/
- **LeRobot Hub**：https://huggingface.co/lerobot

### Awesome List（找资源用）
- **Awesome Humanoid Robot Learning**：https://github.com/YanjieZe/awesome-humanoid-robot-learning
- **Awesome Legged Locomotion Learning**：https://github.com/gaiyi7788/awesome-legged-locomotion-learning
- **Awesome Humanoid Learning**：https://github.com/jonyzhang2023/awesome-humanoid-learning
- **VLA SOTA 排行榜**：https://github.com/MINT-SJTU/Evo-SOTA.io

### 经典参考（不按 Week 读，需要时查）
- **OpenAI Spinning Up**：https://spinningup.openai.com/
  - 定位：RL 教学项目，入职后再完整读
  - Week 4+ 如果 PPO 被问到细节，查 PPO 那一章（1-2 小时）
- **Sutton RL Book**：《Reinforcement Learning: An Introduction》
  - 经典教材，时间充裕时啃

---

## 🗃️ Archive：已淘汰 / 不推荐的资源

> 保留在这里避免重复搜索，看到自动跳过。

- ❌ **ROS 1 相关教程** —— 2025 年 5 月 EOL，只学 ROS 2
- ❌ **Isaac Gym（老版本）** —— 已被 Isaac Lab 取代
- ❌ **Isaac Sim 5.1 / Isaac Lab 3.0 Beta** —— 现阶段稳定性不足
- ❌ **小红书技术内容** —— 深度不够，去知乎 / B 站 / GitHub

---

## 📊 我的"资源饱和度"自查表

**每次想加新资源时，检查一下**：

| 状态 | 说明 | 动作 |
|---|---|---|
| 😎 当前 Week 资源全部看完 | 学得很快 | ✅ 可以加 1 个下 Week 的资源 |
| 🧐 当前 Week 资源看了一半 | 正常速度 | ⚠️ 慎加，先完成主线 |
| 😵 当前 Week 资源还没开始 | 还在搜索 | ❌ 禁止加，立刻开始学 |
| 🥴 凌晨 1 点还在找资源 | **疲劳循环** | ❌ **立刻睡觉** |

---

## 🚨 防止"收藏党"的 3 条铁律

1. **收藏前问自己**：这个资源对应 `master_plan.md` 的哪个 Week？说不出来就不收藏
2. **每周只允许收藏 2 个新资源**，超过就删掉旧的
3. **一旦发现自己在"比较多个资源选哪个好"，立刻停止搜索，选第一个**

---

**最后一句**：

> **最好的资源不是"别人都说最好的"，而是"你真的读完的"。**
>
> **π₀ 一篇论文读 3 遍，胜过收藏 30 篇 VLA 论文都不读。**

---

**更新日志**
- 2026-04-19：初始版本，整合 Day 2 晚上所有讨论过的资源
