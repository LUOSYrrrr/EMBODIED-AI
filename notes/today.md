# 📋 今日任务 — Day 9 / Week 2

> **时间戳**：2026-04-26（周日 AEST）
> **进度**：Day 9 / 56 · Week 2 / 8
> **距离 06-07 投递日**：还有 **42 天**
> **主线**：SO-101 真机 π₀ 复现（v3.0 pivot）
> **时间预算**：5-6 小时（周日全天）

---

## 🎯 核心任务（必做）

- [ ] **A. ACT 真机评估收口**（1.5h）
  - 跑 20 条 rollout，按"物块起点 × 5 区"统计成功率
  - 写入 `notes/daily/2026-04-26.md`，达 ≥50% 即关 M2
  - **录视频**：`demos/act_so101_eval_final.mp4`（剪 30s 最佳 3 条）

- [ ] **B. π₀ 微调脚本上 Spartan**（2h）
  - 数据集 sanity check：`info.json` total_episodes 与 parquet 对齐
  - 写 `train_pi0.slurm`（A100×1, 8h, batch=8）
  - 提交后 `squeue -u $USER` 确认排队
  - 本地 4070 Ti Super 同时跑 π₀ **forward 1 步**冒烟测试

- [ ] **C. 反思暂停 + 周复盘**（1.5h, 周日特供）
  - 见下方模板，必填

## ⭐ 加速版彩蛋

- [ ] `lerobot/configs/policy/pi05.yaml` 与 `pi0.yaml` diff 阅读 30 分钟
- [ ] `resume_assets.md` 项目 2 加 ACT 真机成功率数字

## 🦿 Locomotion 穿插

**今日跳过**（v3.0 pivot 后辅线后挪）。

---

## 💻 命令速查

```bash
# Spartan 提交
ssh spartan
sbatch train_pi0.slurm && squeue -u $USER

# 本地 π₀ 冒烟
conda activate lerobot
python -c "from lerobot.policies.pi0 import PI0Policy; \
  m = PI0Policy.from_pretrained('lerobot/pi0'); print(m)"
```

---

## ⚠️ 风险提醒

1. **Spartan 排队**可能 6-12h，今晚必须提交，别拖到周一
2. **π₀ 显存**~22GB，本地只能 forward，**绝不本地微调**
3. ACT 成功率 <30% → 别急着上 π₀，先回查数据/训练

## 📦 今日产出

- `notes/daily/2026-04-26.md`、`demos/act_so101_eval_final.mp4`
- `train_pi0.slurm`（push 到仓库）
- Commit：`day9: ACT eval close + pi0 spartan submit + week2 review`

---

## 🔁 本周复盘模板（Week 2 = Day 8-14，本周才刚开始第 2 天，复盘 Week 1 + pivot）

| 维度 | 答 |
|---|---|
| Week 1 完成度 | M0 ✅ / M1 ✅（pivot 为 ACT pipeline） |
| 最大收获 | LeRobot CLI 11 坑全踩穿，真机 pipeline 稳了 |
| 最大阻塞 | URDF/Isaac Lab 路线没收益 → 已 pivot |
| Week 2 调整 | 砍 Isaac Lab，全力 π₀/π₀.₅ |

## 🪞 反思暂停（Day 9，每 3 天）

- 过去 3 天最值的事？最浪费的 1 小时？
- 距离 06-07 还有 42 天，简历视频素材进度条 = ?
- 一句话写到 `daily/2026-04-26.md`。

## 💪 一句话激励

**周日 = Week 2 节奏定型日。今晚把 Spartan 任务挂上，明早醒来你就比同期的所有候选人多 1 个 π₀ checkpoint。**
