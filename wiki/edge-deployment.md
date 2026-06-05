# AI 边缘部署与本地推理

> 覆盖本地 LLM 部署、量化技术、推理框架、端侧芯片、边缘 AI 设备、端云协作架构等方向。

---

## 当前生态全景

### 本地推理框架
| 项目 | 定位 | 成熟度 | 最近动态 |
|------|------|--------|----------|
| Ollama | 一键本地 LLM 部署 | 生产级 | 2026-05 MLX 后端集成，Apple Silicon 原生加速 |
| llama.cpp | C++ LLM 推理引擎 | 生产级 | 2026-05 IQ_K 量化合并主线 |
| vLLM | 高吞吐 GPU 推理 | 生产级 | 2026 快速迭代，PagedAttention v2 |
| SGLang | 结构化生成优化推理 | 生产级 | 持续更新 |
| LM Studio | 桌面 LLM 客户端 | 生产级 | 持续更新，支持多后端 |
| MLX (Apple) | Apple Silicon 原生推理 | 生产级 | 2026-05 与 Ollama 深度集成 |
| ExLlamaV3 | 极致 GPU 量化推理 | 成熟 | 2026-04 发布，EXL3 格式 |
| MLC-LLM | 多平台编译部署 | 成熟 | 持续更新 |
| Transformers.js v4 | 浏览器端 WebGPU 推理 | 生产级 | 2026-03 发布，ONNX+WebGPU |

### 量化技术
| 技术 | 定位 | 精度 | 最近动态 |
|------|------|------|----------|
| GGUF (llama.cpp) | 通用 CPU/GPU 量化格式 | Q2-Q8 | 标准格式，生态最广 |
| AWQ | 激活感知权重量化 | W4 | 成熟，广泛支持 |
| GPTQ | 训练后权重量化 | W4/W3 | 成熟 |
| IQ_K / Trellis (llama.cpp) | 重要性感知混合量化 | IQ1-IQ4 | 2026-05 合并主线，极限压缩 |
| EXL3 (ExLlamaV3) | GPU 专用高效量化 | 2-8bit | 2026-04 发布 |
| TurboQuant (NVIDIA) | Blackwell 原生 FP4 量化 | FP4 | 2026-05 发布，NIM 集成 |
| BitNet | 1-bit 量化训练 | W1.58 | 微软研究，推理专用硬件路线 |
| HQQ | 半二次量化 | W2-W4 | 2026 持续更新 |

### 端侧 AI 芯片
| 芯片 | 公司 | 定位 | 最近动态 |
|------|------|------|----------|
| RTX Spark | NVIDIA | AI PC 独立芯片 | 2026-06 发布，小型桌面/笔记本 |
| Apple M5 Ultra | Apple | 桌面/工作站 | 2026 预期，统一内存 512GB |
| Snapdragon X Elite | Qualcomm | PC/移动 NPU | 2026 QMX 量化格式 |
| Jetson Thor | NVIDIA | 具身智能边缘 | 2026-06 发布，机器人专用 |
| MediaTek Dimensity 9500 | MediaTek | 移动端 AI | 2026 旗舰移动芯片 |
| Intel Lunar Lake | Intel | PC NPU | 2026 持续出货 |

### 边缘 AI 设备与应用
| 产品 | 公司 | 场景 | 最近动态 |
|------|------|------|----------|
| Alexa+ (LLM版) | Amazon | 智能家居语音Agent | 2026-02 发布，对话式家居控制 |
| Apple Intelligence 2.0 | Apple | iOS/macOS 系统级AI | 2026 WWDC 预期 |
| Google Gemini Nano 2 | Google | Android 端侧推理 | 2026-03 更新 |
| 小米 HyperMind | 小米 | 智能家居中枢AI | 2026-03 发布 |

---

## 月度时间线

### 2026年1月
- Ollama 持续高速增长（GitHub 120k+ stars）
- llama.cpp 量化精度持续改进（社区贡献 IQ 系列）
- vLLM 快速迭代（多模型并行调度）
- BitNet 论文引发业界讨论（1.58bit 推理效率）

### 2026年2月
- **Amazon Alexa+ 发布**（LLM 驱动的对话式智能家居 Agent，首个大规模端侧 Agent 产品）
- FlashAttention-3 广泛部署（推理/训练双优化）
- GGUF 格式生态继续扩展（支持更多模型架构）
- MLC-LLM 更新（Android/iOS 跨平台部署改进）

### 2026年3月
- **Transformers.js v4 发布**（HuggingFace，WebGPU 原生支持，浏览器端跑 7B 模型）
- **Stable Diffusion 4 本地部署优化**（8GB VRAM 可运行）
- Google Gemini Nano 2 更新（Android 14 原生集成）
- 小米 HyperMind 发布（IoT 设备中枢 AI）
- SGLang 结构化生成性能突破

### 2026年4月
- **ExLlamaV3 + EXL3 格式发布**（GPU 推理新标杆，2-8bit 连续精度）
- **Qualcomm QMX 量化格式发布**（Snapdragon NPU 原生格式）
- Flux 2/SD4 本地部署优化（6-8GB VRAM 实用化）
- 模型蒸馏技术成熟（大模型→小模型知识传递标准化）

### 2026年5月
- **Ollama + MLX 深度集成**（Apple Silicon 用户零配置原生加速）
- **IQ_K (Trellis) 量化合并 llama.cpp 主线**（重要性矩阵驱动的混合精度，极限压缩）
- **TurboQuant 发布**（NVIDIA，Blackwell FP4 硬件量化，NIM 一键部署）
- **FlashAttention-4 发布**（Hopper/Blackwell 定制，推理延迟再降 40%）
- CosyVoice 3.0 流式推理（端侧 TTS 实时化）
- vLLM 持续迭代（投机解码 + 量化推理联合优化）

### 2026年6月
- **NVIDIA RTX Spark 发布**（AI PC 专用独立芯片，小型桌面设备）
- **NVIDIA Jetson Thor 发布**（具身智能边缘芯片，机器人/自动驾驶）
- **NVIDIA Vera Rubin 架构公布**（下一代推理基础设施平台）
- Nemotron 3 Ultra 550B 开源（10% 激活率，边缘可运行 55B 活跃参数）
- VoxCPM2 端侧部署探索（20B 参数 TTS，量化后可端侧运行）

---

## 端云协作架构

### 语音 Agent 端云协作模式

这是一种将边缘设备与云端 Agent 结合的典型架构，适用于智能音箱、车载系统、机器人等场景：

```
┌─────────────────┐         ┌──────────────────────────┐
│   边缘设备       │         │      云端 Agent           │
│                 │         │                          │
│  麦克风 → ASR   │────────▶│  意图理解 + 任务规划      │
│  (本地VAD+降噪) │  文本    │  工具调用（MCP/A2A）      │
│                 │         │  多轮对话管理             │
│  扬声器 ← TTS  │◀────────│  响应生成                 │
│  (本地/流式)    │  文本/   │                          │
│                 │  音频流  │  ┌─────────────────────┐ │
│  传感器/执行器  │◀───API──│  │ 设备控制 API 回调    │ │
│  (IoT控制)     │         │  └─────────────────────┘ │
└─────────────────┘         └──────────────────────────┘
```

**关键技术栈：**
- **端侧 ASR**：Whisper.cpp / Sherpa-ONNX / 讯飞离线引擎（本地 VAD + 降噪 + 语音转文字）
- **云端 Agent**：Claude/GPT + MCP 工具链（理解意图、调度工具、生成响应）
- **端侧 TTS**：CosyVoice 3.0 流式 / Chatterbox / 本地小模型（文字转语音播报）
- **设备控制**：Agent 通过 API/MQTT 回调设备（开灯/调温/播放等）
- **协议层**：MCP（Agent↔工具）、A2A（Agent↔Agent）、MQTT/HTTP（Agent↔设备）

**延迟优化关键：**
- VAD（语音活动检测）在端侧完成，避免静音传输
- ASR 可选端侧（Whisper tiny/small）或云端（大模型精度高）
- TTS 流式输出（首字延迟 <500ms）
- Agent 响应流式返回（token streaming）

**代表产品：**
- Amazon Alexa+（2026-02）：完整端云协作，LLM Agent + 智能家居
- 小米 HyperMind（2026-03）：IoT 中枢 + 云端大模型联动
- Apple Intelligence Siri 2.0（2026 WWDC 预期）：端侧理解 + 云端深度推理

---

## 关键洞察

### 量化技术趋势
- **FP4 成为推理标配**：NVIDIA TurboQuant + Blackwell 硬件支持，工业级 FP4 部署无精度损失
- **混合精度量化主流化**：IQ_K/Trellis 证明"不同层用不同精度"是最优策略
- **格式碎片化隐忧**：GGUF/EXL3/AWQ/QMX 各有适用场景，缺乏统一标准

### 部署范式演进
- **"一键部署"成为基本要求**：Ollama + MLX 集成代表方向——用户不需要理解量化细节
- **浏览器端推理实用化**：Transformers.js v4 + WebGPU 让 7B 模型在浏览器跑，边缘延伸到最远端
- **推理成本每6个月降一个数量级**：硬件(Blackwell FP4) + 软件(FlashAttention-4) + 算法(投机解码) 三路并进

### 端侧 AI 格局
- **AI PC 元年确立**：RTX Spark + Apple M5 + Snapdragon X Elite 三足鼎立
- **智能设备从"命令词"到"对话式"**：Alexa+ 标志性转折，所有语音设备将被 LLM Agent 重塑
- **边缘≠离线**：主流范式是端云协作（端侧做 VAD/ASR/TTS 低延迟环节，云端做深度推理）

### 开源生态
- **llama.cpp 是边缘 AI 的 Linux**：几乎所有本地推理最终依赖 llama.cpp 或其衍生
- **Apple Silicon 生态崛起**：MLX + Ollama 让 Mac 成为 AI 开发者首选本地设备
- **模型适配下沉**：旗舰模型发布即提供量化版本（GGUF/AWQ），"本地可跑"成为发布标配

---

*最后更新：2026-06-05*
