# Embodied AI Internship Prep — Progress Log

**目标**:2026 年 6 月具身智能算法实习入职
**开始日期**:2026-04-18
**硬件**:RTX 4070 Ti Super (16GB) + SO-101 + Spartan A100
**当前状态**:🟢 Week 1,Day 2 结束,提前半天(Day 2 任务在 04-18 当天已完成)

---

## 里程碑进度

| 里程碑 | 截止 | 状态 |
|---|---|---|
| 🎯 **M0**:环境打通 | Day 2 | ✅ **2026-04-18 达成**(原计划 Day 2) |
| 🎯 M1:Franka Reach RL 跑通 | Day 7 | ⏳ 目标 Day 4(04-21) |
| 🎯 M2:SO-101 仿真动起来 | Day 14 | ⏳ |
| 🎯 M3:ROS 2 真机闭环 | Day 20 | ⏳ |
| 🎯 M4:π₀ 真机抓取 demo(必杀技) | Day 28 | ⏳ |
| 🎯 M5:Isaac Lab SO-101 仿真训练 | Day 33 | ⏳ |
| 🎯 M6:Sim-to-Real 闭环 | Day 38 | ⏳ |
| 🎯 M7:投递 20+ 家 | Day 47 | ⏳ |
| 🎯 M8:拿到 1+ 面试 | Week 8 | ⏳ |

---

## Week 1(04-18 ~ 04-26):Isaac Lab 环境打通

**周目标**:跑通 Franka Reach/Lift RL 训练,理解 Manager-based 框架

### Day 1(04-18 周六)✅
- [x] nvidia-smi 检查驱动(580.126.09 / CUDA 13.0)
- [x] 磁盘 916GB / 可用 762GB
- [x] Anaconda 24.9.2 安装 + conda init + 关闭 auto_activate_base
- [x] 创建 `isaaclab` conda 环境(Python 3.10)
- [x] 建立 `~/embodied-ai/` 工作目录骨架

**坑**:无
**收获**:硬件配置完美,4070 Ti Super + 16GB 显存够用

### Day 2(04-19 周日)✅ (实际 04-18 完成,提前半天)
- [x] PyTorch 2.5.1 + cu124 安装并验证 `torch.cuda.is_available()`
- [x] Isaac Sim 4.5.0 安装(pip 方式,~10GB)
- [x] IsaacLab 克隆 + **checkout v2.x**(避开 main 的 v3.0.0-beta / Newton)
- [x] `./isaaclab.sh --install`
- [x] 跑通 `create_empty.py`(GUI 出现空 3D 场景)

**坑**(详见 [daily/2026-04-18.md](daily/2026-04-18.md)):
1. IsaacLab `main` 已是 v3.0.0-beta(Newton 物理),不兼容 Isaac Sim 4.5 → 必须 checkout v2.x
2. ROS2 Bridge 启动报错 → 非阻塞,Week 3 装 ROS 2 后自消
3. Isaac Sim 首次启动 shader 编译 10-20 分钟,GNOME 误报"无响应"
4. CUDA 999 错误 → 重启解决(驱动僵尸状态)

**收获**:
- Omniverse 导航:**按住右键 + WASD**(FPS 风格)
- 以后 99% 用 `./isaaclab.sh -p xxx.py` 命令行,不需要开 `isaacsim` GUI
- `git tag` 对齐框架版本:clone 前永远先看 tag,别默认 main

### Day 3(04-20 周一)⏳ 明日
- [ ] B 站「IsaacLab 中文教程 1.1」 + 官方中文快速入门
- [ ] 4 个 tutorial(create_empty / spawn_prims / run_articulation / create_scene)
- [ ] [week1.md](week1.md) 回答 4 个概念问题(sim/stage/scene、Articulation、sim.step vs episode、USD vs URDF)

### Day 4(04-21 周二)🎯 M1
- [ ] Franka Reach 训练(2048 envs, headless, 15-30min)
- [ ] `play.py` + 录制 10 秒视频 → `demos/franka_reach.mp4`
- [ ] TensorBoard 截图:`Train/mean_reward` + `mean_episode_length`

### Day 5(04-22 周三)
- [ ] 通读 `reach_env_cfg.py` + 理解 5 个 Manager
- [ ] 修改 reward 权重对比训练
- [ ] 数据流图 + 笔记

### Day 6(04-23 周四)
- [ ] Franka Lift 训练
- [ ] URDF 标签基础

### Day 7(04-24 周日)
- [ ] 周复盘
- [ ] GitHub 私有仓库 `embodied-ai-journey` 初始化
- [ ] 更新 resume_assets.md
- [ ] 🦿 Locomotion L1-L2(2h)

### Week 1 总结(Day 7 填)
- 完成度:
- 最大收获:
- 最大的坑:
- Week 2 调整:

---

## Week 2-8(占位,按周填)

### Week 2(04-27 ~ 05-03):SO-101 URDF 导入 + LeRobot
### Week 3(05-04 ~ 05-10):ROS 2 + SO-101 真机
### Week 4(05-11 ~ 05-17):🎯 M4 π₀ 真机冲刺
### Week 5(05-18 ~ 05-24):Isaac Lab 仿真训练 + Locomotion
### Week 6(05-25 ~ 05-31):Sim-to-Real + 简历打磨 + Evo-RL(可选)
### Week 7(06-01 ~ 06-07):投递 + 内推
### Week 8(06-08 ~ 06-14):面试冲刺

---

## 笔记组织约定

- `daily/YYYY-MM-DD.md` — 当天踩坑、解决、细节(临场写)
- `week{N}.md` — 周级别专题笔记(如 Day 3 的 4 个概念问题)
- `progress.md` — 本文件,所有里程碑 + 每日 checkbox 高层视图
- `resume_assets.md` — 简历素材,完成后立刻更新
- `locomotion.md` — 辅线专属
- `future_reading.md` — 待读清单

> **写日笔记的时机**:每天收工前 10 分钟,不求工整,重点记"踩了什么坑 + 怎么解的"。
