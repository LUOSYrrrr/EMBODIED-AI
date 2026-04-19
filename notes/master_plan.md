# 🤖 Embodied AI Internship Prep — Master Plan v2.1

> **目标**：2026 年 6 月具身智能算法实习入职
> **开始日期**：2026-04-18（周六）
> **投递截止**：2026-06-07（Week 7 周日）
> **主攻方向**：VLA / Manipulation（π₀ + Isaac Lab + SO-101 + LeRobot）
> **辅攻方向**：ROS 2 基础 + Locomotion 速通 + Evo-RL 加分
>
> **最后更新**：2026-04-19（Day 2 结束）
>
> **变更日志**：
> - v2.1（2026-04-19）：同步 Day 2 实际进展、加入 Evo-RL 加分项、精确 Locomotion 视频章节
> - v2.0（2026-04-18）：首版，加入 Locomotion 辅线

---

## 📋 目录

1. [硬件与环境清单](#硬件与环境清单)
2. [目标公司与投递优先级](#目标公司与投递优先级)
3. [核心里程碑](#核心里程碑)
4. [Week 1 Isaac Lab 环境打通](#week-1-isaac-lab-环境打通04-18--04-26)
5. [Week 2 SO-101 URDF + LeRobot](#week-2-so-101-urdf-导入--lerobot-基础04-27--05-03)
6. [Week 3 ROS 2 + SO-101 真机](#week-3-ros-2-基础--so-101-真机通信05-04--05-10)
7. [Week 4 π₀ 真机冲刺](#week-4-lerobot--π-真机跑通05-11--05-17)
8. [Week 5 Isaac Lab 仿真 + Locomotion](#week-5-isaac-lab-仿真训练--locomotion-实战05-18--05-24)
9. [Week 6 Sim-to-Real + Evo-RL](#week-6-sim-to-real--evo-rl--简历打磨05-25--05-31)
10. [Week 7 投递 + 内推](#week-7-投递--内推06-01--06-07)
11. [Week 8 面试冲刺](#week-8-面试冲刺06-08--06-14)
12. [Locomotion 辅线汇总](#-locomotion-辅线汇总)
13. [Evo-RL 加分项规划](#-evo-rl-加分项规划)
14. [简历素材卡](#-简历素材卡持续更新)
15. [常见坑速查](#-常见坑速查)
16. [进度追踪](#-进度追踪)

---

## 硬件与环境清单

| 项目 | 配置 | 状态 |
|---|---|---|
| OS | Ubuntu 22.04.5 LTS | ✅ |
| CPU | Intel i7-14700F（20 核 28 线程） | ✅ |
| GPU | RTX 4070 Ti Super (16GB) | ✅ |
| RAM | 31GB | ✅ |
| 磁盘 | 916GB（可用 762GB） | ✅ |
| 驱动 | NVIDIA 580.126.09 / CUDA 13.0（驱动层） | ✅ |
| conda | Anaconda 24.9.2 | ✅ |
| Python | 3.10（conda 环境 `isaaclab`） | ✅ |
| PyTorch | 2.5.1 + cu124 | ✅ |
| Isaac Sim | 4.5.0（pip 方式安装） | ✅ |
| Isaac Lab | v2.3.2（2.x 线最新稳定 tag，避开 main 的 v3.0.0-beta / Newton） | ✅ |
| 机器人 | SO-101（已组装，未跑过代码） | ⏳ Week 3 启用 |
| 远程算力 | Spartan HPC（A100，punim2341） | ✅ Week 4+ 备用 |

### 工作目录结构

```
~/embodied-ai/
├── isaaclab/           # Isaac Lab 源码 + 自定义任务
│   └── IsaacLab/       # Git clone 的源码
├── lerobot/            # LeRobot 源码 + 数据集 + 模型权重
├── ros2_ws/            # ROS 2 workspace（Week 3 创建）
├── evo-rl/             # Evo-RL 代码（Week 6 创建，可选）
├── notes/              # 学习笔记 + 简历素材（同步到 GitHub）
│   ├── master_plan.md        # 本文件
│   ├── progress.md           # 每日进度
│   ├── resume_assets.md      # 简历素材卡
│   ├── future_reading.md     # 待读资源库
│   ├── locomotion.md         # Locomotion 辅线笔记
│   └── week{N}/              # 每周详细笔记
└── demos/              # 训练视频、截图（简历素材）
```

### 关键安装命令（已验证，可复用）

```bash
# Anaconda 环境
conda create -n isaaclab python=3.10 -y
conda activate isaaclab

# PyTorch（注意用 cu124，对齐 Isaac Sim 4.5）
pip install torch==2.5.1 torchvision==0.20.1 --index-url https://download.pytorch.org/whl/cu124

# Isaac Sim 4.5（pip 方式，10GB+）
pip install 'isaacsim[all,extscache]==4.5.0' --extra-index-url https://pypi.nvidia.com

# Isaac Lab
cd ~/embodied-ai/isaaclab
git clone https://github.com/isaac-sim/IsaacLab.git
cd IsaacLab
./isaaclab.sh --install

# 验证
./isaaclab.sh -p scripts/tutorials/00_sim/create_empty.py
```

---

## 目标公司与投递优先级

### 第一梯队（最对口，必投）

| 公司 | 方向 | 联系方式 | 备注 |
|---|---|---|---|
| **银河通用（Galbot）** | 具身 VLA 大模型 / 仿真开发 | hr@galbot.com | 北京/深圳/苏州；6-8k/天；π₀ 技术栈最契合 |
| **上海 AI Lab 具身中心** | VLA / Sim-to-Real | 官网投递 | 研究氛围最好，要求 Isaac Sim + ROS |
| **字节 Seed / Robotics** | VLA / 多模态 | 官网 | 门槛高，需要论文/强项目 |
| **智元机器人** | 启元大模型 / 本体控制 | 官网 | 上海，2026.04 刚发布 4 款新品 |

### 第二梯队（相关方向）

| 公司 | 方向 | 备注 |
|---|---|---|
| 千寻智能 | Spirit v1.5 基础模型 | 2026.01 榜单第一 |
| 宇树科技 | 人形 + 四足 locomotion | 需要 locomotion 背景 |
| 松延动力 | 消费级人形 | 走低价路线 |
| 魔法原子 | 四足 + 人形 | 春晚出圈 |
| 上海期智研究院 | 人形平衡/运动 | 要求 Isaac Lab + sim2real |

### 第三梯队（车企具身）

| 公司 | 备注 |
|---|---|
| 零跑 | VLM/VLA 算法工程师 |
| 理想 | 机器人事业部 |
| 小鹏 | Iron 人形机器人 |

---

## 核心里程碑

| 里程碑 | 截止日期 | 验收标准 | 状态 |
|---|---|---|---|
| 🎯 **M0**：环境打通 | Week 1 Day 2 | 跑通 Isaac Lab `create_empty.py` | ✅ **2026-04-19 达成** |
| 🎯 M1：Isaac Lab 跑通 Franka RL | Week 1 Day 7 | Franka Reach 训练视频 + TensorBoard 曲线 | ⏳ |
| 🎯 M2：SO-101 在 Isaac Lab 仿真里动起来 | Week 2 Day 14 | SO-101 仿真关节运动 demo | ⏳ |
| 🎯 M3：ROS 2 控制 SO-101 真机闭环 | Week 3 Day 20 | ROS 2 节点读关节 + 发目标角 + 真机响应 | ⏳ |
| 🎯 M4：π₀ / ACT 在 SO-101 真机 demo | Week 4 Day 28 | 真机抓取任务视频（**必杀技！**） | ⏳ |
| 🎯 M5：Isaac Lab SO-101 仿真训练 | Week 5 Day 33 | 仿真训练的 policy 完成任务 | ⏳ |
| 🎯 M6：Sim-to-Real 闭环 demo | Week 6 Day 38 | 仿真 → 真机 pipeline 视频 | ⏳ |
| 🎯 M6.5：Evo-RL 对比实验（可选加分） | Week 6 Day 40 | π₀ vs Evo-RL 对比表 | ⏳ |
| 🎯 M7：投递 20+ 家 | Week 7 Day 47 | 简历 + GitHub + 投递记录 | ⏳ |
| 🎯 M8：拿到至少 1 个面试 | Week 8 | 面试笔记 | ⏳ |

---

## Week 1：Isaac Lab 环境打通（04-18 ~ 04-26）

**周目标**：跑通 Franka Reach/Lift RL 训练，理解 Manager-based 框架

### Day 1（04-18 周六）✅ 已完成

- [x] `nvidia-smi` 检查驱动（580.126.09 / CUDA 13.0）
- [x] 磁盘空间（762GB 可用）
- [x] Anaconda 安装 + conda init + auto_activate_base 关闭
- [x] 创建 `isaaclab` conda 环境（Python 3.10）
- [x] 建立 `~/embodied-ai/` 工作目录

**坑记录**：无（硬件配置完美）

### Day 2（04-19 周日）✅ 已完成

#### 实际完成的任务

- [x] PyTorch 2.5.1 + cu124 安装并验证 `torch.cuda.is_available()`
- [x] Isaac Sim 4.5.0 安装（pip 方式，~10GB）
- [x] Isaac Lab 克隆 + `./isaaclab.sh --install`
- [x] 跑通 tutorial（GUI 出现 3D 场景）

#### 实际踩坑记录

| 坑 | 症状 | 解决方案 |
|---|---|---|
| CUDA 999 错误 | Isaac Sim 启动时 `cudaErrorUnknown`，段错误 | `sudo reboot`（驱动僵尸状态） |
| Isaac Sim 首次启动卡 | GUI 白屏 10-20 分钟 | **等**，正在编译 shader cache |
| GNOME 误报"无响应" | 对话框弹出 | 点"等待"，实际没崩 |
| ROS 2 Bridge 报错 | `ROS_DISTRO env var not found` | **忽略**，Week 3 装 ROS 2 后自然消失 |
| Anaconda `conda: command not found` | 安装最后选了 no | `eval "$(~/anaconda3/bin/conda shell.bash hook)" && conda init` |

#### 关键认知

- Isaac Sim GUI 的"无响应"**90% 是 GNOME 误报**，实际程序在工作
- Isaac Sim 第一次启动 = **信仰考验**，shader 编译 10-20 分钟必须的
- 以后 99% 时间用 `./isaaclab.sh -p xxx.py` 命令行，**不需要开 `isaacsim` GUI**

### Day 3（04-20 周一）：跑通 4 个官方教程 ⏳

**时间预算**：3-4 小时

#### 上午（1-2 小时）：看 B 站中文教程

- [ ] B 站「IsaacLab 中文教程 1.1 代码框架」（40 分钟）
  - 链接：https://www.bilibili.com/video/BV1pLYAz1EH3/
- [ ] 对照 [官方中文文档 - 快速入门](https://docs.robotsfan.com/isaaclab/source/setup/quickstart.html)（20 分钟）

#### 下午（2 小时）：动手 + 产出

```bash
cd ~/embodied-ai/isaaclab/IsaacLab

# 1. 创建空场景
./isaaclab.sh -p scripts/tutorials/00_sim/create_empty.py

# 2. 生成刚体
./isaaclab.sh -p scripts/tutorials/00_sim/spawn_prims.py

# 3. 加载机器人资产
./isaaclab.sh -p scripts/tutorials/01_assets/run_articulation.py

# 4. 交互式场景
./isaaclab.sh -p scripts/tutorials/02_scene/create_scene.py
```

- [ ] **在 `notes/week1/day3.md` 回答 4 个概念问题**（不查答案）：
  1. Isaac Lab 里的 `sim` / `stage` / `scene` 各自是什么？
  2. `Articulation` 和普通 rigid body 的区别？
  3. 为什么代码里总用 `sim.step()` 循环，这个循环和 RL 的 episode 什么关系？
  4. USD 文件是什么，和 URDF 什么关系？

### Day 4（04-21 周二）：🎯 M1 Franka Reach RL 训练

**时间预算**：3-4 小时

```bash
# 训练（15-30 分钟）
./isaaclab.sh -p scripts/reinforcement_learning/rsl_rl/train.py \
    --task Isaac-Reach-Franka-v0 \
    --num_envs 2048 \
    --headless

# 可视化（5 分钟）
./isaaclab.sh -p scripts/reinforcement_learning/rsl_rl/play.py \
    --task Isaac-Reach-Franka-v0 \
    --num_envs 32

# TensorBoard
cd logs/rsl_rl/reach_franka
tensorboard --logdir .
```

- [ ] **录制 10 秒视频** → `~/embodied-ai/demos/franka_reach.mp4`
- [ ] **TensorBoard 截图**：`Train/mean_reward` + `Train/mean_episode_length`

### Day 5（04-22 周三）：理解 Manager-based 架构

- [ ] 通读 `source/isaaclab_tasks/isaaclab_tasks/manager_based/manipulation/reach/reach_env_cfg.py`
- [ ] 理解 5 个 Manager：Observations / Actions / Rewards / Terminations / Events
- [ ] 修改一个 reward 权重，重新训练，对比曲线
- [ ] 在 `notes/week1/day5.md` 画数据流图

### Day 6（04-23 周四）：Franka Lift + URDF 基础

- [ ] 跑 Franka Lift 训练
- [ ] 阅读 LeRobot SO-101 URDF
- [ ] 了解 Isaac Lab URDF 导入工具

### Day 7（04-24 周日）：Week 1 复盘

- [ ] Week 1 review 写进 `notes/week1/review.md`
- [ ] GitHub 仓库 `embodied-ai-journey` 初始化
- [ ] 更新 `resume_assets.md`

### 🦿 Locomotion 穿插（本周 2 小时，周末做）

- [ ] **任务 L1**：知乎扫读"RL 做足式机器人运控的经典必读文章（带私货）"
  - 链接：https://zhuanlan.zhihu.com/p/29806809248
  - **不需要读懂**，只记下 3-4 个论文名字
- [ ] **任务 L2**：在 `notes/locomotion.md` 写下 **10 个术语一句话解释**（见文末 Locomotion 章节）

### Week 1 验收 ✅

- [ ] M1 达成：Franka Reach 训练视频 + TensorBoard 曲线
- [ ] Day 3 的 4 个概念能答出来
- [ ] Locomotion 10 术语笔记完成

---

## Week 2：SO-101 URDF 导入 + LeRobot 基础（04-27 ~ 05-03）

**周目标**：把 SO-101 导入 Isaac Lab；LeRobot 跑通 ACT baseline

### Day 8-9（04-27 ~ 04-28）：获取并转换 SO-101 URDF

- [ ] 从 LeRobot 官方仓库找到 SO-101 URDF
- [ ] 检查 URDF 完整性（mesh、joint limits）

### Day 10（04-29）：URDF → USD 转换

```bash
./isaaclab.sh -p scripts/tools/convert_urdf.py \
    --input /path/to/so101.urdf \
    --output /path/to/so101.usd
```

### Day 11（04-30）：🎯 M2 SO-101 关节 PD 控制

- [ ] 写最小 Articulation 配置
- [ ] PD 控制每个关节运动
- [ ] **录视频**：`demos/so101_sim_joint_test.mp4`

### Day 12（05-01）：LeRobot 安装 + ACT demo

```bash
cd ~/embodied-ai/lerobot
git clone https://github.com/huggingface/lerobot.git
conda create -n lerobot python=3.10 -y
conda activate lerobot
pip install -e .
```

- [ ] 跑通官方 ACT demo（pusht 数据集）

### Day 13（05-02）：LeRobot Policy 架构

- [ ] 阅读 LeRobot 的 Policy 抽象代码
- [ ] 在 `notes/week2/lerobot_arch.md` 写 500 字笔记

### Day 14（05-03）：Week 2 复盘

### 🦿 Locomotion 穿插（本周 2-3 小时）

- [ ] **任务 L3**：看 B 站「强化学习+机器人运动控制入门」系列
  - UP 主：二营长向强化学习开炮
  - **Chapter 1**：框架介绍（16 分钟）
  - **Chapter 2**：Isaac 相关（35 分钟）
- [ ] 精读 "Learning to Walk in Minutes" 前半（Introduction + Method）
  - 链接：https://arxiv.org/abs/2109.11978
  - **SCQA 笔记**写进 `notes/locomotion.md`

---

## Week 3：ROS 2 基础 + SO-101 真机通信（05-04 ~ 05-10）

**周目标**：ROS 2 入门 + 🎯 M3 实现"ROS 2 节点控制 SO-101 真机"闭环

### Day 15（05-04）：ROS 2 Humble 安装

```bash
# 鱼香 ROS 一键脚本（推荐，国内网络友好）
wget http://fishros.com/install -O fishros && . fishros

# 或官方脚本
# （详见 v2.0 计划）
```

**验证**：
```bash
# 终端 1
ros2 run demo_nodes_cpp talker
# 终端 2
ros2 run demo_nodes_py listener
```

### Day 16（05-05）：turtlesim + CLI 工具

- [ ] 完成 ROS 2 Beginner: CLI tools 全部
- [ ] 熟练使用 `ros2 node/topic/service/action` 命令

### Day 17（05-06）：Python 节点

- [ ] Publisher/Subscriber（订阅 USB 摄像头，发布处理后图像）
- [ ] `cv_bridge` 使用
- [ ] 建立 `~/embodied-ai/ros2_ws/`

### Day 18（05-07）：TF2 + SO-101 URDF

- [ ] 学 TF2 基础
- [ ] `robot_state_publisher` 发布 SO-101 TF 树
- [ ] RViz 可视化 SO-101

### Day 19（05-08）：SO-101 真机驱动节点

- [ ] feetech-sdk / LeRobot API 读关节
- [ ] 封装成 ROS 2 节点，发布 `/joint_states`

### Day 20（05-09）：🎯 M3 真机闭环

- [ ] 订阅 `/target_joint_positions` 的节点，发送舵机
- [ ] **完整闭环**：手动发目标角 → SO-101 响应
- [ ] **录视频**：`demos/ros2_so101_loop.mp4`

### Day 21（05-10）：Week 3 复盘

### 🦿 Locomotion 穿插（本周 2 小时）

- [ ] **任务 L4**：B 站系列 Chapter 3（Isaac 相关，45 分钟）
- [ ] 精读 "Learning to Walk in Minutes" 后半（Experiments）
- [ ] 练习：给"不懂 locomotion 的朋友"讲懂这篇（500 字写在 `notes/locomotion.md`）

---

## Week 4：LeRobot + π₀ 真机跑通（05-11 ~ 05-17）🚀

**周目标**：🎯 M4 SO-101 真机 π₀ 抓取 demo（**简历核心素材！**）

### ⚠️ 本周严格规则

- ❌ **零新资源**（不看新视频、不研究新论文、不学 Evo-RL）
- ❌ **暂停 Locomotion**（主线冲刺期）
- ✅ **唯一目标**：真机 demo 视频

### Day 22-23（05-11 ~ 05-12）：真机数据采集

- [ ] LeRobot `record` 脚本采集
- [ ] 任务：简单抓取（如抓积木）
- [ ] **50-100 条轨迹**
- [ ] 可选 push 到 HuggingFace Hub

### Day 24（05-13）：ACT baseline 训练

```bash
cd ~/embodied-ai/lerobot/lerobot
python lerobot/scripts/train.py \
    policy=act \
    env=so101 \
    dataset_repo_id=你的用户名/so101_grasp
```

### Day 25（05-14）：ACT 真机 play

- [ ] 真机运行训好的 ACT
- [ ] **录视频**：`demos/act_so101_grasp.mp4`
- [ ] 分析失败 case

### Day 26（05-15）：π₀ 加载 + 微调

- [ ] HuggingFace 下载 π₀ 权重
- [ ] 本地 / Spartan 微调（3-6 小时）

### Day 27（05-16）：🎯 M4 π₀ 真机 demo

- [ ] 真机跑 π₀
- [ ] 对比 ACT vs π₀
- [ ] **录视频**：`demos/pi0_so101_grasp.mp4`

### Day 28（05-17）：demo 合集

- [ ] 剪辑 2-3 分钟 **demo 合集视频**（简历最值钱素材）
- [ ] 更新 `resume_assets.md`

---

## Week 5：Isaac Lab 仿真训练 + Locomotion 实战（05-18 ~ 05-24）

**周目标**：在 Isaac Lab 复现 SO-101 操作任务 + 🦿 跑通 G1 locomotion

### Day 29（05-18）：SO-101 Reach 任务

- [ ] 自定义 `ManagerBasedEnv`
- [ ] 定义 Observation / Action / Reward

### Day 30（05-19）：SO-101 Lift / Pick-Place

### Day 31（05-20）：仿真训练 Diffusion Policy / ACT

### Day 32（05-21）：超参调整

### Day 33（05-22）：域随机化

### Day 34-35（05-23 ~ 05-24）：🦿 Locomotion 实战

#### 任务 L5：跑通 Isaac Lab G1 locomotion

```bash
# 人形 G1 走路（Unitree 自家机器人！）
./isaaclab.sh -p scripts/reinforcement_learning/rsl_rl/train.py \
    --task Isaac-Velocity-Rough-G1-v0 \
    --num_envs 4096 --headless

./isaaclab.sh -p scripts/reinforcement_learning/rsl_rl/play.py \
    --task Isaac-Velocity-Rough-G1-v0 --num_envs 16
```

#### 任务 L6-L7：深度学习 + 录视频

- [ ] B 站系列 **Chapter 4**（33 分钟）+ **Chapter 5**（56 分钟）— 边跑边看，印证代码
- [ ] **录视频**：`demos/g1_locomotion.mp4`
- [ ] 简历加一行：
  > 基于 Isaac Lab 在 Unitree G1 人形机器人上训练 rough-terrain locomotion policy（4096 并行环境 + PPO），复现 Rudin et al. CoRL 2022 工作流

---

## Week 6：Sim-to-Real + Evo-RL + 简历打磨（05-25 ~ 05-31）

**周目标**：🎯 M6 打通仿真 → 真机 pipeline；🔥 Evo-RL 加分实验；简历定稿

### Day 36（05-25）：导出 Isaac Lab policy

- [ ] 导出 `*.pt`
- [ ] 写推理脚本（不依赖 Isaac Lab 运行时）

### Day 37-38（05-26 ~ 05-27）：ROS 2 部署

- [ ] ROS 2 节点加载 policy
- [ ] 订阅真机传感器 + 发布动作

### Day 39（05-28）：Sim-to-Real gap 调试

- [ ] 观测噪声注入
- [ ] 电机延迟模拟
- [ ] 对比实验

### Day 40（05-29）：🔥 Evo-RL 加分实验

**这一天专门做 Evo-RL 对比实验**（如主线进度落后则跳过）

```bash
# 克隆
cd ~/embodied-ai
git clone https://github.com/MINT-SJTU/Evo-RL.git
cd Evo-RL

# 环境
conda create -y -n evo-rl python=3.10
conda activate evo-rl
pip install -e .

# 跑 SO-101 baseline（按官方 README）
```

- [ ] 跑通 Evo-RL 在 SO-101 上的 baseline
- [ ] 与 Week 4 的 π₀ / ACT 做对比
- [ ] **产出对比表**：

  | 方法 | 成功率 | 动作平滑度 | 泛化性 | 训练时间 |
  |---|---|---|---|---|
  | ACT | | | | |
  | π₀ | | | | |
  | Evo-RL | | | | |

- [ ] 简历加一行：
  > 在 SO-101 上同时评估 Imitation Learning（π₀）和 Offline RL（Evo-RL）两种方法，基于 SJTU MINT Lab 开源框架做差异化对比实验

### Day 41-42（05-30 ~ 05-31）：简历 + GitHub 打磨

- [ ] 简历最终版（中英双版）
- [ ] GitHub README 完善（demo 视频嵌入、架构图）
- [ ] 所有笔记 push

### 🦿 Locomotion 穿插（本周可选）

- [ ] B 站系列 **Chapter 6-7**（地形，19+46 分钟）— 如果 Week 5 没看完
- [ ] **任务 L8**（可选）：域随机化消融 —— Anymal 开/关 DR 对比

### ⚠️ Week 6 优先级（时间不够时砍掉顺序）

1. Sim-to-Real pipeline（M6）← 最重要
2. 简历 + GitHub 打磨 ← 必做
3. Evo-RL 加分实验 ← 可选
4. Locomotion Chapter 6-7 ← 最后

---

## Week 7：投递 + 内推（06-01 ~ 06-07）

### ⚠️ 本周零新学习资源

### Day 43（06-01）：第一梯队投递

- [ ] 银河通用：hr@galbot.com（附 demo 视频）
- [ ] 上海 AI Lab
- [ ] 字节 Seed
- [ ] 智元机器人

### Day 44（06-02）：内推启动

- [ ] 联系 Du Fan / Alex 推银河通用、智元
- [ ] 知乎/小红书搜"具身智能内推 2026"

### Day 45-47（06-03 ~ 06-05）：第二梯队

- [ ] 千寻智能
- [ ] 宇树科技
- [ ] 松延动力
- [ ] 魔法原子
- [ ] 上海期智研究院

### Day 48-49（06-06 ~ 06-07）：车企 + 面试准备

---

## Week 8：面试冲刺（06-08 ~ 06-14）

### 技术面准备清单

#### VLA / π₀（必考）
- [ ] π₀ 架构：VLM backbone（PaliGemma）+ Action Expert + Flow Matching
- [ ] 为什么 Flow Matching 而不是 Diffusion
- [ ] Action Expert attention mask
- [ ] π₀ vs RT-2 vs OpenVLA

#### Isaac Lab / Sim
- [ ] Manager-based Env 设计
- [ ] 并行 PPO 原理
- [ ] 域随机化
- [ ] USD vs URDF

#### ROS 2
- [ ] Publisher / Subscriber 手撕
- [ ] TF2
- [ ] QoS

#### Locomotion（辅线）
- [ ] 用 Week 1-5 笔记复习
- [ ] 能聊 "Learning to Walk in Minutes"

#### Evo-RL（如果做了）
- [ ] Offline RL vs IL 的区别
- [ ] 为什么 Offline RL 在真机 VLA 上难

#### 刷题
- [ ] LeetCode Hot 100（一天 5 题）
- [ ] PyTorch：自定义 Dataset、DataLoader、分布式
- [ ] Transformer 手撕 attention

### HR 面准备
- [ ] 自我介绍（中英）
- [ ] 为什么选具身智能
- [ ] 职业规划
- [ ] 薪资预期（参考银河通用 6-8k/天）

---

## 🦿 Locomotion 辅线汇总

### 总投入预算

| 周次 | 任务 | 时长 | 产出 |
|---|---|---|---|
| Week 1 | L1-L2：扫读综述 + 10 术语 | 2h | `notes/locomotion.md` |
| Week 2 | L3：B 站 Ch1-2 + 论文前半 | 2-3h | SCQA 笔记 |
| Week 3 | L4：B 站 Ch3 + 论文后半 + 讲解 | 2h | 完整笔记 |
| Week 4 | **暂停** | 0h | — |
| Week 5 | L5-L7：G1 训练 + B 站 Ch4-5 | 3-4h | `demos/g1_locomotion.mp4` |
| Week 6 | L8：B 站 Ch6-7 + DR 消融（可选） | 3-4h | 对比图（可选） |
| **合计** | | **12-15h** | 简历 2 行 + 1 视频 |

### 执行规则（铁律）

| 场景 | 执行 |
|---|---|
| ✅ 主线当周任务全部完成 | 穿插 Locomotion |
| ⚠️ 主线延期 | **跳过 Locomotion** |
| 🔴 Week 4 和 Week 7-8 | **零 Locomotion** |

### 10 个核心术语（面试聊天用）

| 术语 | 一句话解释 |
|---|---|
| Proprioception | 关节角度、角速度、IMU — 机器人"自己感知自己" |
| Privileged Information | 仿真里能拿到的"作弊数据"，只给 teacher 用 |
| Teacher-Student | 先用特权信息训 teacher，蒸馏到 student |
| Domain Randomization | 仿真随机化物理参数，提升真机鲁棒性 |
| Sim-to-Real Gap | 仿真训好的 policy 到真机掉点 |
| PD 控制器 | RL 输出目标关节角，PD 跟踪 |
| Reward Shaping | 10+ 项奖励组合（速度、姿态、能耗、足部接触） |
| Curriculum Learning | 从简单地形到难地形 |
| ZMP / LIP / MPC | 传统控制三大概念（名字知道即可） |
| WBC | Whole Body Control，传统方法集大成 |

---

## 🔥 Evo-RL 加分项规划

### 项目信息

- **GitHub**：https://github.com/MINT-SJTU/Evo-RL
- **机构**：SJTU MINT Lab（上海交大机器智能与交互实验室）
- **定位**：SO-101 上的真实世界 Offline RL baseline
- **基础**：LeRobot
- **时间线**：
  - 2026-02-26：首个 SO101 baseline 发布
  - 2026-03-07：加入 AgileX PiPER 支持

### 为什么加这个

- ✅ **原生支持 SO-101**（你的硬件）
- ✅ **基于 LeRobot**（Week 4 已打通）
- ✅ **Offline RL** 是 VLA 领域差异化路线
- ✅ **学术前沿**（2026 年 2 月才发布）

### 执行规则

| 前置条件 | 说明 |
|---|---|
| ✅ Week 4 M4 必须达成 | π₀ 真机 demo 跑通 |
| ✅ Week 6 主线 M6 完成 | Sim-to-Real pipeline 打通 |
| ✅ 简历 + GitHub 打磨完 | Day 41-42 |
| ⏳ **只有以上都完成才开始** | Day 40 执行 |

### 简历定位

**不是替代 π₀**，是**增强简历差异化**：

```markdown
### 项目 2 升级版：SO-101 + VLA 方法对比

**技术栈**：LeRobot / π₀ / Evo-RL / PyTorch / Flow Matching

**亮点**：
- 使用 LeRobot 在 SO-101 上采集 100+ 条抓取轨迹
- 微调 π₀ 预训练模型（VLM + Action Expert + Flow Matching）
- **同时评估 Imitation Learning（π₀）和 Offline RL（Evo-RL）两种方法**
- 基于 SJTU MINT Lab 2026 开源框架做差异化对比实验（跟踪前沿）
- 对比成功率、动作平滑度、泛化性差异
```

### 时间允许时的深化（可选）

- Week 6 Day 40 做完基础对比后，如果有时间：
  - 改 Evo-RL 的 reward
  - 加入 π₀ 作为 warm-start（融合 IL + Offline RL）

---

## 📝 简历素材卡（持续更新）

> 每周完成任务后更新这一节！

### 项目 1：Isaac Lab VLA 仿真训练平台

**技术栈**：Python / PyTorch 2.5.1 / Isaac Sim 4.5 / Isaac Lab v2.3.2 / rsl_rl / PPO

**亮点**：
- [x] 在 Ubuntu 22.04 + RTX 4070 Ti Super 完整部署 Isaac Sim + Isaac Lab 环境
- [ ] 基于 Manager-based Config 自定义 SO-101 操作任务（Reach / Lift / Pick-Place）
- [ ] 2048+ 并行环境 PPO 训练，对比不同 reward weighting
- [ ] 引入域随机化（光照、摩擦、物体位置）提升 Sim-to-Real 鲁棒性

### 项目 2：SO-101 + π₀ 真机 VLA 部署

**技术栈**：LeRobot / π₀ / HuggingFace / PyTorch / Flow Matching / Evo-RL（可选）

**亮点**：
- [ ] 使用 LeRobot 在 SO-101 机械臂上采集 100+ 条抓取轨迹
- [ ] 微调 π₀ 预训练模型（VLM backbone + Action Expert + Flow Matching）
- [ ] 对比 ACT / Diffusion Policy / π₀ 三种方法的真机性能
- [ ] 完成 Sim-to-Real pipeline：Isaac Lab 训练 → ROS 2 节点部署
- [ ] **（可选）同时评估 Offline RL（Evo-RL）方法，跟踪 2026 学术前沿**

### 项目 3：ROS 2 机器人软件系统

**技术栈**：ROS 2 Humble / Python / TF2 / rclpy / cv_bridge

**亮点**：
- [ ] 实现 SO-101 真机完整 ROS 2 节点栈
- [ ] 基于 TF2 管理多传感器坐标变换
- [ ] 统一的仿真/真机部署接口（Isaac Sim ROS 2 Bridge）

### 项目 4（辅）：Humanoid Locomotion 研究复现

**技术栈**：Isaac Lab / PPO / rsl_rl / Unitree G1 URDF

**亮点**：
- [ ] 复现 Rudin et al. (CoRL 2022) 并行 RL locomotion 工作流
- [ ] 在 Unitree G1 上训练 rough-terrain 步态 policy（4096 并行环境）
- [ ] （可选）完成域随机化开/关的 sim-to-real 鲁棒性消融实验

### 原有研究项目（保留）

- **Audio-L3A**（墨尔本大学）：Class-incremental learning for multi-label audio classification
  - CNN14 backbone + Weighted Analytic Classifier + RLS 闭式更新
  - Spartan A100 HPC 集群实验

- **PTX Capstone (Titan)**：healthcare data integration control plane

---

## 🛠️ 常见坑速查

### Isaac Sim / Isaac Lab

| 报错 | 解决方案 |
|---|---|
| `CUDA error 999: cudaErrorUnknown` | `sudo reboot`（驱动僵尸状态，Day 2 遇到过 ✅ 已解决） |
| `ImportError: libGL.so.1` | `sudo apt install libgl1-mesa-glx libglib2.0-0` |
| Isaac Sim GUI 白屏 10-20 分钟 | **正常**，shader 编译中，耐心等 |
| GNOME "无响应"对话框 | 点"等待"，90% 是误报 |
| ROS 2 Bridge 启动失败 | 忽略，Week 3 装 ROS 2 后自动解决 |
| `CUDA out of memory` | `--num_envs` 从 2048 降到 1024 或 512 |
| `pip dependency resolver` 警告 | 忽略，Isaac Sim 已知问题 |
| 训练曲线不上升 | `--num_envs` 太小，PPO 需要大 batch |
| conda 找不到 `isaacsim` | `conda activate isaaclab` |

### ROS 2

| 报错 | 解决方案 |
|---|---|
| `ros2: command not found` | `source /opt/ros/humble/setup.bash` |
| `colcon build` 失败 | 检查 `package.xml` 依赖 |
| TF 变换找不到 | 检查 `robot_state_publisher` 是否启动 |
| RViz 看不到机器人 | Fixed Frame 改 `world` 或 `base_link` |

### LeRobot / SO-101

| 报错 | 解决方案 |
|---|---|
| 舵机连接不上 | `sudo chmod 666 /dev/ttyUSB0` |
| 数据采集丢帧 | 降低采集频率或减少相机 |
| π₀ 权重下载慢 | 用镜像 / Spartan 下载 |

### Anaconda

| 报错 | 解决方案 |
|---|---|
| `conda: command not found` | `eval "$(~/anaconda3/bin/conda shell.bash hook)" && conda init` |
| 每次开终端都进 `(base)` | `conda config --set auto_activate_base false` |

---

## 📊 进度追踪

### Week 1 进度

#### Day 1（04-18 周六）✅ 完成
- [x] nvidia-smi 检查驱动（580.126.09 / CUDA 13.0）
- [x] 磁盘空间（762GB 可用）
- [x] Anaconda 安装 + conda init
- [x] 创建 isaaclab 环境（Python 3.10）
- [x] 工作目录建立
- **收获**：硬件配置完美，RTX 4070 Ti Super + 16GB 完全够用
- **耗时**：约 1 小时

#### Day 2（04-19 周日）✅ 完成
- [x] PyTorch 2.5.1 + cu124 安装并验证
- [x] Isaac Sim 4.5.0 安装（pip 方式，~10GB）
- [x] Isaac Lab 克隆 + `./isaaclab.sh --install`
- [x] 跑通 tutorial（GUI 出现 3D 场景）
- **踩坑**：
  - CUDA 999 → 重启解决
  - shader 编译 15 分钟（以为卡死）
  - GNOME 误报"无响应"
  - Anaconda 装完没 init
- **收获**：
  - Isaac Sim + Isaac Lab 完整可用
  - 理解了 Isaac Sim vs Isaac Lab 关系
  - 学会了"收藏给未来的自己"（不强行今晚消化所有资源）
- **耗时**：约 4 小时（含踩坑）
- **🎯 M0 达成**

#### Day 3（04-20 周一）⏳ 下一步
- [ ] B 站 1.1 代码框架
- [ ] 官方中文文档快速入门
- [ ] 跑 4 个 tutorial
- [ ] 回答 4 个概念问题
- [ ] 产出 `notes/week1/day3.md`

#### Day 4 - Day 7
（按计划执行，完成后填写）

### Week 2-8
（按周填写）

---

## 📌 重要提醒

1. **主线永远第一**：VLA / π₀ / SO-101 优先于 Locomotion 和 Evo-RL
2. **每日提交 Git**：`notes/` 目录每天 commit，哪怕只改一个字
3. **视频是王道**：每完成一个里程碑录 30 秒 demo
4. **简历素材卡持续更新**：Week 7 投递前再改就来不及
5. **面试准备从 Week 4 就开始**
6. **遇到阻塞立刻求助**：不要一个问题卡 3 小时以上
7. **防止收藏党**：看 `future_reading.md` 的 3 条铁律

---

## 🔗 关键资源链接

**主线**：
- [Isaac Lab 官方文档](https://isaac-sim.github.io/IsaacLab/)
- [Isaac Lab 中文文档](https://docs.robotsfan.com/isaaclab/)
- [LeRobot GitHub](https://github.com/huggingface/lerobot)
- [ROS 2 Humble 文档](https://docs.ros.org/en/humble/)
- [π₀ 论文](https://www.physicalintelligence.company/blog/pi0)

**辅线**：
- [Learning to Walk in Minutes](https://arxiv.org/abs/2109.11978)
- [Legged Gym](https://github.com/leggedrobotics/legged_gym)
- [Evo-RL](https://github.com/MINT-SJTU/Evo-RL)

**B 站教程**：
- [IsaacLab 中文教程](https://www.bilibili.com/video/BV1pLYAz1EH3/)
- [强化学习+机器人运动控制入门](https://space.bilibili.com/) （搜"二营长向强化学习开炮"）

**公司**：
- 银河通用 hr@galbot.com
- [上海 AI Lab](https://www.shlab.org.cn/)

---

**最后一句话**：这份计划 **80% 执行 > 100% 规划**。开始做比想怎么做重要。

祝你 6 月 offer 入账 🚀