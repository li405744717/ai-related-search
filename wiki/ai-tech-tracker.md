# AI 技术追踪 Wiki

> 本文件随每日日报自动更新，记录各技术领域的演进时间线，用于回溯和趋势分析。

---

## Agent 框架与编排基础设施

### 当前生态全景
| 项目 | 定位 | 成熟度 | 最近动态 |
|------|------|--------|----------|
| DeerFlow 2.0 | Super Agent Harness（字节跳动） | 生产级 | 2026-02 发布，47.3k stars |
| LangGraph | 通用 Agent 状态图编排（LangChain） | 成熟 | 持续更新中 |
| CrewAI | 多角色 Agent 协作框架 | 成熟 | 活跃开发 |
| AutoGen | 多 Agent 对话框架（Microsoft） | 成熟 | v0.4+ |
| OpenAI Agents SDK | OpenAI 官方 Agent 开发包 | 早期 | 2026 年发布 |
| Strands | AWS 开源 Agent 框架 | 早期 | 2026 年发布 |
| Smolagents | 轻量 Agent 框架（HuggingFace） | 成熟 | 持续更新 |
| Pydantic AI | 类型安全 Agent 框架 | 成长期 | 活跃开发 |
| Claude Workflows | 多子代理编排（Anthropic） | 生产级 | 2026-05 发布 |
| ECC | Agent 性能优化系统 | 新兴 | 2026-06-02 GitHub 1,533 stars/day |

### 时间线
- **2026-06-02**：ECC（Agent性能优化框架）登顶 GitHub Trending，1,533 stars/日。小红书上线 Red Skill 平台（Agent 能力下沉内容消费场景）。Claude Code 年化收入 25 亿美元。 — 来源：6/2 日报
- **2026-06-01**：NVIDIA 发布 Cosmos 3 全模态世界模型（含 Agent 编排能力）。 — 来源：6/1 日报
- **2026-05-31**：Claude Workflows 多子代理并行编排发布，支持百万行级代码迁移。 — 来源：5/31 日报

### 关键洞察
- Agent 赛道从"能做 demo"进入"生产级基础设施"阶段，标志：Claude Code 年化 25 亿美元变现
- 框架分层明确：编排层（DeerFlow/LangGraph）→ 运行时（沙箱/记忆）→ 优化层（ECC/Headroom）
- 内容平台开始原生集成 Agent（小红书 Red Skill），预示 Agent 分发将成为新流量入口

---

## LLM 上下文管理与压缩

### 当前生态全景
| 项目 | 定位 | 成熟度 | 最近动态 |
|------|------|--------|----------|
| Headroom | Agent 工具链上下文压缩层 | 新兴 | 2026-06-02 GitHub 1,265 stars/day |
| LLMLingua-2 | Prompt 压缩（Microsoft Research） | 学术 | 论文已发布 |
| Anthropic Prompt Caching | 服务端 KV cache 复用 | 生产级 | 已上线 |
| ContextCite | 上下文归因+选择性压缩（MIT） | 学术 | 论文阶段 |

### 时间线
- **2026-06-02**：Headroom 发布，实现 60-95% 无损压缩（GSM8K 准确率 0.870→0.870）。三大压缩器：SmartCrusher（JSON）、CodeCompressor（AST感知）、Kompress-base（HF模型）。 — 来源：6/2 日报

### 关键洞察
- 上下文压缩从"可选优化"变为"基础设施标配"——Agent 工具调用产生的 token 开销指数增长

---

## AI 安全攻防

### 当前生态全景
| 项目 | 定位 | 成熟度 | 最近动态 |
|------|------|--------|----------|
| Claude Security (Opus 4.8) | 代码库漏洞扫描产品 | 生产级 | 已发现 10,000+ 高危漏洞 |
| Project Glasswing | AI 防御联盟（Anthropic） | 扩展中 | 2026-06-02 扩至 150 家 |
| Claude Mythos Preview | 专用漏洞检测模型 | 受限访问 | 6-12个月内其他公司将追平 |

### 时间线
- **2026-06-02**：Glasswing 扩至 150 家组织（15+国家），覆盖电力/水利/医疗。Meta AI 客服机器人被社工攻击劫持 Instagram 头部账号（Confused Deputy 漏洞）。 — 来源：6/2 日报

### 关键洞察
- AI 安全进入"AI vs AI"阶段：防守方用 AI 扫描漏洞，攻击方用 AI 生成深伪视频绕过验证
- LLM 在高权限系统中的 Prompt Injection 问题仍无根本解法

---

## 开源大模型（MoE / 多模态）

### 当前生态全景
| 项目 | 定位 | 成熟度 | 最近动态 |
|------|------|--------|----------|
| Nemotron 3 Ultra | 550B MoE 开源模型（NVIDIA） | 发布 | 2026-06-01，55B 活跃 |
| MiniMax M3 | 多模态 Agent 模型（MiniMax） | 发布 | 2026-06-01，100T 训练数据 |
| Qwen3.7-Plus | 多模态 Agent 模型（阿里） | 发布 | 2026-06-02 |
| NVIDIA Cosmos 3 | 全模态世界模型（开源） | 发布 | 2026-06-01 |
| VoxCPM2 | 无分词器 TTS（OpenBMB） | 开源 | 2026-06-02，30语言 |
| DeepSeek V4 | MoE 模型（~3%激活率） | 生产级 | 持续运营 |

### 时间线
- **2026-06-02**：Qwen3.7-Plus 发布（屏幕理解超 GPT-5.4）。VoxCPM2 开源（20B，无分词器 TTS，WER 1.84%）。 — 来源：6/2 日报
- **2026-06-01**：Nemotron 3 Ultra 550B 开源（10%稀疏率）。MiniMax M3 发布（MSA架构，1M上下文）。NVIDIA Cosmos 3 全模态世界模型开源。 — 来源：6/1 日报
- **2026-05-31**：Step 3.7 Flash（阶跃星辰 MoE）。AlphaEvolve（进化+LLM代码生成）。 — 来源：5/31 日报

### 关键洞察
- MoE 稀疏率成为新竞争轴：NVIDIA 10% vs DeepSeek ~3%
- 语音合成经历"大模型化"：拼接式→端到端神经→连续潜空间生成

---

## AI 平台化与商业模式

### 当前生态全景
| 项目 | 定位 | 成熟度 | 最近动态 |
|------|------|--------|----------|
| OpenAI Codex | 全能工作平台（62款插件） | 生产级 | 2026-06-02，周活 500 万 |
| Amazon Bedrock | 多模型统一治理云服务 | 生产级 | 2026-06-02 上线 OpenAI 模型 |
| Claude Workflows | 企业 Agent 编排 | 生产级 | 年化 25 亿美元 |
| OpenRouter | 多模型路由平台 | 独角兽 | $1.3B 估值 |

### 时间线
- **2026-06-02**：OpenAI Codex 发布 62 款角色插件（非开发者增速 3x）。OpenAI 模型登陆 AWS Bedrock（GPT-5.5/5.4/Codex）。Alphabet 800 亿融资 + 巴菲特 100 亿。Anthropic 秘密提交 S-1。 — 来源：6/2 日报
- **2026-06-01**：NVIDIA RTX Spark AI PC 芯片发布，Vera Rubin 推理基础设施平台。 — 来源：6/1 日报
- **2026-05-31**：Anthropic IPO 传闻首次出现。 — 来源：5/31 日报

### 关键洞察
- 竞争从"谁的模型强"转向"谁的平台生态完整"
- 多云分发成为默认（OpenAI on Bedrock），模型不再是壁垒，分发/合规才是
- AI 算力供给方确定性盈利，需求方（OpenAI/Anthropic）仍在亏损——"铲子 vs 淘金者"叙事持续

---

## AI 算力基础设施

### 时间线
- **2026-06-02**：Alphabet 启动 800 亿美元融资（伯克希尔 100 亿私募配售）。2026 资本开支 1800-1900 亿。Google Cloud 订单积压超 4600 亿。 — 来源：6/2 日报
- **2026-06-01**：NVIDIA Vera Rubin 架构发布。RTX Spark PC 芯片。Jetson Thor 具身智能芯片。 — 来源：6/1 日报

---

*最后更新：2026-06-03*
