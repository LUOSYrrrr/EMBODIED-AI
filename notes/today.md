# 📋 今日任务 — Day 2 / Week 1

> **时间戳**：2026-04-19（周日，AEST）
> **进度**：Day 2 / 56 · Week 1 / 8
> **距 06-07 投递**：还有 49 天
> **状态**：🟢 M0 已达成（Day 2 装机任务于 04-18 提前完成），今日滚动吃下 Day 3 的概念任务
> **时间预算**：3-4 小时

---

## 🎯 核心任务（必做）

### 上午（1-2h）理论打底

- [ ] B 站「IsaacLab 中文教程 1.1 代码框架」40 分钟 https://www.bilibili.com/video/BV1pLYAz1EH3/
- [ ] 对照官方中文快速入门 20 分钟 https://docs.robotsfan.com/isaaclab/source/setup/quickstart.html

### 下午（2h）动手 + 产出

跑 4 个 tutorial（见命令速查）：
- [ ] `create_empty.py` 空场景
- [ ] `spawn_prims.py` 生成刚体
- [ ] `run_articulation.py` 加载机器人
- [ ] `create_scene.py` 交互式场景

在 `notes/week1.md` 回答 4 个概念问题（**先不查答案**）：
- [ ] Q1：sim / stage / scene 各自是什么？
- [ ] Q2：Articulation vs RigidObject 区别？
- [ ] Q3：`sim.step()` 循环 vs RL episode 的关系？
- [ ] Q4：USD vs URDF 的关系？

## ⭐ 加速版彩蛋（有余力才做）

- [ ] 预读 `reach_env_cfg.py` 里 5 个 Manager 的定义，为 Day 4 Franka Reach 训练暖场

## 🦿 Locomotion 穿插（周末 2h）

- [ ] **L1**：知乎扫读「RL 做足式机器人运控的经典必读文章」— 只记 3-4 个论文名 https://zhuanlan.zhihu.com/p/29806809248
- [ ] **L2**：`notes/locomotion.md` 补完 10 术语一句话解释

---

## 📦 今日产出

- `notes/week1.md` — 4 个概念问题填完
- `notes/daily/2026-04-19.md` — 踩坑记 + 一句话复盘
- `notes/locomotion.md` — 10 术语（若完成 L2）
- Commit：`feat(day2): IsaacLab 4 tutorials + 4 core concepts`

## ⚙️ 命令速查

```bash
cd ~/embodied-ai/isaaclab/IsaacLab
conda activate isaaclab
./isaaclab.sh -p scripts/tutorials/00_sim/create_empty.py
./isaaclab.sh -p scripts/tutorials/00_sim/spawn_prims.py
./isaaclab.sh -p scripts/tutorials/01_assets/run_articulation.py
./isaaclab.sh -p scripts/tutorials/02_scene/create_scene.py
```

## ⚠️ 风险提醒

- **别冲 Day 4**：Franka Reach 训练留到明天，今日把概念吃透更值钱
- Isaac Sim 首次启动 shader 编译 10-20 分钟，GUI "白屏/无响应" 90% 是 GNOME 误报
- 主线没做完就**跳过 Locomotion**，不要颠倒优先级

---

## 📖 本周复盘模板（Day 2 周日 mini 版）

> Week 1 正在进行中，只有 2 天数据，迷你复盘即可。

- **Week 1 已完成**：M0 环境打通（PyTorch + Isaac Sim 4.5 + IsaacLab v2.3.2）
- **最大收获**：`git tag` 对齐框架版本；`./isaaclab.sh -p` 命令行为主，不必开 GUI
- **最大阻塞**：CUDA 999 + shader 编译耐心考验（已解）
- **Week 1 剩余 5 天目标**：拿下 M1（Franka Reach 训练视频 + TB 曲线）
- **节奏自评**：🟢 提前半天，保持不加速

---

## 💪 一句话激励

**M0 已落袋，今日把 sim/stage/scene 讲给自己听明白 —— 明天 Franka Reach 上桌就不慌。**
