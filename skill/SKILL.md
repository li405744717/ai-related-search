---
name: ai-daily-news
description: 生成 AI 动态日报（HTML 卡片格式）。当用户提到 AI 日报、AI daily、每日 AI 新闻、AI 动态、AI news digest、生成日报、今日 AI 速览、daily AI briefing 时触发。即使用户没有明确说"日报"，但只要涉及汇总当天/昨天的 AI 领域动态并以结构化的 HTML 卡片输出，也应使用本技能。同时也适用于用户想了解当天 AI 圈发生了什么、有什么大新闻、有什么论文或模型发布等场景——按日报的工作流搜给用户看，而不是零散地回答。
---

# AI 日报技能

生成以"昨天"为时间窗口的 AI 动态 HTML 日报。输出为结构化的卡片式 HTML 文件，包含左侧 sticky 导航、顶部高亮条、分类卡片、信源覆盖表。

## 工作流概览

```
Step 1: 确定时间边界（昨天）
Step 2: 三路并行调研（综合调研 + Twitter 专项 + 国内平台专项，各派一个 subagent）
Step 3: 等待 subagents 返回后整合去重
Step 4: 生成 HTML 文件（含完整样式）
Step 5: 提交文件 + 桌面通知
```

## 时间边界

- "昨天" = 当天日期减 1 天。先调 `current_status` 拿 `logical_date`，得到 today，算 yesterday = today - 1。
- 如果用户主动指定了日期（如"5/26 的日报"），以用户指定为准。
- 覆盖范围严格限定为 yesterday 这一天首次披露的内容，旧闻不收。

## 关注范围

### 核心层
- **基础模型**：OpenAI / Anthropic / Google / DeepMind / Meta / DeepSeek / Qwen / Mistral / xAI 等的新模型、版本、benchmark
- **本地 LLM 部署生态**：ollama、llama.cpp、vllm、sglang、LM Studio、MLX
- **Agent / Coding 工具**：Claude Code、Codex、Cursor、Devin、Aider、OpenHands、Windsurf
- **Agent 框架与编排基础设施**：DeerFlow、LangGraph、CrewAI、AutoGen、OpenAI Agents SDK、Strands（AWS）、Smolagents、Pydantic AI 等 Agent 开发框架的版本更新、架构变化、新功能发布；Agent 运行时能力（sandbox、memory、tool orchestration）的技术突破；以及相关的性能评测（如 SWE-Bench、MCP Atlas、Terminal Bench）
- **GitHub Trending**（当日新晋热门）
- **arXiv** 当日值得关注的论文（人工筛热度，非随机抽样）

### 应用层
- AI 在医疗、法律、设计、影视、教育、金融等垂直行业的落地案例
- 重要 AI 应用产品的发布或更新

### 国内平台层（B站 / 知乎 / 小红书 / 其他主流媒体）
- **B站**：AI 领域头部 UP 主的技术科普、实测评测、教程演示类视频；AI 工具实操、模型对比、开源项目体验等高播放量视频
- **知乎**：AI 相关高赞回答、热门讨论、专栏深度文章；关注"人工智能""大模型""ChatGPT""AI Agent"等话题下的热门内容
- **小红书**：AI 工具测评、效率提升攻略、AI 绘画/写作实操分享等爆款笔记
- **其他国内媒体**：36氪、虎嗅、极客公园、InfoQ中文、CSDN等平台的 AI 相关头条报道
- 时间窗口：**近3天内**发布的热门内容（与核心层/应用层的"仅昨天"不同）

## 执行流程

### Step 1: 确定时间

用 `current_status(action="get", key="time")` 获取当前时间，计算 yesterday。

### Step 2: 派三个 subagent 并行调研

三个 subagent **必须同时发起**，不要串行。每个 subagent 的 task 参数里要放完整的调研指令。

**subagent A（综合调研）**：
```
任务：调研 [yesterday] 全球 AI 领域动态。

信息源（显式访问，不要只靠 web_search）：
1. smol.ai AINews 当日 issue（https://news.smol.ai/）—— 最稳定、最高优先级的信源
2. Anthropic / OpenAI / Google DeepMind / Meta AI 官方博客 release 页
3. GitHub Trending（https://github.com/trending）daily AI 相关
4. 机器之心 / 量子位 / 新智元
5. arXiv cs.AI / cs.CL 当日新提交（人工筛 3-5 篇高热度）
6. VentureBeat / The Decoder / Digg.com AI 等英文 AI 媒体

要求：每条必须附原文 URL、信源标注、时间核对（必须是 [yesterday]）、一句话中文摘要 + 一句话价值说明。
权限：只读，不修改文件。
```

**subagent B（Twitter 专项）**：
```
任务：专项调研 [yesterday] 在 X/Twitter 上 AI 圈一手资料。

重点账号：@karpathy、@sama、@AnthropicAI、@elonmusk、@ylecun、@JeffDean、@_jasonwei、@swyx、@simonw、@dotey、@teortaxesTex、@rasbt、@_sholtodouglas、@SebastienBubeck、@vllm_project、@OpenRouter、@mustafasuleyman、@ClaudeDevs、@SakanaAILabs

抓取方式：web_search "<account> tweet <date>"、web_fetch X 公开 URL、读 smol.ai AINews issue 里的 X 摘录、读 Digg.com / The Decoder 等媒体引文。

要求：每条必须真实有出处，抓不到就如实说"该信源未拿到"，绝对不要编造推文内容。
权限：只读，不修改文件。
```

**subagent C（国内平台专项：B站 + 知乎 + 小红书 + 其他媒体）**：
```
任务：专项调研近 3 天内（[yesterday-2] 至 [yesterday]）国内主流平台上 AI 领域的热门内容。

⚠️ 时间窗口：近 3 天（含昨天及前两天），比其他 subagent 更宽，目的是捕捉国内平台发酵较慢但热度正在攀升的内容。

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
【平台 1：哔哩哔哩（Bilibili）】

重点关注 UP 主：
- 技术科普类：稚晖君、林亦LYi、跟李沐学AI、二次元的Zhangzhe、秋葉aaaki、Koala聊开源
- AI 工具实测类：花儿不哭、阿Test正经比比、AI工具集、就叫木头人吧
- 开发者向：代码真香、Andrej Karpathy中文、极客湾Geekerwan
- AI 热点讨论：差评、量子位、机器之心官方号

搜索策略：
1. web_search "bilibili AI 大模型"、"B站 AI工具 测评"（限定近3天）
2. web_search "site:bilibili.com AI" + 时间限定
3. 搜索重点 UP 主近3天是否有新视频
4. 搜索 B站 AI 热搜 / 热门排行

抓取字段：视频标题、UP 主、BV号或链接、播放量（如有）、摘要、价值说明
目标：5-8 条优质视频

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
【平台 2：知乎（Zhihu）】

重点关注：
- 话题：人工智能、大模型、ChatGPT、AI Agent、Claude、Cursor、深度学习
- 类型：高赞回答（>500赞）、热榜问题、专栏深度分析文章
- 知名答主：苏剑林、李rumor、张俊林、王喆、刘群等 NLP/AI 领域大V

搜索策略：
1. web_search "知乎 AI 热门" / "zhihu.com AI 大模型"（限定近3天）
2. web_search "site:zhihu.com AI agent" / "site:zhihu.com 大模型"
3. 搜索知乎热榜中 AI 相关问题
4. 搜索特定热点事件在知乎的讨论

抓取字段：问题/文章标题、回答者/作者、链接、点赞数（如有）、摘要、价值说明
目标：3-5 条高质量内容

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
【平台 3：小红书（Xiaohongshu / RED）】

重点关注：
- 类型：AI 工具测评笔记、效率神器推荐、AI 绘画/写作/视频实操、职场 AI 应用
- 热门标签：#AI工具 #ChatGPT #AI绘画 #AI效率 #Midjourney #AI写作 #AI办公

搜索策略：
1. web_search "小红书 AI工具 推荐"（限定近3天）
2. web_search "xiaohongshu.com AI" / "RED AI tool"
3. web_search "小红书 AI 爆款笔记"

抓取字段：笔记标题、作者、链接（如有）、点赞/收藏数（如有）、摘要、价值说明
目标：3-5 条爆款笔记

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
【平台 4：其他国内科技媒体】

覆盖：36氪、虎嗅、极客公园、InfoQ中文、CSDN博客、少数派

搜索策略：
1. web_search "36氪 AI" / "虎嗅 大模型" / "极客公园 AI"（限定近3天）
2. web_search "site:36kr.com AI" / "site:huxiu.com AI"

抓取字段：文章标题、媒体来源、链接、摘要、价值说明
目标：3-5 条重要报道

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
【通用要求】
- 每条必须真实有出处，抓不到就如实说"该信源未拿到"，绝对不要编造内容
- 标注具体发布日期（精确到天），让整合时可区分"今天"vs"前天"
- 优先收录热度高（播放量/点赞/互动量大）的内容
- 总目标：15-20 条跨平台热门 AI 内容

权限：只读，不修改文件。
```

### Step 3: 整合去重

三份资料都返回后，做整合：
- 重复的条目以更详细的版本为准
- 各自独家的内容都要保留
- 四条最重磅的选为"最值得记住"，放在顶部高亮条
- 国内平台内容如与其他信源报道同一事件，可合并但保留国内平台链接作为补充视角
- 国内平台层的条目需标注具体发布日期（可能是前天/大前天），与核心层"仅昨天"区分开

### Step 4: 生成 HTML 文件

**文件路径**：`D:\Workspace\news\YYYY-MM-DD-ai-daily.html`

**HTML 样式参考**：读取 `D:\Workspace\news\2026-05-26-ai-daily.html` 作为样式模板（CSS 变量、卡片结构、导航栏、信源表等全部沿用）。

**结构层次**（从上到下）：
1. **页面头部**：日期、标题、lede（一句话定调当天基调）
2. **高亮条**（`class="highlight-strip"`）：四条最值得记住
3. **核心层**（`id="core-layer"`）：基础模型 → Agent/Coding → 本地部署/推理栈 → GitHub Trending → 论文，各用 `<h3 class="cat">` 分隔
4. **应用层**（`id="app-layer"`）：行业应用 & 商业动态
5. **X/Twitter 摘录**（`id="twitter-layer"`）：关键账号推文列表，说明间接获取方式
6. **国内平台热门**（`id="cn-platform-layer"`）：B站视频 / 知乎热议 / 小红书爆款 / 媒体头条，按平台分组展示，各条目标注发布日期
7. **信源覆盖表**（`id="coverage"`）：用 `<table class="coverage">`，标注 ✅ / ❌ / ⚠️

**卡片条目规范**（每个条目一个 `<div class="card">`）：
- 重要爆料用 `<div class="card hot">` + `<span class="tag hot">独家爆料</span>`
- 必须包含：title（标题）、source-tags（信源标签）、summary（摘要）、value（价值说明）、link（原文链接）
- tag 分类：`<span class="tag core">` 核心层 / `<span class="tag app">` 应用层 / `<span class="tag tweet">` Twitter / `<span class="tag bilibili">` B站 / `<span class="tag zhihu">` 知乎 / `<span class="tag red">` 小红书 / `<span class="tag cn-media">` 国内媒体
- 各 card 间按重要性排序，同类中最重要的放最前面
- 国内平台卡片额外包含：作者/UP主名称（`<span class="author-name">`）、热度指标（`<span class="engagement">`，播放量/点赞数等，如有）、发布日期（`<span class="pub-date">`）

**左侧导航栏**（`<aside class="nav">`）：sticky 定位，包含各章节的锚点链接（含"国内平台热门"）。

**⚠️ 关键技术注意：HTML 编码处理**
- 用 `write` 工具直接写入文件（write 默认是 UTF-8 无 BOM，正确）
- 如果因某种原因需要手动拼接，**严禁**使用 PowerShell 的 `Get-Content -Raw` + `Set-Content -Encoding UTF8`，这会经过 GBK 错误解码导致中文乱码
- 必须使用 .NET API：`$utf8 = New-Object System.Text.UTF8Encoding($false)`；`[System.IO.File]::ReadAllText(path, $utf8)` 读取，`[System.IO.File]::WriteAllText(path, content, $utf8)` 写入
- 写完后用 `[System.IO.File]::ReadAllBytes(path)` 验证：首三字节应该是 60,33,68（即 `<!D`），不是 BOM 239,187,191

### Step 5: stage 文件 + 桌面通知

```python
stage_files(filepaths=["D:\\Workspace\\news\\YYYY-MM-DD-ai-daily.html"])
notify(
    title="AI 日报 · YYYY-MM-DD",
    body=f"今日已生成 {N} 条动态\n- {高亮1（≤30字）}\n- {高亮2（≤30字）}\n- {高亮3（≤30字）}",
    channels=["desktop"]
)
```

## 内容撰写规则

### 信息密度
- 靠事实密度说话，不凑数。如果昨天动态确实稀少，就在 lede 和通知里如实说"今日动态稀少"
- 每条都要有独立的"价值判断"——告诉读者这条为什么值得看，而不是单纯罗列
- 不要把多条同质新闻揉成一条，各自独立成卡，便于读者按兴趣跳读

### 价值判断（Value）撰写原则
每条 card 的 `.value` 部分是最体现差异化的地方，应该：
- 指出这条新闻**为什么今天很重要**，而不是复述摘要
- 可以是行业影响、技术趋势、对读者的实用意义、或与其他条目的关联
- 可以用问句收尾引发思考，但不要空洞的"值得关注"
- 例："2026 年的核心命题被反复印证——能力瓶颈已从模型参数转移到 harness 系统。"

### 标题风格
- 信息完整，一眼知道谁干了什么
- 重要信息前置：模型名 / 公司名 / 事件名放最前面
- 例："GPT-5.6 (iris-alpha) 后端日志泄露，150 万 token 上下文" 而不是 "消息称 OpenAI 新模型曝光"

### 国内平台内容撰写规范
- **B站**标题格式："[UP主名] 视频标题"，如 "稚晖君：自研机器人大脑芯片首次实测"
- **知乎**标题格式："[知乎] 问题/文章标题"，如 "[知乎] 如何评价 Claude 4 的编程能力？"
- **小红书**标题格式："[小红书] 笔记标题"，如 "[小红书] 用AI一天做完毕业论文，亲测6款工具"
- **媒体**标题格式："[媒体名] 文章标题"，如 "[36氪] DeepSeek 完成新一轮融资估值破百亿"
- 摘要侧重核心结论或亮点，而非流程描述
- 价值判断可关联作者专业背景、社区热度趋势、或与当日其他新闻的关联
- 热度指标（播放量/点赞数/收藏数）作为参考标注，不作为唯一筛选标准——内容质量优先
- 每条必须标注发布日期（如"5/30发布"），因为时间窗口是3天而非仅昨天

### 信源处理
- 每条必须标注具体信源，附可追溯的 URL
- X 主站封锁严重时，在 Twitter 章节顶部加说明文字解释获取方式
- B站视频链接统一使用 `https://www.bilibili.com/video/BVxxxxxxx` 格式
- 知乎链接使用 `https://www.zhihu.com/question/xxx` 或 `https://zhuanlan.zhihu.com/p/xxx` 格式
- 小红书链接使用 `https://www.xiaohongshu.com/explore/xxx` 格式（如能获取）
- 信源覆盖表如实标注成功 ✅ / 失败 ❌ / 间接 ⚠️
- 某些信源完全抓不到（如 OpenAI Blog 403、HN fetch failed），在覆盖表里如实标 ❌，不影响其他部分继续生成

### 异常处理
- 某个 subagent 调研失败或超时：继续用其他 subagent 的结果生成，在信源覆盖表和通知中说明
- 整体流程失败：发桌面通知告知失败原因，不要静默死掉

## 深度解读模式（默认启用）

日报的核心价值不是"列新闻"，而是**从新闻中提炼技术洞察**。默认采用以下结构：

### 输出结构

不以新闻条目为单位，而是以**关键技术点**为单位组织内容。从当天所有事件/新闻中归纳出 5-8 个核心技术点，每个技术点从 4 个维度展开：

| 维度 | 含义 | 内容要求 |
|------|------|----------|
| **原理** | 这项技术是什么、怎么工作 | 技术架构、核心机制、关键算法、与已有方案的区别。需要实际阅读原文提取，不能只读标题 |
| **现有应用** | 最新最热的代表性产品/工具/项目 | 列举 2-5 个具体的、已上线/已开源的应用实例。要求有名称、一句话说明、链接。优先选择最近发布的、热度最高的、最具代表性的 |
| **落地用途** | 技术实际解决什么问题、产出什么价值 | 具体的使用场景、量化效果（如"训练速度翻倍""错误率降低30%"）、真实案例 |
| **后续方向** | 接下来会往哪走 | 技术路线的演进趋势、未解决的挑战、对行业格局的影响预判 |

### "现有应用"维度撰写规范

这个维度专门列举该技术点最新、最热、最有代表性的具体产品或项目：

```
格式示例：
• Claude Workflows（Anthropic，5/28发布）— 多子代理并行编排，支持百万行级代码迁移
• Cursor v2.5（Anysphere）— AI 编码半自主队友模式，报告AI增强效果分化
• OpenRouter（独角兽，$1.3B估值）— 400+模型一站式路由调用平台
```

要求：
- 每个应用必须有：产品名称、公司/团队、发布时间或版本、一句话核心定位
- 优先选择本周/本月新发布或有重大更新的应用
- 包含开源项目（GitHub链接）和商业产品
- 避免只列大厂产品，也关注新兴创业公司和个人开源项目

### 事件作为引用

新闻事件不是主体，而是技术点的**引用来源**。放在每个技术卡片底部，格式为：
```
引用事件：
• [信源名] 标题 — URL
• [信源名] 标题 — URL
```

### 深度阅读要求

生成日报时，**必须用 WebFetch 实际阅读**至少 8-12 篇原文，提取技术细节和数据。禁止只搜标题不读内容。在信源覆盖表中标注"全文阅读"状态。

### 设计风格

使用 frontend-design skill 的设计思路：
- 白色主题 + iOS glassmorphism 磨砂质感（backdrop-filter: blur + 半透明白色卡片）
- 独特字体选择（避免 Inter/Roboto 等通用字体）
- 精致的圆角、柔和阴影、微妙渐变
- 左侧 sticky 导航改为锚点跳转至各技术点
- 四维度用不同颜色标识：原理（蓝）、现有应用（橙）、落地（绿）、方向（紫）

## 搜索策略原则

搜索不仅限于 trending/最新热门。对于每个技术领域，应采用**全景式搜索**：

1. **当日热点**：GitHub Trending、新闻、社交媒体（捕捉最新动态）
2. **生态全景**：搜索该领域当前主流方案的对比和选型文章（例如"best agent framework 2026 comparison"），了解当前被广泛使用的成熟方案
3. **历史演进**：对于重要技术点，补充搜索其前身和演进路径（例如从 LangChain → LangGraph → DeerFlow 的迭代关系）
4. **非热门但重要**：关注那些 star 数不高但被头部开发者推荐/使用的项目（通过 Simon Willison、swyx 等人的博客/推文发现）

搜索心法：最热的不一定最好，最好的不一定最热。目标是帮助读者建立"这个领域当前怎么选"的判断力。

## 技术追踪 Wiki（持久化记忆）

每次生成日报后，同步更新技术追踪 wiki 文件（`./tmp/ai-tech-tracker.md`），用于跨日期回溯同一技术的发展过程。

### Wiki 结构

```markdown
# AI 技术追踪 Wiki

## [技术领域名称]（如：Agent 框架）

### 当前生态全景
| 项目 | 定位 | 成熟度 | 最近动态 |
|------|------|--------|----------|
| DeerFlow | Super Agent Harness | 生产级 | 2.0 发布 (2026-02) |
| LangGraph | 通用 Agent 编排 | 成熟 | ... |

### 时间线
- **2026-06-02**：[事件摘要] — 来源：日报链接
- **2026-05-31**：[事件摘要] — 来源：日报链接

### 关键洞察
- [跨多天观察总结出的趋势判断]
```

### 更新规则
- 每次日报生成后，将当天提炼的技术点追加到对应领域的时间线中
- 如果出现新的技术领域，创建新的章节
- "当前生态全景"表格保持最新状态（有新版本/新项目时更新）
- "关键洞察"在同一技术出现 3 次以上时，总结跨期趋势
- wiki 文件在下次生成日报时先读取，用于提供历史上下文（避免重复解释已跟踪过的技术）

## 输出物

单个 HTML 文件，路径 `D:\Workspace\news\YYYY-MM-DD-ai-daily.html`。
