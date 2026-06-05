# Agent 框架与编排基础设施

> 追踪 AI Agent 开发框架、编排协议、运行时基础设施的演进。

---

## 当前生态全景（截至 2026-06）

| 项目 | 定位 | 公司/社区 | 成熟度 | 许可证 |
|------|------|-----------|--------|--------|
| LangGraph v1.1 | 通用 Agent 状态图编排 | LangChain | 生产级 | MIT |
| DeerFlow 2.0 | Super Agent Harness | 字节跳动 | 生产级 | MIT |
| CrewAI v1.14+ | 多角色 Agent 协作 | CrewAI | 生产级 | Apache 2.0 |
| Claude Managed Agents | 托管式 Agent 运行时 | Anthropic | 生产级 | 商业 |
| OpenAI Agents SDK | 官方 Agent 开发包 | OpenAI | 生产级 | — |
| Strands 1.0 | AWS 原生 Agent 框架 | AWS | GA | Apache 2.0 |
| AutoGen → MS Agent Framework | 多 Agent 对话（维护模式） | Microsoft | 维护中 | MIT |
| Smolagents | 轻量 code-first Agent | HuggingFace | 成熟 | Apache 2.0 |
| Pydantic AI | 类型安全 Agent 框架 | Pydantic | 成熟 | MIT |
| Mastra | TypeScript-first Agent | Gatsby 团队 | 成长期 | MIT |
| Google ADK | Agent Development Kit | Google | 成长期 | Apache 2.0 |

### 协议标准

| 协议 | 用途 | 状态 |
|------|------|------|
| MCP (Model Context Protocol) | Agent ↔ 工具连接（"AI 的 USB-C"） | 行业标准，150+ CVE 暴露安全挑战 |
| A2A (Agent-to-Agent) | Agent 间通信 | 150+ 组织加入，Linux Foundation 托管 |

---

## 月度时间线

### 2026年1月
- **[新加坡政府] 发布全球首个 Agentic AI 治理框架**（1/22）— 在达沃斯世界经济论坛发布，为 Agent 系统监管提供首个国际参考标准
- **[MCP] "USB-C for AI" 共识形成**（1/20）— 行业文章普遍将 Model Context Protocol 类比为"AI 的 USB-C"，标志工具连接标准化
- **[Pydantic AI / Smolagents] 进入生产级**— 多篇框架评测将两者列为 2026 顶级框架，"type-safe agent" 和 "code-first agent" 范式获主流认可
- **[Cursor] Multi-Agent Orchestration 模式初现**— 社区开始利用 Background Agents 实现多专业化 Agent 协同
- **[Mastra] TypeScript 原生 Agent 框架崛起**— 来自 Gatsby 团队，内置 workflows、RAG pipelines、observability

### 2026年2月
- **[DeerFlow v1.0] 字节跳动开源**— MIT 许可，模块化多 Agent 深度研究框架，基于 LangGraph 构建
- **[OpenAI Codex] 桌面应用发布**（2/2）— macOS 版，从云端助手转型为本地多 Agent 工作台
- **[Cursor] 长时运行 Agent 研究预览**（2/12）— Agent 可在云端持续运行复杂任务
- **[Claude Agent SDK] 更名与升级**— 从 Claude Code SDK 升级为 Claude Agent SDK，支持远程 HTTPS 中继
- **[Windsurf] Wave 13：Multi-Agent Sessions**— 多 AI Agent 并发处理同一项目
- **[MCP] Streamable HTTP + OAuth 2.1 规范推进**— 解决远程 MCP Server 安全与扩展性
- **[Google ADK] 重定位为"Agent 执行框架"**（2/27）

### 2026年3月
- **[LangGraph v1.1] 正式发布**— type-safe streaming/invoke、Pydantic 自动转换，强化类型安全
- **[OpenAI Agents SDK + Temporal] 集成 GA**（3/23）— 持久执行 + 故障恢复
- **[DeerFlow 2.0] 升级为 Super Agent Harness**— Lead Agent 动态生成子 Agent（隔离上下文、独立工具/目标），被称为"AI Workers 的 Docker"
- **[A2A Protocol] 快速增长**— CrewAI 一等公民支持，LangGraph/ADK 推出适配器
- **[MCP 安全危机] 60天30个CVE**— 包括 CVE-2026-26118（工具劫持，CVSS 8.8）
- **[LangChain 供应链安全事件]**（3/26-27）— 3 个关键漏洞，引发框架安全广泛关注
- **[AWS Strands] 选型指南发布**（3/15）— 推荐 Strands + Bedrock AgentCore

### 2026年4月
- **[Claude Managed Agents] 公开测试版**（4/8）— 完全托管 Agent 运行时，被评为"2026最重要 Agent 基础设施发布"
- **[OpenAI Agents SDK] 沙箱执行重大更新**（4/15）— 原生沙箱、文件检查、命令执行、代码编辑
- **[OpenAI Codex] Computer Use 能力**（4/16）— Mac 控制，从代码工具扩展为通用 Agent 平台
- **[A2A Protocol] 超150个组织加入**（4/9）— Linux Foundation 宣布
- **[Microsoft] AutoGen → Agent Framework 迁移**（4/2）— AutoGen 进入维护模式
- **[Cursor 3] 发布**— 深度 Agent 能力 + Composer 重构

### 2026年5月
- **[LangChain Interrupt 2026]**（5/13-14）— 年度大会，主题"Agents at Enterprise Scale"
- **[Anthropic Code with Claude 2026]**（5/6-8）— 发布 Dreaming、Outcomes、Multi-Agent Orchestration、Claude Finance、Add-ins
- **[AWS Strands] TypeScript SDK 1.0 GA**（5/20）
- **[Windsurf] Cognition 整合后企业量10倍增长**
- **[Claude Managed Agents] 新增跨会话记忆**

### 2026年6月
- **[ECC] Agent 性能优化系统 GitHub Trending**（6/2，1,533 stars/day）
- **[小红书 Red Skill] 内容平台原生 Agent 分发**（6/1）
- **[Headroom] Agent 上下文压缩层**（6/2，1,265 stars/day）

---

## 关键洞察

1. **托管式 Agent 基础设施兴起** — Anthropic（Managed Agents）、OpenAI（Codex+沙箱）、AWS（Strands+AgentCore）均推出 Agent-as-a-Service
2. **协议双轨标准化** — MCP（工具连接）+ A2A（Agent 通信）形成互补，但 MCP 安全问题严峻（30+ CVE）
3. **框架整合与退役** — AutoGen→MS Agent Framework；Swarm→Agents SDK；Cognition 收购 Windsurf
4. **多 Agent 并行成为默认模式** — Cursor Background Agents、DeerFlow 动态子 Agent、Claude Multi-Agent
5. **Agent 商业验证** — Claude Code 年化 25 亿美元、Cursor ARR 20 亿美元，证明 Agent 产品可规模变现
6. **内容平台 Agent 化** — 小红书 Red Skill 代表 Agent 能力下沉到内容消费场景

---

*最后更新：2026-06-05*
