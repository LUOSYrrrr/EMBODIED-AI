# 📋 今日任务 — Day 3 / Week 1

> **时间戳**：2026-04-20（周一，墨尔本时区）
> **进度**：Day 3 / 56 · Week 1 / 8
> **距离 06-07 投递日**：还有 48 天
> **时间预算**：3-4 小时

---

## 🎯 核心任务（必做）

### 上午（1-2h）：看 B 站中文教程

- [ ] B 站「IsaacLab 中文教程 1.1 代码框架」（40 min）
  - https://www.bilibili.com/video/BV1pLYAz1EH3/
- [ ] 对照官方中文文档「快速入门」（20 min）
  - https://docs.robotsfan.com/isaaclab/source/setup/quickstart.html

### 下午（2h）：动手跑 4 个 tutorial

- [ ] `create_empty.py` — 空场景 GUI
- [ ] `spawn_prims.py` — 生成刚体
- [ ] `run_articulation.py` — 加载机器人资产
- [ ] `create_scene.py` — 交互式场景

### ✍️ 4 个概念问题（不查答案，先凭印象写在 [week1.md](week1.md)）

- [ ] Q1：sim / stage / scene 各自是什么？
- [ ] Q2：Articulation vs RigidObject 区别？
- [ ] Q3：`sim.step()` 循环和 RL episode 什么关系？
- [ ] Q4：USD 是什么，和 URDF 什么关系？

---

## ⭐ 加速版彩蛋（行有余力）

- [ ] 提前扫一眼 Day 4 的 `Isaac-Reach-Franka-v0` 任务名，确认 Isaac Lab 里能找到
- [ ] 把 4 个 tutorial 的 GIF/截图存进 `demos/`（Week 7 简历素材）

> ❌ **不要**今天就开 Franka 训练 — 概念吃透比跑得快重要

---

## 🛑 反思暂停（每 3 天触发，今天是 Day 3）

收工前 5 分钟，在 [daily/2026-04-20.md](daily/2026-04-20.md) 末尾回答：

1. 过去 3 天最大阻塞是什么？根因是技术 / 时间 / 信息？
2. 学习节奏现在是"过快 / 刚好 / 过慢"？需要调整吗？
3. Day 4 Franka 训练，最担心哪个环节？

---

## 🛠️ 命令速查

```bash
cd ~/embodied-ai/isaaclab/IsaacLab
conda activate isaaclab

./isaaclab.sh -p scripts/tutorials/00_sim/create_empty.py
./isaaclab.sh -p scripts/tutorials/00_sim/spawn_prims.py
./isaaclab.sh -p scripts/tutorials/01_assets/run_articulation.py
./isaaclab.sh -p scripts/tutorials/02_scene/create_scene.py
```

---

## 📦 今日产出

- [week1.md](week1.md) — 填完 4 个概念问题（每题 ≥ 3 句话）
- [daily/2026-04-20.md](daily/2026-04-20.md) — 当天踩坑 + 反思暂停回答
- Commit：`feat(day3): IsaacLab 4 tutorials + 4 core concepts`

---

## ⚠️ 风险提醒

- **GUI 白屏 / GNOME "无响应" 仍可能复发** → 等，别 kill
- **概念 Q3 容易跑偏** → `sim.step()` 是物理仿真步，不是 RL step；一个 episode 包含很多 sim.step
- **周一非 Locomotion 日**（辅线只在周末穿插，今天专注主线）

---

## 💪 一句话激励

**Day 2 已经把最难的环境关闯过了 — Day 3 是收割认知的爽日，把"为什么这样写"写进笔记，Week 4 的真机 demo 才有底气。**
