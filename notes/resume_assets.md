# 📝 简历素材卡

> 每周完成任务后更新。Week 7 投递前是最终版。

---

## 项目 1：Isaac Lab VLA 仿真训练平台

**技术栈**：Python / PyTorch / Isaac Sim 4.5 / Isaac Lab 2.x / rsl_rl / PPO

**亮点**：
- [ ] 搭建 Isaac Sim + Isaac Lab 完整开发环境(Ubuntu 22.04 + RTX 4070 Ti Super)
- [ ] 基于 Manager-based Config 自定义 SO-101 操作任务(Reach / Lift / Pick-Place)
- [ ] 2048 并行环境 PPO 训练,对比不同 reward weighting 的效果
- [ ] 引入域随机化(光照、摩擦、物体位置)提升 Sim-to-Real 鲁棒性

**demo**: `demos/franka_reach.mp4` / `demos/so101_sim_pickplace.mp4`

---

## 项目 2:SO-101 + π₀ 真机 VLA 部署

**技术栈**:LeRobot / π₀ / HuggingFace / PyTorch / Flow Matching

**亮点**:
- [ ] 使用 LeRobot 在 SO-101 机械臂上采集 100+ 条抓取轨迹
- [ ] 微调 π₀ 预训练模型(VLM backbone + Action Expert + Flow Matching)
- [ ] 对比 ACT / Diffusion Policy / π₀ 三种方法的真机性能
- [ ] 完成 sim-to-real pipeline:Isaac Lab 训练 → ROS 2 节点部署

**demo**: `demos/pi0_so101_grasp.mp4`

---

## 项目 3:ROS 2 机器人软件系统

**技术栈**:ROS 2 Humble / Python / TF2 / rclpy / cv_bridge

**亮点**:
- [ ] 实现 SO-101 真机完整 ROS 2 节点栈(camera / controller / vla_policy)
- [ ] 基于 TF2 管理多传感器坐标变换
- [ ] 统一的仿真/真机部署接口(通过 Isaac Sim ROS 2 Bridge 切换)

---

## 项目 4(辅):Humanoid Locomotion 研究复现

**技术栈**:Isaac Lab / PPO / rsl_rl / Unitree G1 URDF

**亮点**:
- [ ] 复现 Rudin et al. (CoRL 2022) 并行 RL locomotion 工作流
- [ ] 在 Unitree G1 上训练 rough-terrain 步态 policy(4096 并行环境)
- [ ] 完成域随机化开/关对 sim-to-real 鲁棒性的消融实验(可选)

**demo**: `demos/g1_locomotion.mp4`

---

## 项目 5(可选加分):π₀ vs Evo-RL 对比

**技术栈**:Evo-RL / π₀ / Isaac Lab

**亮点**:
- [ ] TBD(Week 6 根据主线进度决定)

---

## 原有研究项目(保留)

### Audio-L3A(墨尔本大学)
Class-incremental learning for multi-label audio classification
- CNN14 backbone + Weighted Analytic Classifier + RLS 闭式更新
- Spartan A100 HPC 集群实验

### PTX Capstone (Titan)
Healthcare data integration control plane

---

## 自我介绍口径(中)

> 我是 XX,墨尔本大学 XX 方向研究生,主攻具身智能的 VLA 大模型方向。
> 过去 8 周内,我从零搭建了 Isaac Sim + Isaac Lab + LeRobot + ROS 2 的完整开发环境,
> 在自有的 SO-101 机械臂上复现了 π₀ 抓取任务,并打通了 Isaac Lab 仿真训练 → 真机部署的 sim-to-real pipeline。
> 辅线上复现了 Rudin CoRL 2022 的并行 RL locomotion 工作流。
> 期望加入贵司的 VLA / Manipulation 团队。

## 自我介绍口径(英)

> TBD
