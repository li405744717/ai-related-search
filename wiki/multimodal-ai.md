# 多模态 AI（生图/生视频/语音/3D/OCR）

> 覆盖图像生成、视频生成、语音合成与克隆、3D 生成、数字人、OCR、音乐生成等方向。

---

## 当前生态全景

### 图像生成
| 项目 | 定位 | 成熟度 | 最近动态 |
|------|------|--------|----------|
| Midjourney V8 | 商业级文生图平台 | 生产级 | 2026-05 发布，统一架构生成图/视频/3D |
| Flux 2 (Black Forest Labs) | 开源旗舰文生图 | 生产级 | 2026-04 发布，12B参数，原生多分辨率 |
| Stable Diffusion 4 (Stability AI) | 开源社区标杆 | 生产级 | 2026-03 发布，MMDiT架构 |
| Ideogram 3.0 | 文字渲染精准的生图 | 生产级 | 2026-02 发布，文字准确率95%+ |
| Google Imagen 4 | Google 旗舰生图 | 生产级 | 2026-05 Gemini 集成 |
| Recraft V4 | 设计师向矢量+位图 | 生产级 | 2026-03 发布，原生SVG输出 |

### 视频生成
| 项目 | 定位 | 成熟度 | 最近动态 |
|------|------|--------|----------|
| Kling 3.0 (快手) | 国产视频生成旗舰 | 生产级 | 2026-04 发布，2分钟连贯视频 |
| Veo 3.1 (Google DeepMind) | Google 视频生成 | 生产级 | 2026-05 发布，对话+环境音同步 |
| Wan 2.1 (阿里) | 开源视频生成 | 生产级 | 2026-03 开源，Apache 2.0 |
| Hailuo AI / MiniMax Video | 国产视频生成 | 生产级 | 2026-04 更新，物理引擎增强 |
| Pika 2.5 | 创意短视频 | 生产级 | 2026-03 发布 |
| Runway Gen-4 | 专业影视向 | 生产级 | 2026-02 发布，多镜头叙事 |
| Sora (OpenAI) | ⚠️ 已关停 | 停运 | 2026-02 关停，团队并入 GPT 视觉 |

### 语音合成与克隆
| 项目 | 定位 | 成熟度 | 最近动态 |
|------|------|--------|----------|
| Chatterbox (Resemble AI) | 开源 TTS，超越 ElevenLabs | 开源生产级 | 2026-05 发布，MIT 许可 |
| GPT-SoVITS v4 | 开源语音克隆 | 社区成熟 | 2026-04 更新，5秒克隆 |
| CosyVoice 3.0 (阿里) | 多语言 TTS | 开源生产级 | 2026-05 发布，流式推理 |
| VoxCPM2 (OpenBMB) | 无分词器 TTS | 开源 | 2026-06 发布，30语言，WER 1.84% |
| ElevenLabs | 商业 TTS/克隆 | 生产级 | 持续运营，但开源追平 |
| Fish Speech 2.0 | 开源实时 TTS | 社区成熟 | 2026-03 发布，VITS2架构 |

### 3D 生成
| 项目 | 定位 | 成熟度 | 最近动态 |
|------|------|--------|----------|
| Meshy 6 | 商业 AI 3D 建模 | 生产级 | 2026-04 发布，文字→PBR材质网格 |
| Tripo 3.1 (VAST AI) | 单图→3D | 生产级 | 2026-05 发布，<10秒生成 |
| Rodin Gen-2.5 (微软) | 高精度3D生成 | 生产级 | 2026-03 发布 |
| InstantMesh (腾讯) | 开源单图→网格 | 开源 | 2026-02 更新 |
| Genie 2 (Google DeepMind) | 3D世界生成 | 研究 | 2026-01 论文 |

### 数字人
| 项目 | 定位 | 成熟度 | 最近动态 |
|------|------|--------|----------|
| HeyGen 4.0 | 商业数字人视频 | 生产级 | 2026-04 发布，实时互动数字人 |
| D-ID Creative Reality | 数字人对话 | 生产级 | 持续更新 |
| SadTalker/MuseTalk | 开源唇形同步 | 社区成熟 | 持续迭代 |

### OCR 与文档理解
| 项目 | 定位 | 成熟度 | 最近动态 |
|------|------|--------|----------|
| PaddleOCR-VL-1.5 (百度) | 视觉语言OCR | 开源生产级 | 2026-05 发布，端到端多语言 |
| GOT-OCR 2.0 | 通用OCR Transformer | 开源 | 2026-03 更新 |
| Surya (DataLab) | 多语言OCR | 开源 | 2026-04 更新，90+语言 |
| Marker v2 (DataLab) | PDF→Markdown | 开源 | 2026-03 发布 |
| Docling (IBM) | 文档理解 | 开源 | 2026-02 发布 |

### 音乐生成
| 项目 | 定位 | 成熟度 | 最近动态 |
|------|------|--------|----------|
| Suno V5 | 商业 AI 音乐 | 生产级 | 2026-05 发布，5分钟完整编曲 |
| Udio V3 | 商业 AI 音乐 | 生产级 | 2026-04 发布 |
| Stable Audio 3.0 | 开源音频生成 | 开源 | 2026-03 发布 |

---

## 月度时间线

### 2026年1月
- Midjourney V7.5 重大更新（一致性控制+角色锁定）
- Sora 进入衰退期，用户流失加速
- Google Genie 2 论文发布（3D世界生成研究）
- Stable Diffusion 3.5 Turbo 推理优化发布

### 2026年2月
- **Sora 正式关停**（OpenAI 宣布视频团队并入 GPT 视觉部门）
- Ideogram 3.0 发布（文字渲染准确率突破95%）
- Runway Gen-4 发布（多镜头叙事一致性）
- InstantMesh 开源更新（腾讯，单图→3D网格）
- Docling 1.0 发布（IBM 开源文档理解框架）

### 2026年3月
- **Stable Diffusion 4 发布**（MMDiT 架构，8B参数，社区引爆）
- Wan 2.1 开源（阿里视频生成，Apache 2.0）
- Recraft V4 发布（原生 SVG 矢量输出）
- Rodin Gen-2.5 发布（微软高精度3D）
- Fish Speech 2.0 开源（VITS2 架构实时 TTS）
- Pika 2.5 发布
- GOT-OCR 2.0 更新
- Marker v2 发布（PDF→Markdown）
- Stable Audio 3.0 开源

### 2026年4月
- **Flux 2 发布**（Black Forest Labs，12B参数旗舰）
- **Kling 3.0 发布**（快手，2分钟连贯长视频）
- Hailuo AI 物理引擎增强更新
- GPT-SoVITS v4 更新（5秒声音克隆）
- Meshy 6 发布（文字→PBR材质3D网格）
- HeyGen 4.0 发布（实时互动数字人）
- Udio V3 发布
- Surya OCR 更新（90+语言）

### 2026年5月
- **Midjourney V8 发布**（统一架构：图/视频/3D 一体化）
- **Veo 3.1 发布**（Google DeepMind，对话+环境音同步生成）
- **Chatterbox 开源**（Resemble AI，MIT 许可，TTS 质量超 ElevenLabs）
- CosyVoice 3.0 发布（阿里，流式推理多语言 TTS）
- Tripo 3.1 发布（VAST AI，<10秒单图→3D）
- Google Imagen 4 集成 Gemini
- PaddleOCR-VL-1.5 发布（百度，视觉语言端到端 OCR）
- Suno V5 发布（5分钟完整编曲）

### 2026年6月
- **VoxCPM2 开源**（OpenBMB，无分词器 TTS，20B参数，30语言）
- **NVIDIA Cosmos 3 全模态世界模型开源**（含视频/3D/物理模拟）
- Qwen3.7-Plus 发布（屏幕理解能力超 GPT-5.4）
- MiniMax M3 发布（100T数据训练，原生多模态）

---

## 关键洞察

### 架构趋势
- **统一多模态架构成为主流**：Midjourney V8 首先实现图/视频/3D统一生成，预示下半年所有旗舰模型将走向统一架构
- **扩散模型 → DiT/MMDiT 迁移完成**：SD4/Flux2 均采用 DiT 变体，UNet 时代彻底结束
- **视频生成进入"物理正确"竞赛**：从画面质量转向物理模拟准确性（Cosmos 3、Kling 3.0）

### 商业格局
- **Sora 关停是标志性事件**：证明"先做demo再找商业化"路径在视频生成不可行，快手/Google/Runway 的"先落地再迭代"胜出
- **开源 TTS 追平商业**：Chatterbox（MIT）质量超 ElevenLabs，语音合成进入"开源够用"时代
- **中国在视频生成领先**：Kling/Wan/Hailuo 在商业化和技术指标上均领先西方（Runway 除外）

### 技术方向
- **语音合成"大模型化"**：从拼接式→端到端神经→连续潜空间生成（VoxCPM2 无分词器范式）
- **OCR 与 VLM 融合**：PaddleOCR-VL 代表趋势——OCR 不再是独立管线，而是视觉语言模型的子能力
- **3D 生成 <10 秒**：Tripo 3.1 实现单图→3D 十秒内完成，接近实时交互式建模

---

*最后更新：2026-06-05*
