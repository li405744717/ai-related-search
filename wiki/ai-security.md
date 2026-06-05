# AI 安全攻防

> 追踪 AI 安全领域的攻防进展、政策法规、对齐研究、漏洞事件。

---

## 当前态势（截至 2026-06）

| 领域 | 关键玩家 | 状态 |
|------|----------|------|
| AI 防御扫描 | Anthropic (Claude Security / Glasswing) | 生产级，150+ 组织联盟 |
| MCP 安全 | 社区/CSA | 高危，30+ CVE in 60 days |
| AI 法规 | EU AI Act / 美国行政令 | 分阶段执行中 |
| 对齐研究 | Anthropic RSP v3.0 / OpenAI Preparedness | 迭代中 |
| 供应链安全 | HuggingFace / npm / PyPI | 攻击频发 |

---

## 月度时间线

### 2026年1月
- **[MIT Technology Review] 机械可解释性列为年度突破性技术** — Anthropic 开源 circuit tracing 工具集
- **[CrowdStrike] Agentic Tool Chain 攻击报告**（1/30）— 揭示 AI Agent 通过工具链被利用的三种攻击方式
- **[供应链] 训练数据投毒成为隐形威胁**（1/6）— TTMS 报告，多个开源模型被发现后门

### 2026年2月
- **[国际AI安全报告2026] 正式发布**（2/3）— Bletchley 峰会授权，综合评估通用 AI 风险
- **[Anthropic] RSP v3.0 发布**（2/24）— 更灵活的风险评估框架，引发争议（被批放弃部分承诺）
- **[OpenAI] 新任 Preparedness 负责人**（2/3）— 前 Anthropic 安全研究员，年薪 55.5 万美元
- **[英国] 深度伪造亲密图像入刑**（2/6）— 《数据使用与访问法案2025》第 138 条生效

### 2026年3月
- **[EU AI Act] 通用 AI 条款执法生效**（3/31）— 强制执行透明度和合规要求
- **[供应链攻击] Axios 和 LiteLLM 中招** — npm 包投毒，RAT 远程木马 + 凭证窃取
- **[MCP 安全危机] 60天内30个CVE** — CVE-2026-26118（工具劫持，CVSS 8.8）、CVE-2026-33032（MCPwn）
- **[Anthropic] RSP 违规报告 + 反报复政策更新**（3/24）

### 2026年4月
- **[MCP] "AI供应链之母"漏洞**（4/15-20）— OX Security 披露系统性 RCE，影响整个 Agent 生态
- **[Anthropic] Automated Alignment Researchers**（4/14）— 用 LLM 自动进行对齐研究
- **[CSA] MCP 安全危机研究报告** — 系统分析 Agent 基础设施设计缺陷
- **[NTIRE 2026] 深度伪造检测挑战赛**（CVPR 联合赛道）

### 2026年5月
- **[HuggingFace] 恶意模型冒充 OpenAI** — 18 小时 24.4 万次下载，登趋势榜首位
- **[HuggingFace] tokenizer 劫持漏洞** — tokenizer 库文件可被篡改劫持模型输出
- **[EU AI Act] 调整延期** — 减少规则重叠，延长高风险 AI 合规截止日期（5/13）
- **[OpenAI] 约 200 人从事安全工作**（5/12），招聘应对"自我训练 AI"风险研究员（5/23）
- **[CVE-2026-32211] Azure DevOps MCP 缺少认证**（CVSS 9.1）

### 2026年6月
- **[Anthropic] Glasswing 扩至 150 家组织**（6/2）— 覆盖电力/水利/医疗/通信，15+ 国家
- **[Meta AI] 客服机器人被社工攻破**（6/2）— Confused Deputy 漏洞，劫持奥巴马白宫等 Instagram 账号
- **[美国] 特朗普签署 AI 安全行政令**（6/2）— 自愿提交模型进行网络安全测试

---

## 关键洞察

1. **MCP/Agent 安全成为最大风险面** — 30+ CVE in 60 days，Agent 工具链是新的攻击面
2. **供应链攻击全面升级** — 从 npm/PyPI 扩展至模型仓库投毒，覆盖数据→模型→工具全链路
3. **AI 安全进入"AI vs AI"** — 防守方用 AI 扫漏洞（Glasswing），攻击方用 AI 生成深伪绕验证
4. **Prompt Injection 仍无根本解法** — Meta AI 事件证明 LLM 无法可靠区分指令 vs 数据
5. **法规分化** — EU 强制执行但面临实施困难；美国从强制转向自愿审查
6. **RSP 争议** — Anthropic v3.0 被部分安全社区批评放宽承诺

---

*最后更新：2026-06-05*
