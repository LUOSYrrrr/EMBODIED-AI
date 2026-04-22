# 📋 今日任务 — Day 6 / Week 1

> **时间戳**：2026-04-23（周四 AEST）
> **进度**：Day 6 / 56 · Week 1 / 8
> **距离 06-07 投递日**：还有 **45 天**
> **v3.0 pivot 第 2 天**：SO-101 真机 π₀/π₀.₅ 复现
> **时间预算**：4-5 小时
> **🔄 Day 6 反思暂停日**（Day 3 那次错过了,这次必须写）

---

## 🎯 核心任务（必做）

Day 5 夜里 ACT 挂训（80k steps / 2h36min / loss 7k 步已到 0.78），今晨起床直接接 eval。**M2 验收线：真机成功率 ≥50%**。

- [ ] **A. ACT 真机 eval 完整跑完**（2h）— 承接 Day 5 未完成的 rollout
  - [ ] checkpoint loss 曲线复盘（TensorBoard / WandB）
  - [ ] 物块 5 种起点 × 2 次 = **10 条 rollout**,记成功率
  - [ ] 🎯 **M2**：≥50% → 进 π₀；30-50% → 再采 20 条补数据；<30% → 回头查数据质量
  - [ ] 录视频：`demos/act_so101_eval_day6.mp4`（最佳 1 条 10s 内）

- [ ] **B. π₀ 权重落地 + 加载验证**（1-1.5h）— Day 5 B 项搬运
  - [ ] `huggingface-cli download lerobot/pi0 --local-dir ~/embodied-ai/lerobot/weights/pi0`
  - [ ] 脱机 `from lerobot.policies.pi0 import Pi0Policy` 能加载 + forward 1 步
  - [ ] 检查 `configs/policy/pi0.yaml` 的 obs/action 维度与 SO-101 对齐（6 joint × 2 arm + 2 cam）
  - [ ] 评估本地 16GB 显存够不够微调,不够就写 Spartan submit 脚本草稿

- [ ] **C. 🔄 反思暂停**（0.5h）— 写进 `notes/daily/2026-04-23.md`
  - [ ] pivot 3 天复盘：砍掉 Isaac Lab 仿真是否正确？
  - [ ] ACT → π₀ 节奏是否过激（跳过 Diffusion Policy 中间态）？
  - [ ] Week 2 前 3 天要不要重新排？
  - [ ] 有没有新的"把时间花在错误地方"的风险？

## ⭐ 加速版彩蛋（A 项 ≥50% 才解锁）

- [ ] π₀ 微调配置 dry-run：`configs/policy/pi0.yaml` 接 SO-101 dataset repo_id,只做配置不跑训
- [ ] `resume_assets.md` 项目 2 更新："ACT baseline 50 trajectories / 真机首轮 eval 成功率 X%"

## 🦿 Locomotion 穿插

**今日跳过**（周四非周末 + v3.0 pivot 辅线后挪）。

---

## 💻 命令速查

```bash
conda activate lerobot
cd ~/embodied-ai/lerobot

# USB 权限（每次重启都要,昨日坑 2）
sudo chmod 666 /dev/ttyACM0 /dev/ttyACM1 2>/dev/null || true

# ACT eval
python lerobot/scripts/eval.py \
    --policy.path=outputs/train/act_so101/checkpoints/last \
    --env.type=so101 \
    --eval.n_episodes=10

# π₀ 权重（~10GB）
huggingface-cli login   # 首次
huggingface-cli download lerobot/pi0 --local-dir ./weights/pi0

# π₀ 加载验证（Python REPL）
python -c "from lerobot.common.policies.pi0.modeling_pi0 import PI0Policy; print('ok')"

# 显存 / 温度监控
watch -n 1 nvidia-smi
```

---

## ⚠️ 风险提醒

1. **USB 权限**：`sudo chmod 666 /dev/ttyACM*`(昨日坑 2 记录,每次重启失效)
2. **π₀ 权重 ~10GB**：HF 下载慢就挂 Spartan 拉,再 rsync 回本地
3. **显存**：π₀ 微调显存预估 > 16GB → 本地只做加载验证,微调走 Spartan
4. **别急着微调**：今天只"能加载 + 能前向 1 步",微调放 Day 7-8
5. **反思暂停别跳**：Day 3 已经错过一次,这次 30 分钟硬挤也要写

---

## 📦 今日产出

- `notes/daily/2026-04-23.md`：ACT eval 成功率 + π₀ 加载日志 + 3 天 pivot 反思
- `demos/act_so101_eval_day6.mp4`：真机 rollout 首轮视频
- `~/embodied-ai/lerobot/weights/pi0/`：π₀ 权重就位
- Commit：`notes(day6): ACT real-robot eval + pi0 weights loaded + pivot reflection`

---

## 💪 一句话激励

**pivot 第 3 天,拍下那条 ≥50% 的 rollout,你就从"跑通脚本的学生"变成"能做实验的候选人"—— 这是简历上第一条能让 HR 停 3 秒的素材。**
