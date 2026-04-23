# 📋 今日任务 — Day 7 / Week 1（Week 1 收尾日）

> **时间戳**：2026-04-24（周五 AEST）
> **进度**：Day 7 / 56 · Week 1 / 8 最后一天
> **距离 06-07 投递日**：还有 **44 天**
> **主线**：SO-101 真机 π₀/π₀.₅ 复现（v3.0 pivot 第 3 天）
> **时间预算**：4-5 小时（Week 1 收尾 + Week 2 启动准备）

---

## 🎯 核心任务（必做）

Day 6 未留下笔记，今天先补齐 ACT 真机评估数据，再做 Week 1 复盘 + Week 2 冷启动。

- [ ] **A. ACT 真机评估成绩定版（90 min）**
  - 若 Day 6 的 10 条 rollout 未完成 → 今天补到 ≥10 条
  - 记录成功率（M2 验收线：≥50%）、失败模式（夹爪时机 / 视角 / 抖动）
  - **录视频**：`demos/act_so101_eval_final.mp4`（最佳 1 条 + 典型失败 1 条，各 ≤10s）
  - 成绩写进 `notes/daily/2026-04-23.md`（Day 6 补档）+ `notes/daily/2026-04-24.md`

- [ ] **B. Week 1 复盘（60 min）**
  - 新建 `notes/week1/review.md`，覆盖 5 项：
    1. M0 ✅ / M1（pivot 后 = SO-101 pipeline）✅ / M2 完成度
    2. v3.0 pivot 决策是否正确（凭 Day 5 的 11 个真机坑回答）
    3. 本周最大收获 1 条 + 最大阻塞 1 条
    4. Week 2 需调整的计划项
    5. 反思暂停合并：过去 3 天最关键的 1 个判断失误

- [ ] **C. π₀ 权重 smoke test（60 min）**
  - `huggingface-cli download lerobot/pi0 --local-dir ~/embodied-ai/lerobot/weights/pi0`（若 Day 5 未完成）
  - 写 10 行 Python：加载权重 + 1 次前向（不微调，不训练）
  - 4070 Ti Super 显存足够 → 继续本地；不够 → Spartan 提交脚本草稿

- [ ] **D. 简历素材 + GitHub 打磨（45 min）**
  - `resume_assets.md` 项目 2 加：`SO-101 真机 ACT baseline 50 traj / 成功率 XX% / HF 数据集已公开`
  - 仓库 README 嵌入 Day 5 数据集链接 + Day 7 demo 视频

## ⭐ 加速版彩蛋

- [ ] π₀ vs ACT 架构对比 200 字写进 `notes/week1/review.md`（Week 8 面试直接复用）
- [ ] Spartan `punim2341` 队列提交模板文件存 `~/embodied-ai/scripts/spartan_pi0_ft.slurm`（跑不跑先不管）

## 🦿 Locomotion 穿插

**跳过**：非周末 + v3.0 pivot 全辅线后挪。

---

## 💻 命令速查

```bash
# ACT eval（续跑）
conda activate lerobot
cd ~/embodied-ai/lerobot
python lerobot/scripts/eval.py \
    --policy.path=outputs/train/act_so101/checkpoints/last \
    --env.type=so101 --eval.n_episodes=10

# π₀ smoke test
huggingface-cli download lerobot/pi0 --local-dir ~/embodied-ai/lerobot/weights/pi0
python -c "from lerobot.common.policies.pi0 import Pi0Policy; p = Pi0Policy.from_pretrained('~/embodied-ai/lerobot/weights/pi0'); print(sum(x.numel() for x in p.parameters())/1e6, 'M')"

# 周复盘骨架
mkdir -p notes/week1 && cp notes/today.md notes/week1/review.md  # 再改
```

---

## ⚠️ 风险提醒

1. **Day 6 数据缺口**：若 ACT 成功率 <30%，Week 2 不要急着开 π₀，先排查 Day 5 数据集质量（工作空间胶带 / 相机视角）
2. **π₀ 权重 ~10GB**：网差挂 Spartan 后 rsync 回来
3. **Week 1 复盘不求完美**：45 分钟框架写完就收，Week 2 Day 8（明天）就要开工
4. **反思暂停欠账**：Day 6 漏记，今天必须在复盘里补一笔
5. **周五不是 review 的"赠送时间"**：Week 2 Day 8 = 周六 = SO-101 数据扩增起点，别把今天当周末

---

## 📦 今日产出

- `notes/daily/2026-04-23.md`：Day 6 补档（ACT eval 日志）
- `notes/daily/2026-04-24.md`：Day 7 当天记录
- `notes/week1/review.md`：Week 1 复盘
- `demos/act_so101_eval_final.mp4`：真机评估视频
- `resume_assets.md`：项目 2 更新
- Commit：`notes(week1): day7 review + ACT eval final + pi0 smoke test`

---

## 📊 Week 1 复盘模板（收工前 30 分钟填）

```markdown
# Week 1 Review（04-18 ~ 04-24）

## 完成度
- M0 Isaac Sim/Lab 环境：✅ Day 2 达成
- 原 M1 Franka Reach RL：❌ 因 Day 5 pivot 跳过
- 新 M1 SO-101 pipeline：✅ Day 5 达成（50 条数据 + ACT 训练启动）
- M2 ACT 真机评估：{✅/⚠️/❌} 成功率 {N}%

## 决策复盘：v3.0 pivot 是否值得
- 支持证据：
- 反对证据：
- 结论：

## 最大收获
-

## 最大阻塞
-

## Week 2 调整
- [ ] Day 8-9：数据扩增到 100 条（如 ACT 成功率 <50%）
- [ ] Day 10-11：π₀ 本地 / Spartan 微调
- [ ] Day 12-14：π₀ vs ACT 真机对比 + demo 合集预剪
```

---

## 💪 一句话激励

**Week 1 以 1 次 pivot + 11 个真机坑收尾 — 这正是简历里"踩过真机的人"和"只看过论文的人"之间的分水岭。Week 2 把 π₀ demo 拍到手。**
