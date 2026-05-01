# 📋 今日任务 — Day 15 / Week 3

> **时间戳**：2026-05-02（周六 AEST）
> **进度**：Day 15 / 51 · Week 3 / 8
> **距离 06-07 投递日**：还有 **36 天**
> **v3.0 pivot 状态**：SO-101 真机 π₀/π₀.₅ 复现主线
> **今日特别**：🪞 **第 5 次反思暂停日**（每 3 天触发）+ Week 3 开周
> **时间预算**：5-6 小时（周末档）

---

## 🎯 核心任务（必做）

按 v3.0 流水线，Week 4（05-11）才进 π₀ 真机冲刺。本周（W3）必须把"数据 + 微调脚本 + Spartan 提交"三件事跑顺，否则 Week 4 起不来。

- [ ] **A. 数据集扩充到 100 条**（2h）
  - ACT 已用 50 条；π₀ 微调推荐 ≥100 条
  - `lerobot/scripts/control_robot.py record` 再补 50 条同任务轨迹
  - 加入 2-3 种物体位置 / 光照 variation（为面试聊"数据多样性"留素材）
  - 推 HuggingFace Hub：`lerobot/scripts/push_dataset_to_hub.py`

- [ ] **B. π₀ 前向 1 步 smoke test**（1.5h）
  - 加载 `~/embodied-ai/lerobot/weights/pi0` → 喂 1 帧 obs → 检查 action 维度
  - 显存峰值记录（决定本地 vs Spartan）
  - 输出对照 `lerobot/configs/policy/pi0.yaml` 写进 `notes/daily/2026-05-02.md`

- [ ] **C. Spartan 微调脚本骨架**（1h）
  - `slurm/pi0_finetune.sbatch`：A100 单卡 / 80G / 6h walltime
  - rsync 数据集 → punim2341；`huggingface-cli` 缓存路径设到 scratch
  - 不实际提交，今天只完成 dry-run

- [ ] **D. 🪞 反思暂停（30 分钟，今晚收工）**
  - Day 13-15 三天产出对账：ACT 真机成功率？π₀ 加载是否过坑？
  - 一句话答：**Week 4 冲刺起跑线还差什么？**
  - 写进 `notes/daily/2026-05-02.md` 末尾

## ⭐ 加速版彩蛋（主线顺畅再做）

- [ ] 简历 `resume_assets.md` 项目 2 加一行："数据集 100 traj / HF Hub 公开"
- [ ] 看一段 π₀ 论文 §4 Flow Matching 推导（10 分钟即可，面试题预热）

## 🦿 Locomotion 穿插

**v3.0 后已砍**。若主线全清且仍想做：限 30 分钟 — 翻 `notes/locomotion.md` 10 术语过一遍即可，不开新视频。

---

## 💻 命令速查

```bash
conda activate lerobot
cd ~/embodied-ai/lerobot

# 补录数据
python lerobot/scripts/control_robot.py record \
    --robot.type=so101 --control.type=teleoperate \
    --control.num_episodes=50 \
    --control.repo_id=LUOSYrrrr/so101_grasp_v2

# π₀ smoke test
python -c "from lerobot.common.policies.pi0 import PI0Policy; \
    p=PI0Policy.from_pretrained('./weights/pi0'); print(p)"

# 显存监控
watch -n 1 nvidia-smi
```

---

## ⚠️ 风险提醒

1. **USB 权限**：每次重启 `sudo chmod 666 /dev/ttyUSB0`
2. **π₀ 显存**：4070 Ti Super 16G 跑微调大概率 OOM → 早确认走 Spartan
3. **HF Hub 限速**：100 条数据上传可能 30min+，开始任务时先后台 push
4. **不要今天就启动 π₀ 微调**：脚本骨架就好，正式微调留到 Week 4 Day 22-23
5. **周六放纵警告**：不开新论文/新视频，一切围绕 Week 4 起跑线

---

## 📦 今日产出

- `notes/daily/2026-05-02.md`：数据扩充日志 + π₀ smoke test 输出 + 反思
- `~/embodied-ai/lerobot/datasets/so101_grasp_v2/`（100 条）
- `slurm/pi0_finetune.sbatch`（dry-run 通过）
- HF Hub 数据集 link
- Commit：`notes(day15): dataset to 100 + pi0 smoke + spartan skeleton`

---

## 💪 一句话激励

**距离投递 36 天 —— 今天每补一条数据，就是 Week 4 demo 视频里多 1% 的成功率。**
