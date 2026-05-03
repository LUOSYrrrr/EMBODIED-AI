# 📋 今日任务 — Day 17 / Week 3

> **时间戳**：2026-05-04（周一 AEST）
> **进度**：Day 17 / 56 · Week 3 / 8
> **距离 06-07 投递日**：还有 **34 天**
> **v3.0 主线**：SO-101 真机 π₀ 微调 + demo（M3）
> **时间预算**：3-4 小时（工作日强度）

---

## 🎯 核心任务（必做）

承接 Day 5 (04-22) ACT pipeline 首通，Week 3 进入 v3.0 流水线第 3 步：**SO-101 数据微调 π₀ → 真机首跑**。今天先把"权重就位 + 配置对齐 + 单步前向"打通，明后两天再上微调。

- [ ] **A. ACT eval 收尾 & 数据沉淀**（1h）
  - 把 04-22 之后的 ACT 真机推理结果（成功率、失败模式）补一份到 `notes/daily/2026-05-04.md`
  - 如果还没录 → 今天补 1 条 10 秒 demo 视频 → `demos/act_so101_eval.mp4`
  - 12 天的执行 gap 必须落账，否则 Week 3 复盘没有数据点

- [ ] **B. π₀ 权重 + 配置对齐**（1.5h）
  - `huggingface-cli download lerobot/pi0 --local-dir ~/embodied-ai/lerobot/weights/pi0`（如已下完跳过）
  - 用 `LUOSYrrrrr/so101_pickplace_v1` 数据集对照 `lerobot/configs/policy/pi0.py`：
    - `input_features.observation.state` 维度 = SO-101 6 关节 ✓
    - `input_features.observation.images.{top,wrist}` shape 对齐
    - `output_features.action` 维度 = 6
  - 跑一次 **dry-run**（`--steps=1` 或 `policy.forward()` 单帧）验证能加载、能前向，**不训练**

- [ ] **C. 显存 / Spartan 决策**（0.5-1h）
  - 4070 Ti Super 16GB 跑 π₀ batch=1 看峰值显存
  - 如 >14GB → 今天就把 Spartan 提交脚本 (`punim2341`) 写好，明天直接 `sbatch`
  - 把决策记进 `daily/2026-05-04.md`：本地 / Spartan / 混合

## ⭐ 加速版彩蛋（A/B/C 全清完再做）

- [ ] 在 `resume_assets.md` 项目 2 加一行：「ACT baseline N% 成功率 / 50 trajectories」（N 用今天补录的真实数字）
- [ ] `notes/week1.md` 末尾追加 **π₀ flow matching vs diffusion 3 句话**（Week 8 面试题预存）

## 🦿 Locomotion 穿插

**今日跳过**。Week 3 在 v3.0 pivot 后辅线全部后挪，且周一非周末。

---

## 💻 命令速查

```bash
conda activate lerobot
cd ~/embodied-ai/lerobot

# π₀ 权重下载（~10GB）
huggingface-cli download lerobot/pi0 --local-dir ./weights/pi0

# π₀ dry-run（按实际 script 名调整，先不训练）
python -c "
from lerobot.common.policies.pi0.modeling_pi0 import PI0Policy
import torch
p = PI0Policy.from_pretrained('./weights/pi0').cuda().eval()
print(p.config.input_features)
print(p.config.output_features)
"

# 显存监控
watch -n 1 nvidia-smi
```

---

## ⚠️ 风险提醒

1. **12 天日志真空**（Day 5 → Day 17）：今天先补 ACT eval 结果，否则 Week 3 周日复盘无据可写
2. **π₀ 配置维度极易错位**：SO-101 是 6 自由度 + 2 相机，π₀ 默认是 7 自由度 ALOHA 配置 → 大概率要写 SO-101 专属 config
3. **不要今天就启动微调**：今天目标是"加载 + 单步前向"，微调是 Day 18-19 的事
4. **HF 用户名拼写陷阱**：HF 是 `LUOSYrrrrr`（5 r），git 是 `LUOSYrrrr`（4 r），别又 403
5. **每 3 天反思暂停**：Day 15 (05-02) 已错过 → 明天 Day 18 是新的 3 日节点，今晚收工花 5 分钟想"v3.0 pivot 12 天后是否仍正确"

---

## 📦 今日产出

- `notes/daily/2026-05-04.md`：ACT eval 数字 + π₀ 加载日志 + Spartan 决策
- `~/embodied-ai/lerobot/weights/pi0/`：π₀ 权重就位
- `demos/act_so101_eval.mp4`（如缺）：真机 ACT 评估视频
- Commit：`notes(day17): pi0 weights ready + ACT eval backfill`

---

## 💪 一句话激励

**34 天到投递 — 今天把 π₀ 加载从"想做"变成"跑过一次前向"，简历素材的第二根支柱就立起来了。**
