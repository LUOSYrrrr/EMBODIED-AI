# 📋 今日任务 — Day 12 / Week 2

> **时间戳**：2026-04-29（周三 AEST）
> **进度**：Day 12 / 56 · Week 2 / 8
> **距离 06-07 投递日**：还有 **39 天**
> **主线**：SO-101 真机 π₀ / π₀.₅ 复现（v3.0 pivot）
> **时间预算**：4-5 小时
> **🔄 反思暂停日**（每 3 天一次）— 收工前必做

---

## 🎯 核心任务（必做）

承接 Day 5 的 ACT 真机评估 + π₀ 权重就位（若 04-22 ~ 04-28 已完成则直接推进 π₀ 微调）。今日目标：**M2 ACT 真机推理验证收口** + **π₀ 微调脚本首跑**。

- [ ] **A. ACT 真机评估收口**（1.5h）
  - 跑满 20 条 rollout，统计成功率（M2 验收线 ≥ 50%）
  - 失败 case 分类：抓取偏移 / 夹爪时机 / 视角丢失 / 物体打滑
  - 结果表写入 `notes/daily/2026-04-29.md`
  - **若已达标**：跳过本项，直接进 B

- [ ] **B. π₀ 微调脚本配置 + 首跑**（2-2.5h）
  - 确认 `~/embodied-ai/lerobot/weights/pi0/` 权重完整
  - 用同一份 SO-101 数据集，跑 `lerobot/scripts/train.py policy=pi0`
  - 先跑 **100 step 冒烟测试**（确认 loss 下降 + 显存不爆 + 数据维度对齐）
  - 失败立刻准备 Spartan A100 提交脚本（4070 Ti Super 16GB 微调 π₀ 大概率不够）

- [ ] **C. 反思暂停（10 min）**（强制）
  - 过去 3 天最大阻塞是什么？（数据 / 算力 / 调试）
  - v3.0 pivot 是否仍然正确？需要再砍内容吗？
  - 写进 `notes/daily/2026-04-29.md` 末尾"反思"段

## ⭐ 加速版彩蛋（A+B 顺畅再做）

- [ ] 速读 π₀ 论文 §3 Method（Action Expert + Flow Matching），3 句话总结写进 `notes/week2.md`
- [ ] `resume_assets.md` 项目 2 加一行：`SO-101 ACT 真机评估，X 条 rollout，成功率 Y%`

## 🦿 Locomotion 穿插

**今日跳过**（周三非周末 + v3.0 主线优先）。

---

## 💻 命令速查

```bash
conda activate lerobot
cd ~/embodied-ai/lerobot

# ACT eval（继续昨日的 rollout）
python lerobot/scripts/eval.py \
    --policy.path=outputs/train/act_so101/checkpoints/last \
    --env.type=so101 \
    --eval.n_episodes=20

# π₀ 冒烟训练（100 step）
python lerobot/scripts/train.py \
    policy=pi0 \
    dataset_repo_id=LUOSYrrrr/so101_grasp \
    training.offline_steps=100 \
    training.batch_size=4

# Spartan 备用提交
ssh spartan "cd /data/projects/punim2341/embodied-ai && sbatch slurm/pi0_finetune.sh"

# 显存监控
watch -n 1 nvidia-smi
```

---

## ⚠️ 风险提醒

1. **π₀ 显存爆炸**：本地 16GB 大概率 OOM → batch_size=2 / 启用 gradient checkpointing / 切 Spartan
2. **数据集 schema 对齐**：π₀ 需要 language instruction 字段，ACT 数据可能没有 → 加默认 prompt（如 "pick the cube"）
3. **USB 权限**：`sudo chmod 666 /dev/ttyUSB0` 重启必做
4. **别陷入调参陷阱**：今天只验证"能跑通 + loss 下降"，刷点放到 Day 13-14
5. **反思别跳过**：Day 12 是反思日，10 分钟收口决定 Week 2 走向

---

## 📦 今日产出

- `notes/daily/2026-04-29.md`：ACT 成功率表 + π₀ 首跑日志 + 反思
- `~/embodied-ai/lerobot/outputs/train/pi0_so101/`：π₀ 微调首个 checkpoint（哪怕 100 step）
- Commit：`notes(day12): ACT eval close-out + pi0 first run + reflection`

---

## 💪 一句话激励

**距离投递只剩 39 天 —— 今天把 π₀ 第一行 loss 跑出来，简历的 "微调过 π₀" 就从想象变成事实。**
