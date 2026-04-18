<!-- Generated at 2026-04-18 15:10 AEDT -->

# 📋 Day 1（日历） / 计划 Day 3 内容 — 2026-04-18（周六）🚀 加速中

- **日历日**：Day 1（formula: `今天 - 2026-04-18 + 1`）
- **实际进度**：Day 1 + Day 2 已在 04-18 当天完成（提前 2 天，🎯 M0 达成）
- **今日推进**：按计划表 **Day 3 内容**（原定 04-20 周一）
- **Week**：1 / 8
- **距 2026-06-07 投递日**：**50 天**
- **本周主题**：Isaac Lab 环境打通 → Franka RL

---

## 🎯 核心任务（必做，3–4h）

### 上午（1–2h）：B 站 + 中文文档扫读
- [ ] B 站「IsaacLab 中文教程 1.1 代码框架」40min
  - https://www.bilibili.com/video/BV1pLYAz1EH3/
- [ ] 官方中文快速入门 20min
  - https://docs.robotsfan.com/isaaclab/source/setup/quickstart.html

### 下午（2h）：跑通 4 个官方 tutorial
```bash
conda activate isaaclab
cd ~/embodied-ai/isaaclab/IsaacLab
./isaaclab.sh -p scripts/tutorials/00_sim/create_empty.py
./isaaclab.sh -p scripts/tutorials/00_sim/spawn_prims.py
./isaaclab.sh -p scripts/tutorials/01_assets/run_articulation.py
./isaaclab.sh -p scripts/tutorials/02_scene/create_scene.py
```

### 📝 概念内化（`notes/week1/day3.md`，不查答案写 4 问）
1. `sim` / `stage` / `scene` 各自是什么？
2. `Articulation` 和普通 rigid body 的区别？
3. `sim.step()` 循环 vs RL 的 episode 是什么关系？
4. USD vs URDF 什么关系？

---

## ⭐ 加速版彩蛋（提前完成后再做）
- [ ] 预读 Day 4 Franka Reach 训练命令 + rsl_rl 参数表
- [ ] 在 `notes/week1.md` 起草「Manager-based 数据流图」TODO 骨架
- [ ] `demos/` 目录预建 + README 占位

---

## 🦿 Locomotion 穿插
本周仅周末（Day 7, 04-24）做 L1-L2。**今日跳过**，把精力压在主线 tutorial。

---

## 📦 今日产出

| 文件 | 内容 |
|---|---|
| `notes/week1/day3.md` | 4 个概念问答 |
| `notes/daily/2026-04-18.md` | 补 Day 3 踩坑记录 |
| `notes/progress.md` | Day 3 checkbox 勾上 |
| commit @ 分支 `claude/daily-2026-04-18` | `docs: Day 3 tutorial walkthrough + 4 concepts` |

---

## 💻 命令速查

```bash
# 环境激活
conda activate isaaclab

# Omniverse 导航：按住【鼠标右键 + WASD】= FPS 漫游
# GUI "无响应" 90% 是 GNOME 误报 → 点"等待"
# shader 首次编译 10–20 分钟，耐心等
```

---

## ⚠️ 风险提醒

- tutorial 之间 stage 状态可能互相污染 → 每次独立启动一次
- `run_articulation.py` 首次要下载 Franka USD，留意网络
- 若 `CUDA error 999` → `sudo reboot`（Day 2 踩过）
- 不要误切回 IsaacLab `main`（v3.0-beta，已 checkout v2.x）
- **节奏 > 速度**：已提前 2 天，不代表可以通宵刷到 Day 5；今天把 4 个概念钉死胜过多跑 2 个 tutorial

---

## 💪 今日一句

> 已提前 2 天达成 M0。50 天后投递，今天把 4 个概念钉死，Day 4 的 Franka RL 会像滑梯。🚀
