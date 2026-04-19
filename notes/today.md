# 📋 今日任务 — Day 3 / Week 1

> **时间戳**：2026-04-19（周日）
> **进度**：Day 3 / 56 · Week 1 / 8（滚动推进：Day 1+2 已于 04-18 完成）
> **距离 06-07 投递日**：还有 50 天
> **时间预算**：3-4 小时

---

## 🎯 上午（1-2h）：看 B 站中文教程

- [ ] B 站「IsaacLab 中文教程 1.1 代码框架」（40 min）
  - https://www.bilibili.com/video/BV1pLYAz1EH3/
- [ ] 对照官方中文文档「快速入门」（20 min）

## 🛠️ 下午（2h）：动手 + 产出

跑 4 个 tutorial：

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

- [ ] `create_empty.py` — 空场景 GUI
- [ ] `spawn_prims.py` — 生成刚体
- [ ] `run_articulation.py` — 加载机器人资产
- [ ] `create_scene.py` — 交互式场景

## ✍️ 在 [week1.md](week1.md) 回答 4 个概念问题（不查答案，先凭印象写）

- [ ] Q1：sim / stage / scene 各自是什么？
- [ ] Q2：Articulation vs RigidObject 的区别？
- [ ] Q3：`sim.step()` 循环和 RL episode 什么关系？
- [ ] Q4：USD 是什么，和 URDF 什么关系？

## 🔧 开工前（15 min）冒烟测试

- [ ] 重开终端：`conda activate isaaclab && ./isaaclab.sh -p scripts/tutorials/00_sim/create_empty.py`

---

## 📦 今日产出

- [week1.md](week1.md) 填完 4 个概念问题 + 4 tutorial 产出
- [daily/2026-04-19.md](daily/2026-04-19.md) 记当天踩坑
- Commit：`feat(day3): IsaacLab 4 tutorials + 4 core concepts`

---

## ⚠️ 风险提醒

- **别冲 Day 4**：今天吃透概念比跑通更多 tutorial 重要
- **触发 3 日反思暂停**：今晚回答"过去 3 天最大阻塞是什么"
- 非主线（Locomotion L1-L2 / future_reading 归档）塞不进就推迟，不占主线时间

---

## 💪 一句话激励

**Day 2 提前一天完成 — 节奏稳住，Day 3 按部就班吃透 4 个概念就是胜利。**
