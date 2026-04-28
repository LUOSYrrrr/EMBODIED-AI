# 📋 今日任务 — Day 11 / Week 2

> **时间戳**：2026-04-28（周二 AEST）
> **进度**：Day 11 / 56 · Week 2 / 8
> **距离 06-07 投递日**：还有 **40 天**
> **v3.0 pipeline 当前位置**：Step 2-3（ACT 真机评估收尾 → π₀ 微调启动）
> **时间预算**：4-5 小时
> **⚠️ 缺口提醒**：04-23 ~ 04-27 共 5 天无 daily note，先 5 分钟回填关键节点再开工

---

## 🎯 核心任务（必做）

- [ ] **A. ACT 真机推理收尾（M2 验收，1.5h）**
  - 04-22 启动的 80k ACT checkpoint 若已收敛但未真机测：跑 10 条 rollout，记成功率
  - 已测过：直接把数字填进 `resume_assets.md` 项目 2，跳到 B
  - **录视频**：`demos/act_so101_eval.mp4`（任一 1 条成功 rollout）

- [ ] **B. π₀ 权重就位 + 加载冒烟测（1.5h）**
  - `huggingface-cli download lerobot/pi0 --local-dir ~/embodied-ai/lerobot/weights/pi0`（~10GB）
  - 写最小脚本：load `lerobot/pi0` config + 前向 1 步（dummy obs），确认 SO-101 obs/action dim 对齐
  - OOM → 立刻评估 Spartan 提交方案，**不要硬扛**

- [ ] **C. π₀ 微调 sanity check（1-1.5h）**
  - 用 `LUOSYrrrrr/so101_pickplace_v1` 数据集，本地 batch=1 + grad_accum=8，跑 200 steps
  - 看 loss 是否下降；不降就排查 dataset adapter / action normalization

## ⭐ 加速版彩蛋（主线顺畅再做）

- [ ] π₀ 论文 §3 架构 200 字笔记进 `notes/week2.md`（VLM=PaliGemma + Action Expert + Flow Matching）— Week 8 面试必考

## 🦿 Locomotion

**跳过**（仅周末 + Week 4 暂停规则；周日补 L3）。

---

## 💻 命令速查

```bash
conda activate lerobot && cd ~/embodied-ai/lerobot

# π₀ 权重
huggingface-cli download lerobot/pi0 --local-dir ./weights/pi0

# π₀ 微调 sanity（200 steps）
python -m lerobot.scripts.train \
    --policy.type=pi0 \
    --policy.pretrained_path=lerobot/pi0 \
    --dataset.repo_id=LUOSYrrrrr/so101_pickplace_v1 \
    --batch_size=1 --steps=200 \
    --output_dir=outputs/pi0_so101_sanity

watch -n 1 nvidia-smi
```

---

## ⚠️ 风险提醒

1. **5 天进度断档**：先回填 04-23~04-27 在 `progress.md` 写一行（哪怕"未推进"也写）
2. **π₀ 16GB 显存边缘**：bf16 + batch=1 + grad_accum；OOM 直接转 Spartan 别浪费时间
3. **Day 12 = 下一次反思暂停**：今晚收工预留 10 分钟回顾"v3.0 pivot 6 天后是否还正确"
4. **40 天倒计时**：Week 4 才是 π₀ 真机 demo 周，今天必须把 sanity 跑通否则 Week 4 危险

---

## 📦 今日产出

- `notes/daily/2026-04-28.md`：进度断档复盘 + ACT 成功率 + π₀ sanity loss
- `demos/act_so101_eval.mp4`（如未录）
- `~/embodied-ai/lerobot/weights/pi0/`：权重就位
- Commit：`notes(day11): ACT eval close + pi0 sanity check`

---

## 💪 一句话激励

**40 天能不能拿出 π₀ 真机视频，从今晚的 sanity loss 是否下降开始 — 别让 6 天断档变 7 天。**
