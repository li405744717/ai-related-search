# 开源大模型（MoE / 多模态）

> 追踪开源和半开源大语言模型的发布、架构演进、benchmark 表现。

---

## 当前生态全景（截至 2026-06）

| 模型 | 公司 | 参数（总/活跃） | 架构 | 许可证 | 发布时间 |
|------|------|-----------------|------|--------|----------|
| DeepSeek-V4-Pro | DeepSeek | 1.6T / 49B | MoE | MIT | 2026-04 |
| DeepSeek-V4-Flash | DeepSeek | 284B / 13B | MoE | MIT | 2026-04 |
| Nemotron 3 Ultra | NVIDIA | 550B / 55B | Mamba-Transformer MoE | 开源 | 2026-06 |
| Nemotron 3 Super | NVIDIA | 120B / 12B | Mamba-Transformer MoE | 开源 | 2026-03 |
| Qwen3.7-Plus | 阿里 | — | 多模态 MoE | Apache 2.0 | 2026-06 |
| Qwen3.5-397B | 阿里 | 397B / 17B | 多模态 MoE | Apache 2.0 | 2026-02 |
| GLM-5 | 智谱 | 744B / 40B | MoE | MIT | 2026-02 |
| MiniMax M3 | MiniMax | — | MSA (稀疏注意力) | 开放权重 | 2026-06 |
| Kimi K2.6 | 月之暗面 | 1T / 32B | MoE | Modified MIT | 2026-04 |
| Mistral Small 4 | Mistral | 119B / 6B | MoE | Apache 2.0 | 2026-03 |
| Gemma 4 | Google | 多规格(E2B/E4B/26B/31B) | MoE/Dense | Gemma License | 2026-04 |
| Cohere Command A+ | Cohere | 218B / 25B | MoE | Apache 2.0 | 2026-05 |
| VoxCPM2 | OpenBMB | 20B | 连续潜空间生成 | Apache 2.0 | 2026-06 |
| MAI-Thinking-1 | Microsoft | 1T / 35B | — | 商业 | 2026-06 |

---

## 月度时间线

### 2026年1月
- **[DeepSeek-V3.2-Speciale] (685B/37B)** — V3.2 推理增强版，专为 Agent 工作流设计，MIT 开源
- **[Qwen3-235B-A22B] (235B/22B)** — Qwen3 旗舰 MoE，混合推理（thinking/non-thinking），Apache 2.0
- **[Qwen3-Coder-Next] (80B/3B)** — 专业代码模型，256K 上下文，编码接近 Sonnet 4.5

### 2026年2月
- **[Qwen3.5-397B-A17B] (397B/17B)**（2/16）— 原生多模态视觉-语言 MoE，201 种语言，1M 上下文，Apache 2.0。"开源 AI 年"代表作
- **[GLM-5] (744B/40B)**（2/12）— 智谱开源，MIT 许可，33T tokens 预训练，幻觉率创历史新低
- **[MiniCPM5-1B] (1B)** — 端侧部署标杆，同规模顶尖性能
- **[MiniMax-M2.5]** — 达到前沿编码水平，"1 美元/小时的前沿模型"

### 2026年3月
- **[Nemotron 3 Super] (120B/12B)**（3/11）— 混合 Mamba-Transformer MoE，支持多 token 预测(MTP)，完全开源（权重+数据+配方）
- **[Mistral Small 4] (119B/6B)**（3/16）— 统一指令/推理/编码/多模态，Apache 2.0，256K 上下文
- **[Voxtral TTS] (~3B)**（3/26）— 开源 TTS，9 语言，超越 ElevenLabs

### 2026年4月
- **[DeepSeek-V4-Pro] (1.6T/49B) + V4-Flash (284B/13B)**（4/24）— 1M 上下文，33T 训练数据，性能对标顶级闭源
- **[Gemma 4] 多规格**（4/2）— 支持图像/视频/音频输入，面向推理和 Agent
- **[Kimi K2.6] (1T/32B)**（4/20）— 原生多模态 Agent 模型，长周期编码设计任务突出
- **[Meta Muse Spark]**（4/8）— Meta 首个完全闭源旗舰，标志从 Llama 开源路线转向。**非开源**
- **[Qwen3.6 系列]**（4/14-22）— MoE + Dense 双版本，专注 Agent 编码

### 2026年5月
- **[Cohere Command A+] (218B/25B)**（5/20）— Cohere 首个 MoE + 首个 Apache 2.0 完全开源模型，企业主权定位
- **[Qwen3.7]**（5/19）— "Agent 前沿"定位
- **[Nemotron 3 Ultra 预告]** — GTC Taipei 预告，550B/55B，NVIDIA 最大开源模型

### 2026年6月
- **[Nemotron 3 Ultra] (550B/55B)** — 正式发布，10% 稀疏率，推理 300+ tokens/s
- **[MiniMax M3]**（6/1）— MSA 架构，100T 训练数据，1M 上下文
- **[Qwen3.7-Plus]**（6/2）— 屏幕理解超 GPT-5.4，11 小时独立开发 App
- **[VoxCPM2] (20B)**（6/2）— 无分词器 TTS，30 语言，WER 1.84%，Apache 2.0

---

## 关键洞察

1. **MoE 成为绝对主流** — 几乎所有重大发布均为 MoE，典型配比 1T 总参/30-50B 活跃
2. **中国模型集中爆发** — 2 月 HuggingFace 榜单前 10 均为中国模型。DeepSeek/Qwen/GLM/Kimi/MiniMax 形成强大开源阵营
3. **Agent 化成为核心方向** — 模型设计从"对话"转向"长时 Agent 任务"
4. **Meta 战略转向** — Muse Spark 闭源标志 Meta 从 Llama 开源路线转向
5. **许可证开放趋势** — Apache 2.0 和 MIT 成为主流（Qwen/GLM/Mistral/Cohere）
6. **混合架构创新** — NVIDIA Mamba-Transformer MoE，结合 SSM 高效推理 + Transformer 表达力
7. **稀疏率竞争** — NVIDIA 10% vs DeepSeek ~3%，更低激活=更高推理效率但更难训练

---

*最后更新：2026-06-05*
