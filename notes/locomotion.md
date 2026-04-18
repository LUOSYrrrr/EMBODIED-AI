# 🦿 Locomotion 辅线笔记

> 目标:Week 5 录制 G1 locomotion demo + 简历加 2 行 + 面试能聊 10 分钟
>
> **铁律**:主线(VLA/π₀)落后就跳过 Locomotion。Week 4 和 Week 7-8 零 Locomotion。

---

## 时间预算

| 周次 | 任务 | 时长 | 产出 |
|---|---|---|---|
| Week 1 | L1-L2:概念 + 10 术语 | 2h | 本文件的"10 核心术语" |
| Week 2 | L3:"Walk in Minutes" 前半 SCQA | 2-3h | 精读笔记 |
| Week 3 | L4:论文后半 + 讲解 | 2h | 给外行讲懂的 500 字 |
| Week 4 | **暂停** | 0h | — |
| Week 5 | L5-L6:G1 训练 + 录视频 | 3-4h | `demos/g1_locomotion.mp4` |
| Week 6 | L7:DR 消融(可选) | 3-4h | 对比图 + 200 字分析 |
| **合计** | | **12-15h** | 简历 2 行 + 1 视频 |

---

## 10 个核心术语(Week 1 L2 完成)

| 术语 | 一句话解释 | 我懂了吗 |
|---|---|---|
| Proprioception | 关节角度、角速度、IMU 数据——机器人"自己感知自己" | [ ] |
| Privileged Information | 仿真里能拿到的"作弊数据"(真实摩擦、外力),只给 teacher 用 | [ ] |
| Teacher-Student | 先用特权信息训 teacher,再蒸馏到只用本体感知的 student | [ ] |
| Domain Randomization | 仿真里随机化物理参数,让 policy 对真机差异鲁棒 | [ ] |
| Sim-to-Real Gap | 仿真训好的 policy 到真机掉点的核心问题 | [ ] |
| PD 控制器 | RL 输出目标关节角,PD 负责跟踪 | [ ] |
| Reward Shaping | 精心设计 10+ 项奖励(速度、姿态、能耗、足部接触…) | [ ] |
| Curriculum Learning | 从简单地形开始,逐渐加难度 | [ ] |
| ZMP / LIP / MPC | 传统控制三大概念(名字知道即可) | [ ] |
| WBC | Whole Body Control,传统方法的集大成 | [ ] |

---

## L3-L4:"Learning to Walk in Minutes" 精读(Week 2-3)

论文链接:https://arxiv.org/abs/2109.11978

### SCQA 笔记

- **Situation**:(待填)
- **Complication**:(待填)
- **Question**:(待填)
- **Answer**:(待填)

### 必须搞懂的 5 件事

1. [ ] Observation 空间(proprioception vs privileged)
2. [ ] Action 空间(关节目标位置)
3. [ ] Reward 函数的 10+ 项组合
4. [ ] Terrain curriculum 的从易到难
5. [ ] 域随机化了哪些参数

### 给外行讲懂的 500 字(Week 3 L4)

TBD

---

## L5-L6:G1 Locomotion 实战(Week 5)

### 跑通命令

```bash
cd ~/embodied-ai/isaaclab/IsaacLab

# 训练
./isaaclab.sh -p scripts/reinforcement_learning/rsl_rl/train.py \
    --task Isaac-Velocity-Rough-G1-v0 \
    --num_envs 4096 --headless

# Play
./isaaclab.sh -p scripts/reinforcement_learning/rsl_rl/play.py \
    --task Isaac-Velocity-Rough-G1-v0 --num_envs 16
```

### 产出

- [ ] `demos/g1_locomotion.mp4`
- [ ] 简历行:
  > 基于 Isaac Lab 在 Unitree G1 人形机器人上训练 rough-terrain locomotion policy
  > (4096 并行环境 + PPO),复现 Rudin et al. CoRL 2022 工作流

---

## L7:DR 消融(Week 6,可选)

TBD

---

## 面试话术预备

**Q**: 讲讲 Locomotion 这块你做了什么?

**A**: 我复现了 Rudin et al. CoRL 2022 的 "Learning to Walk in Minutes" 工作流。核心是用 Isaac Lab 的 4096 并行环境跑 PPO,在 Unitree G1 上训出 rough-terrain 步态。关键点是 terrain curriculum 从平地逐渐升级到楼梯/斜坡,以及域随机化让 policy 对真机物理参数差异鲁棒。我也跑了 DR 开/关的消融,印证了 sim-to-real gap 主要由物理参数分布差异导致。

**Q**: π₀ 这种 VLA 模型怎么应用到 locomotion?

**A**: TBD
