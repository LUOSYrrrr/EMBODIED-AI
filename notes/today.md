# 📋 今日任务 — Day 8 / Week 2

> **时间戳**：2026-04-25（周六 AEST）
> **进度**：Day 8 / 56 · Week 2 / 8（Week 2 开启）
> **距离 06-07 投递日**：还有 **43 天**
> **主线**：SO-101 真机 π₀/π₀.₅ 复现（v3.0 pivot）
> **时间预算**：4-5 小时

---

## 🎯 核心任务（必做）

**A. ACT 真机推理验证 — M2 收官**（2-2.5h）
- [ ] USB 权限 + 双相机冒烟测试
- [ ] 跑 20 条 rollout，记录成功率（目标 ≥50%，Week 2 M2 验收线）
- [ ] **录视频**：`demos/act_so101_grasp_v1.mp4`（10 秒最佳 1 条）
- [ ] 失败模式归档到 `notes/daily/2026-04-25.md`（抓取抖动 / 夹爪时机 / 视角偏移）

**B. Week 1 复盘 + π₀ 微调脚本准备**（1.5h）
- [ ] 写 `notes/week1/review.md`：完成度 / 最大收获 / 最大坑 / Week 2 调整
- [ ] 检查 `~/embodied-ai/lerobot/weights/pi0/` 已就位
- [ ] 对齐 `configs/policy/pi0.yaml` 与 SO-101 observation/action 维度
- [ ] 起草微调命令草案（本地试 1 step；若 OOM 切 Spartan）

**C. Day 6 反思暂停**（30min）
- [ ] 过去 3 天最大阻塞是什么？
- [ ] v3.0 pivot 是否依然正确？
- [ ] ≤200 字写到 `notes/daily/2026-04-25.md` 末尾

## ⭐ 加速版彩蛋（主线顺畅再做）

- [ ] `resume_assets.md` 项目 2 加 "ACT 真机首轮 N% 成功率（20 条 rollout）"
- [ ] π₀ 架构 3 句话面试卡（VLM backbone + Action Expert + Flow Matching）写进 `notes/week1.md`

## 🦿 Locomotion 穿插

**今日跳过**（v3.0 pivot 后辅线全部后挪；周六也优先 M2 收官）。

---

## 💻 命令速查

```bash
conda activate lerobot
cd ~/embodied-ai/lerobot

# USB 权限（重启必做）
sudo chmod 666 /dev/ttyUSB0

# ACT eval（按实际 script 名调整）
python lerobot/scripts/eval.py \
    --policy.path=outputs/train/act_so101/checkpoints/last \
    --env.type=so101 \
    --eval.n_episodes=20

# π₀ 权重检查
ls -lh weights/pi0/

# π₀ 微调试跑 1 step（占位，参数按实际 config 写）
python lerobot/scripts/train.py \
    policy=pi0 \
    env=so101 \
    dataset_repo_id=你的用户名/so101_grasp \
    training.steps=1
```

---

## ⚠️ 风险提醒

1. **USB 权限**：每次重启 `sudo chmod 666 /dev/ttyUSB0`
2. **相机带宽冲突**：两路 USB 相机争带宽 → 分 USB 控制器或降 480p
3. **微调 OOM**：4070 Ti Super 16GB 大概率不够 π₀，提前打包 Spartan 提交脚本
4. **别提前进 SO-101 仿真**：v3.0 已后挪，Week 2 唯一目标 = π₀ 真机 demo
5. **Day 6 反思必须做**：上次反思 Day 5 已合并 Day 3，今日是新的 3 天节点

---

## 📦 今日产出

- `notes/daily/2026-04-25.md`：M2 评估结果 + 失败案例 + Day 6 反思
- `notes/week1/review.md`：Week 1 完整复盘
- `demos/act_so101_grasp_v1.mp4`：M2 验收视频
- Commit：`notes(day8): ACT M2 eval + week1 review`

---

## 💪 一句话激励

**Week 2 第一天就是 M2 收官战 — 把 ACT 真机视频钉死，下周直奔 π₀ 微调。简历素材的第一颗钉子，今天敲进去。**
