# 📋 今日任务 — Day 16 / Week 3

> **时间戳**：2026-05-03（周日 AEDT）
> **进度**：Day 16 / 56 · Week 3 / 8
> **距离 06-07 投递日**：还有 **35 天**
> **v3.0 主线**：SO-101 真机 π₀ 复现 — 流水线第 2-3 步
> **时间预算**：5-6 小时（周日全天主线）
> **⚠️ 状态预警**：Day 5（04-22）后无 daily 记录，今日先"对齐 + 恢复 momentum"

---

## 🎯 核心任务（必做）

主线流水线进度自查（先 30 分钟做这件事，再选下面 A/B）：

- [ ] **S0. 状态对齐（30 min）**
  - ACT checkpoint 跑完了吗？真机 eval 做了吗？(`outputs/train/act_so101/checkpoints/last` 在不在)
  - π₀ 权重下了吗？(`~/embodied-ai/lerobot/weights/pi0/` 是否存在)
  - 把结论写进 `notes/daily/2026-05-03.md` 顶部 3 行

**根据 S0 结果二选一：**

- [ ] **A. 如果 ACT eval 还没做** → 做 Day 5 的遗留任务（2-3h）
  - SO-101 接线冒烟测试（`sudo chmod 666 /dev/ttyUSB0`）
  - ACT eval 跑 10 条 rollout，记成功率（M2 验收线 ≥50%）
  - **录视频** `demos/act_so101_eval_day16.mp4`

- [ ] **B. 如果 ACT eval 已完成** → 推进到 π₀ 流水线（3-4h）
  - `huggingface-cli download lerobot/pi0 --local-dir ./weights/pi0`
  - 写最小 `pi0_load_test.py`：load weights + forward 1 步 + dump action shape
  - 显存 profile（4070 Ti Super 16GB 微调够不够，不够走 Spartan）

- [ ] **C. 流水线节点重排（30 min）**
  - master_plan v3.0 流水线第 3-5 步重新排进 Week 3-4 的具体日期
  - 写进 `progress.md` 的 Week 3 那一行

## ⭐ 加速版彩蛋（主线全部完成再做）

- [ ] `notes/week3.md` 起一个新文件，记 π₀ 架构 3 句话总结（VLM + Action Expert + Flow Matching）
- [ ] `resume_assets.md` 项目 2 状态从 ⏳ 改成"ACT pipeline 跑通 + π₀ 权重就位"

## 🦿 Locomotion 穿插（周末，本周可做）

主线如果有余量再碰：
- [ ] 任务 L4：B 站「二营长」Chapter 3（45 min，Isaac 相关）
- 主线吃紧 → **跳过**，不要分心

---

## 📅 本周复盘模板（周日特供）

> 写进 `notes/week3.md` 末尾，5-10 分钟搞定

```markdown
## Week 3 复盘（04-27 ~ 05-03）

### 实际完成
- [ ] ...

### 偏离计划的地方
- 计划：ROS 2 + SO-101 真机闭环
- 实际：v3.0 pivot 后改成 SO-101 + π₀ 真机
- 后果：ROS 2 暂缓（master_plan 已记录）

### 最大阻塞
-

### 最大收获
-

### Week 4 调整（05-04 ~ 05-10）
- π₀ 微调 + 真机 demo（M3）
- ROS 2 完全不做
- 简历素材卡更新 1 次
```

---

## 🛑 反思暂停（Day 15 已错过 → 今晚补）

过去 11 天为什么没写 daily？识别真实原因（任选）：
- [ ] 真在写代码，没时间记笔记 → 设个每晚 21:00 闹钟，5 分钟流水账即可
- [ ] 主线卡住没进展，不知道写什么 → 写"今天没动"也是数据
- [ ] 优先级飘了 → 重读 master_plan v3.0 "决策规则"那一段
- [ ] 其他：________

---

## 💻 命令速查

```bash
# 状态自查
ls ~/embodied-ai/lerobot/outputs/train/act_so101/checkpoints/ 2>/dev/null
ls ~/embodied-ai/lerobot/weights/pi0/ 2>/dev/null
nvidia-smi

# 接着干
conda activate lerobot
cd ~/embodied-ai/lerobot
sudo chmod 666 /dev/ttyUSB0  # 每次重启都要

# π₀ 权重（如果 S0 显示没下）
huggingface-cli login
huggingface-cli download lerobot/pi0 --local-dir ./weights/pi0
```

---

## ⚠️ 风险提醒

1. **35 天倒计时**：投递日已不到 5 周，Week 4 是 π₀ 真机冲刺，**今天落下的就是 Week 4 多出来的债**
2. **不要重新规划**：v3.0 已经收敛，今天动手就行，别再改路线
3. **π₀ 微调显存**：本地不够直接 Spartan，别在本机硬 OOM
4. **录视频是最高 ROI 的 30 秒**：哪怕 ACT 成功率 30% 也录一条，简历需要的是"能动"不是"完美"

---

## 📦 今日产出

- `notes/daily/2026-05-03.md`：状态对齐 + 当日工作日志
- `notes/week3.md`：周复盘 + π₀ 架构 3 句话（彩蛋）
- `progress.md`：Week 3 状态更新
- `demos/act_so101_eval_day16.mp4`（如果走 A 路线）
- Commit：`notes(day16): week3 review + pi0 pipeline kickoff`

---

## 💪 一句话激励

**11 天的空白不是失败，是数据 —— 今天写下第一行代码或第一个 commit，就把"中断"变成了"重启"。35 天还够 π₀ 真机 demo 翻盘。**
