# AI Related Search

AI 技术日报自动化系统 + 技术演进追踪 Wiki。

## 目录结构

```
├── skill/
│   └── SKILL.md              # AI 日报技能完整定义
├── wiki/
│   ├── ai-tech-tracker.md    # 技术追踪总览
│   ├── agent-frameworks.md   # Agent 框架与编排
│   ├── llm-models.md         # 开源大模型
│   ├── ai-security.md        # AI 安全攻防
│   ├── infra-compute.md      # 算力基础设施
│   ├── context-compression.md # 上下文压缩
│   └── platform-biz.md       # 平台化与商业模式
├── digests/
│   ├── 2026-05-31.md         # 每日日报纯文本摘要
│   ├── 2026-06-01.md
│   └── 2026-06-02.md
└── README.md
```

## 工作流

1. 每日自动生成 AI 深度日报（HTML）
2. 生成后提取技术要点，更新 `wiki/` 下对应领域文件
3. 生成当日摘要写入 `digests/`
4. Commit & Push 到本仓库

## 技术栈

- 数据源：smol.ai AINews、官方博客、GitHub Trending、X/Twitter、国内平台（B站/知乎/小红书/36氪等）
- 分析维度：原理、现有应用、落地用途、后续方向
- 输出：iOS glassmorphism 风格 HTML 日报 + 技术追踪 Wiki
