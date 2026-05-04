# 📋 今日任务 — Day 18 / Week 3

> **时间戳**：2026-05-05（周二 AEST，墨尔本时区）
> **进度**：Day 18 / 56 · Week 3 / 8
> **距离 06-07 投递日**：还有 **33 天**
> **v3.0 主线**：SO-101 真机 π₀ / π₀.₅ 复现
> **本周里程碑**：🎯 **M3 — π₀ 微调 + 真机 demo**（Week 3 末验收）
> **时间预算**：4-5 小时
> **🪞 反思暂停日**（每 3 天触发一次）

---

## 🎯 核心任务（必做）

按 v3.0 流水线第 3-4 步推进。前提假设：M2（ACT 真机 ≥50%）已在 Week 2 末打卡；π₀ 权重已下载。如未达，先补 M2 再说。

- [ ] **A. π₀ 微调跑起来**（2.5h，本日重头戏）
  - 数据复用 Week 1 那批 SO-101 抓取数据集（≥50 条）
  - 本地 4070 Ti Super 显存够则本地跑；不够立刻切 Spartan A100
  - 参数起手：`policy=pi0`，`batch_size=8`，`steps=20000`，混合精度 bf16
  - 监控 loss 曲线 + 显存占用，**前 2000 步必须 loss 下降**否则停训查 config

- [ ] **B. 真机推理脚手架**（1h，并行做）
  - `lerobot/scripts/eval.py` 写好 π₀ 推理路径：`policy.path=outputs/train/pi0_so101/checkpoints/last`
  - SO-101 双相机 + 舵机冒烟测试（`sudo chmod 666 /dev/ttyUSB0`）
  - **不要等微调结束才接线**，今天把推理链路先拉通

- [ ] **C. 🪞 反思暂停（Day 18，0.5h）**
  - 写进 `notes/daily/2026-05-05.md`，回答 3 题：
    1. 过去 3 天主线推进了几步？是否仍在 v3.0 节奏上？
    2. ACT 真机成功率到了多少？π₀ 是否真的能拉开差距（写假设）？
    3. 距离投递只剩 33 天，**最该砍掉的一件事**是什么？

## ⭐ 加速版彩蛋（主线顺畅再做）

- [ ] π₀.₅ config 预读：对比 `pi05` vs `pi0` 训练时长 / attention mask 差异，3 句话写进 `notes/week3.md`（Week 4 直接用）
- [ ] 在 `resume_assets.md` 项目 2 加 "π₀ fine-tuning launched on SO-101 real-world dataset"

## 🦿 Locomotion 穿插

**今日跳过**（周二非周末 + v3.0 pivot 后辅线全部后挪，Week 3 仍主线优先）。

---

## 💻 命令速查

```bash
conda activate lerobot
cd ~/embodied-ai/lerobot

# π₀ 微调（本地）
python lerobot/scripts/train.py \
    policy=pi0 \
    env=so101 \
    dataset_repo_id=<你的用户名>/so101_grasp \
    training.batch_size=8 \
    training.offline_steps=20000 \
    training.save_freq=2000

# 显存不够 → Spartan A100
sbatch ~/embodied-ai/scripts/spartan_pi0_train.sh

# 真机推理（微调出第一个 checkpoint 后）
python lerobot/scripts/eval.py \
    --policy.path=outputs/train/pi0_so101/checkpoints/last \
    --env.type=so101 \
    --eval.n_episodes=10

# 监控
watch -n 1 nvidia-smi
tensorboard --logdir outputs/train/pi0_so101
```

---

## ⚠️ 风险提醒

1. **π₀ 显存**：4070 Ti Super 16GB 大概率不够 batch_size=8；OOM 立刻 → batch=2 + grad accumulation，或直接上 Spartan
2. **数据集格式**：π₀ 期待的 obs/action key 与 ACT 不同，跑前 `dry-run 1 step` 验证
3. **真机不要边训边跑**：训练时 GPU 占满，推理会抢资源 → 推理用 CPU 模式或晚上换班
4. **33 天倒计时**：Week 4 才是 π₀ 冲刺周，本周如果 π₀ 跑不通就**砍掉 π₀.₅ 对比**直接锁 π₀
5. **反思暂停别跳过**：Day 5 那次帮你做了 v3.0 pivot，今天可能又是一个决策窗

---

## 📦 今日产出

- `notes/daily/2026-05-05.md`：π₀ 微调启动日志 + 反思 3 答 + 踩坑
- `outputs/train/pi0_so101/checkpoints/`：至少 1 个早期 checkpoint
- TensorBoard 截图：π₀ loss 前 2000 步曲线
- Commit：`notes(day18): kick off pi0 fine-tuning + reflection pause`

---

## 💪 一句话激励

**Week 3 的 π₀ 微调跑通就意味着 M3 提前一周达成，Week 4 全用来打磨 demo 视频 —— 这就是把"投递时手里有牌"的安全感攒出来。**
