# AI Related Search

AI 技术日报自动化系统 + 技术演进追踪 Wiki。

## 目录结构

```
├── skill/
│   └── SKILL.md                  # AI 日报技能完整定义
├── wiki/
│   ├── ai-tech-tracker.md        # 索引文件
│   ├── agent-frameworks.md       # Agent 框架与编排
│   ├── llm-models.md             # 开源大模型
│   ├── ai-security.md            # AI 安全攻防
│   ├── infra-compute.md          # 算力基础设施
│   └── platform-biz.md           # 平台化与商业模式
├── digests/
│   ├── 2026-05-31.md             # 每日日报纯文本摘要
│   ├── 2026-06-01.md
│   └── 2026-06-02.md
└── README.md
```

## 工作流

1. 每日自动生成 AI 深度日报（HTML，4 维度技术分析）
2. 生成后提取技术要点，更新 `wiki/` 下对应领域文件
3. 生成当日摘要写入 `digests/`
4. Commit & Push 到本仓库

## Wiki 覆盖时间线

- **2026年1月-5月**：基础 wiki（每月重大事件回顾）
- **2026年6月起**：每日自动追加

## 技术栈

- 数据源：smol.ai AINews、官方博客、GitHub Trending、X/Twitter、国内平台（B站/知乎/小红书/36氪等）
- 分析维度：原理、现有应用、落地用途、后续方向
- 输出：iOS glassmorphism 风格 HTML 日报 + 技术追踪 Wiki
- 推送：企业微信自动通知

## 5 大追踪领域

1. **Agent 框架** — LangGraph / DeerFlow / CrewAI / Claude Managed Agents / MCP / A2A
2. **开源大模型** — DeepSeek / Qwen / GLM / Nemotron / Mistral / MoE 架构
3. **AI 安全** — MCP 漏洞 / Prompt Injection / EU AI Act / 对齐研究
4. **算力基础设施** — NVIDIA / AMD / TPU / 推理框架 / 量化技术
5. **平台与商业** — OpenAI / Anthropic / 融资 / 定价 / 商业模式
