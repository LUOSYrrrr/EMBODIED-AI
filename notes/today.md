# 📋 今日任务 — Day 14 / Week 2

> **时间戳**：2026-05-01（周五 AEST）
> **进度**：Day 14 / 56 · Week 2（最后一天）
> **距离 06-07 投递日**：还有 **37 天**
> **状态**：⚠️ 进度笔记停在 04-22（Day 5），9 天断层 — 今日先做**状态对齐**再推进
> **时间预算**：4-5 小时

---

## 🛑 反思暂停（3-day rule 已积压两轮）

收工前用 5 分钟在 `notes/daily/2026-05-01.md` 答 3 题：
1. 04-23 ~ 04-30 这 9 天主线实际推到哪一步？M2 / M3 进度卡在哪？
2. 没写日记是因为太忙、忘记，还是没产出可写？
3. Week 2 剩 0 天 → 是否需要把剩余 milestone 平移到 Week 3 做 re-plan？

---

## 🎯 核心任务（必做）

按 v3.0 流水线第 2-3 步推进。**先验状态再选路径**：

- [ ] **A. M2 状态确认（30min）**
  - 翻 `outputs/train/act_so101/` 与 `demos/` 看 ACT 真机评估是否完成
  - 若 **未达成 ≥50% 成功率** → 今天主攻 A，B 顺延
  - 若 **已达成** → 跳到 B/C

- [ ] **B. π₀ 微调启动（2-3h，主路径）**
  - 验权重在 `~/embodied-ai/lerobot/weights/pi0/`，缺则 `huggingface-cli download lerobot/pi0`
  - `lerobot` 配置 `policy=pi0`、`dataset_repo_id=LUOSYrrrrr/so101_pickplace_v1`、batch=2-4（4070 Ti Super 16GB 显存边界）
  - **dry-run 100 steps 验前向反向不 OOM**，再决定本地全跑 or Spartan 提交
  - 显存炸 → 写 Spartan SBATCH 脚本，scp 数据集 + 周末挂队列

- [ ] **C. 周末计划（30min）**
  - 周六（Day 15 / Week 3 Day 1）：π₀ 微调监控 + L3 Locomotion B 站 Ch1-2（v3.0 限定 2h）
  - 周日（Day 16）：Week 2 复盘 + π₀ 真机 1-shot 推理冒烟

## ⭐ 加速版彩蛋（B 顺利再做）

- [ ] 在 `resume_assets.md` 项目 2 加上 "ACT baseline N% 真机成功率"（数字按 A 实测）
- [ ] `notes/week1.md` 补一段 "π₀ vs ACT vs Diffusion Policy" 三句话对比，Week 8 面试直接复用

## 🦿 Locomotion 穿插

**今日跳过**（周五非周末）。L3 任务推到周六 Day 15（v3.0 仅在主线顺畅时穿插）。

---

## 💻 命令速查

```bash
conda activate lerobot && cd ~/embodied-ai/lerobot

# A: ACT eval 回看
ls outputs/train/act_so101/checkpoints/ && tensorboard --logdir outputs/train/act_so101

# B: π₀ 微调 dry-run（按你版本调整 entrypoint）
python -m lerobot.scripts.train \
    policy=pi0 env=so101 \
    dataset_repo_id=LUOSYrrrrr/so101_pickplace_v1 \
    training.batch_size=2 training.num_steps=100

# 显存监控
watch -n 1 nvidia-smi

# Spartan 备选
sbatch scripts/spartan_pi0_finetune.sbatch  # 不存在就今天写一个
```

---

## ⚠️ 风险提醒

1. **断层风险最大** — 9 天没记录,先花 30min 把 04-23~04-30 的实际进度补到 `progress.md`,否则 Week 7 投递时简历素材对不上
2. **π₀ batch size 边界** — 16GB 显存 + π₀(VLM 3B) 大概率 OOM,先 batch=2 试,gradient_checkpointing=true
3. **Week 2 已用尽** — 今天 Day 14 是 Week 2 最后一天,M2 / M3 全都晚于 master_plan,周日复盘必须重排 Week 3-4
4. **Spartan 队列** — 周末提交大概率排队,周五尽量先把脚本写好不要等

---

## 📦 今日产出

- `notes/daily/2026-05-01.md`：A/B 实测结果 + 反思暂停 3 答 + 9 天进度补记
- `notes/progress.md`：补 Day 6-13 真实状态（即使是空白也写"未推进"）
- `~/embodied-ai/lerobot/outputs/train/pi0_so101/`：π₀ dry-run 日志
- Commit：`notes(day14): pi0 finetune dry-run + 9-day progress catch-up`

---

## 💪 一句话激励

37 天还够把 π₀ demo 视频拍出来 — 但只够你**今天**就把断层补上、把微调按下去启动键。
