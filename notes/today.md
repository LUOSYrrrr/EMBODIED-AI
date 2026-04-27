# 📋 今日任务 — Day 10 / Week 2

> **时间戳**：2026-04-27（周一 AEST）
> **进度**：Day 10 / 56 · Week 2 / 8 起始日
> **距离 06-07 投递日**：还有 **41 天**
> **v3.0 pivot 第 6 天**：SO-101 真机 π₀ / π₀.₅ 复现冲刺
> **时间预算**：4-5 小时

---

## 🎯 核心任务（必做）

承接 Day 5-9 的 ACT 真机评估 + π₀ 权重落地，本周目标是在 **Day 14（05-03）前完成 π₀ 微调首跑**。今日是 Week 2 启动日，把 ACT 收尾 + π₀ 微调脚手架搭起来。

- [ ] **A. ACT 评估收尾**（1h）
  - 把 Day 5-9 的真机 rollout 成功率汇总进 `notes/week2.md`
  - 确认是否达到 M2 验收线（≥ 50%），不达标只列 1 条最有可能的 fix（不要再调，进入 π₀ 阶段）

- [ ] **B. π₀ 微调配置 dry-run**（2-2.5h）
  - 检查 `lerobot/configs/policy/pi0.yaml` 与 SO-101 数据集 obs/action 维度对齐
  - 写微调启动脚本 `scripts/train_pi0_so101.sh`（policy=pi0, dataset=你的 so101 数据集）
  - **`--steps 100` 跑 dry-run** 验证能进 train loop，不 OOM、不报 shape mismatch
  - 估算全量 step 数 + 单卡时长，决定本地 4070 Ti Super 还是 Spartan A100

- [ ] **C. Spartan 提交模板**（1h，仅当 B 显示本地不够时）
  - 写 `slurm/pi0_finetune.slurm`（A100 单卡，预估 6-9h）
  - rsync 数据集到 punim2341，记录路径

## ⭐ 加速版彩蛋（B 顺利再做）

- [ ] 在 `resume_assets.md` 项目 2 加一行："SO-101 50 条数据集上微调 π₀（VLM + Action Expert + Flow Matching），对比 ACT baseline"
- [ ] `notes/week2.md` 写 3 句话：π₀ 与 ACT 的核心架构差异（Week 8 面试卡片直接复用）

## 🦿 Locomotion 穿插

**今日跳过**（周一 + Week 2 主线冲刺中）。

---

## 💻 命令速查

```bash
conda activate lerobot
cd ~/embodied-ai/lerobot

# π₀ 微调 dry-run（路径按你实际调整）
python lerobot/scripts/train.py \
    policy=pi0 \
    dataset_repo_id=<你的用户名>/so101_grasp \
    training.offline_steps=100 \
    training.batch_size=8 \
    hydra.run.dir=outputs/dryrun/pi0_so101

# 显存监控
watch -n 1 nvidia-smi

# Spartan 提交（如需）
sbatch slurm/pi0_finetune.slurm
squeue -u $USER
```

---

## ⚠️ 风险提醒

1. **π₀ batch_size**：4070 Ti Super 16GB 大概率只够 batch=4-8，OOM 立刻降
2. **数据集格式**：π₀ 期望 `image` + `state` + `action`，确认 ACT 训练用的同一份数据集 schema 兼容
3. **不要今天就 launch 全量微调**：dry-run 通过 → 明天 Day 11 再启动正式训练
4. **Flow Matching scheduler**：检查配置里 `num_train_timesteps` 默认值（10 步通常够）

---

## 📦 今日产出

- `notes/daily/2026-04-27.md`：ACT 收尾汇总 + π₀ dry-run 日志
- `notes/week2.md`：Week 2 计划 + π₀ vs ACT 架构对比
- `scripts/train_pi0_so101.sh` 或 `slurm/pi0_finetune.slurm`
- Commit：`notes(day10): wrap ACT eval, scaffold pi0 finetune`

---

## 💪 一句话激励

**Week 2 第一天就把 π₀ 跑出 1 个 forward pass —— 你离"银河通用面试桌上能掏出来的真机视频"只剩 1 周。**
