# 📋 今日任务 — Day 1 / Week 1

> **时间戳**：2026-04-18（周六）生成
> **进度**：Day 1 / 56 · Week 1 / 8
> **距离 06-07 投递日**：还有 50 天
> **状态**：🚀 超进度（M0 已于今日达成，Day 2 计划项也已完成）

---

## 🎯 核心任务（今日，2-3h，可选弹性）

由于 Day 1+2 计划项今天都做完了，今天主线已完成，进入"巩固 + 低强度前瞻"模式：

- [ ] **整理 Day 1/2 踩坑笔记**：确认 `notes/daily/2026-04-18.md` 完整（CUDA 999、IsaacLab v2.x checkout、shader 编译 15min、GNOME 误报）
- [ ] **环境冒烟测试**（15 分钟）：重开终端验证 `conda activate isaaclab && ./isaaclab.sh -p scripts/tutorials/00_sim/create_empty.py` 一次通过，防止明天 Day 3 被环境坑
- [ ] **资源归档**：Day 3 要看的 B 站「IsaacLab 1.1 代码框架」链接 + 官方中文快速入门链接，收进 `future_reading.md`（不看，仅归档）

## ⭐ 加速版彩蛋（可选，1h）

- [ ] **提前看 Day 3 的 4 个概念题**（sim/stage/scene、Articulation、sim.step vs episode、USD vs URDF），**先写下你的猜测答案**，明天看完教程再对照修正 — 主动回忆 > 被动看视频

## 🦿 Locomotion 穿插（周末 slot，Week 1 允许，1-2h）

- [ ] **L1**：扫读知乎《RL 做足式机器人运控的经典必读文章》→ 只记 3-4 个论文名字，不求读懂
- [ ] **L2**：在 `notes/locomotion.md` 写 10 个术语一句话解释（proprioception / privileged info / teacher-student / DR / sim2real gap / PD / reward shaping / curriculum / ZMP-LIP-MPC / WBC）

---

## 📦 今日产出

- `notes/daily/2026-04-18.md`（已存在，确认完整）
- `notes/locomotion.md`（+10 术语 + 3-4 论文名）
- `notes/future_reading.md`（+Day 3 B 站链接归档）
- Commit：`chore(day1): consolidate Day 1-2 notes + locomotion L1-L2`

## ⚡ 命令速查

```bash
# 明早 Day 3 开工前的冒烟测试（今天先跑一次）
conda activate isaaclab
cd ~/embodied-ai/isaaclab/IsaacLab
./isaaclab.sh -p scripts/tutorials/00_sim/create_empty.py
```

## ⚠️ 风险提醒

- **别冲 Day 3**：今天已连跑两天量，晚上堆 tutorial 容易第二天卡 bug 没耐心 → 留着精力明天一次吃透
- **明天 Day 3 触发 3 日反思暂停**：提前备好"过去 3 天最大阻塞是什么"的答案
- **Week 4/7/8 零加速**：把冲刺欲望留到 Week 4 π₀ 真机那一周

---

## 💪 一句话激励

**第一天就达成 M0，节奏已经对了 — 剩下的 50 天不是赶路，是把路走稳。**
