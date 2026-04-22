# 📋 今日任务 — Day 5 / Week 1

> **时间戳**：2026-04-22（周三 AEST）
> **进度**：Day 5 / 56 · Week 1 / 8
> **距离 06-07 投递日**：还有 **46 天**
> **v3.0 pivot 首日主线**：SO-101 真机 π₀/π₀.₅ 复现
> **时间预算**：4-5 小时

---

## 🎯 核心任务（必做）

昨夜 master_plan 已 pivot 到 v3.0。M1（ACT pipeline）✅ 达成，今日承接流水线第 2 步：**ACT 真机推理验证** + **π₀ 预训练权重预下载**。

- [ ] **A. ACT 真机推理测试**（2-2.5h）
  - 确认 ACT checkpoint 已收敛（看 loss 曲线 + TensorBoard）
  - 真机接线：SO-101 双相机 + 舵机 `/dev/ttyUSB0` 冒烟测试
  - `lerobot/scripts/control_robot.py record` 用 **policy eval 模式**跑 10 条 rollout
  - 记录成功率（目标 ≥ 40%，M2 验收线是 Day 6-7 达 50%）
  - **录视频**：`demos/act_so101_eval_day5.mp4`（10 秒内最佳 1 条）

- [ ] **B. π₀ 权重 + 环境预备**（1-1.5h）
  - `huggingface-cli login`（若未登录）
  - `huggingface-cli download lerobot/pi0 --local-dir ~/embodied-ai/lerobot/weights/pi0`
  - 检查 `lerobot` 源码 `configs/policy/pi0.yaml` 与 SO-101 observation/action 维度对齐
  - 评估本地 4070 Ti Super 显存是否够微调 → 不够就准备 Spartan 提交脚本

- [ ] **C. 失败案例归档**（0.5h）
  - ACT 跑崩的 rollout 写进 `notes/daily/2026-04-22.md`（抓取抖动？夹爪时机？视角偏移？）
  - 对照 π₀ flow matching 的优势假设 1-2 句话

## ⭐ 加速版彩蛋（主线顺畅再做）

- [ ] 在 `resume_assets.md` 更新项目 2：加上 "ACT baseline 50 trajectories / 真机首轮评估" 一行
- [ ] 简述 π₀ 架构（VLM backbone + Action Expert + Flow Matching）3 句话写进 `notes/week1.md`，Week 8 面试直接复用

## 🦿 Locomotion 穿插

**今日跳过**（周三非周末 + v3.0 pivot 后辅线全部后挪）。

---

## 💻 命令速查

```bash
conda activate lerobot
cd ~/embodied-ai/lerobot

# ACT eval（伪代码，按你实际 script 名调整）
python lerobot/scripts/eval.py \
    --policy.path=outputs/train/act_so101/checkpoints/last \
    --env.type=so101 \
    --eval.n_episodes=10

# π₀ 权重下载
huggingface-cli download lerobot/pi0 --local-dir ./weights/pi0

# 显存监控
watch -n 1 nvidia-smi
```

---

## ⚠️ 风险提醒

1. **USB 权限**：`sudo chmod 666 /dev/ttyUSB0`（每次重启都要）
2. **相机冲突**：两个 USB 相机争带宽 → 分 USB 控制器或降分辨率 480p
3. **π₀ 权重 ~10GB**：下载慢就挂 Spartan 拉取再 rsync 回本地
4. **别急着微调 π₀**：今天只做"能加载 + 能前向 1 步"验证，微调是 Day 6-7 的事
5. **Day 3 反思暂停已错过** → 合并到今晚收工写（"过去 3 天最大阻塞 + pivot 是否正确"）

---

## 📦 今日产出

- `notes/daily/2026-04-22.md`：踩坑 + ACT 成功率 + π₀ 加载日志
- `demos/act_so101_eval_day5.mp4`：首个真机评估视频
- `~/embodied-ai/lerobot/weights/pi0/`：π₀ 权重本地就位
- Commit：`notes(day5): ACT real-robot eval + pi0 weights ready`

---

## 💪 一句话激励

**pivot 后的第 1 天就是"让简历素材从零到一"的起跑枪 —— 拍下第一条 ACT 真机视频，你就有了跟银河通用 HR 开口的底气。**
