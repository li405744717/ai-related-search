# AI 算力基础设施

> 追踪 AI 芯片、数据中心投资、推理框架、量化技术的演进。

---

## 当前生态全景（截至 2026-06）

### 芯片平台
| 芯片 | 公司 | 工艺 | 定位 | 状态 |
|------|------|------|------|------|
| Blackwell Ultra (B200/GB200) | NVIDIA | 4nm | 训练+推理旗舰 | 大规模量产 |
| Vera Rubin | NVIDIA | 3nm/2nm | 下一代平台 | 2026H2 |
| RTX Spark | NVIDIA | — | AI PC 芯片 | 2026-06 发布 |
| Jetson Thor | NVIDIA | — | 具身智能 | 2026-06 发布 |
| MI300X | AMD | 5nm | 推理（192GB HBM3） | 生产级 |
| MI350 | AMD | 3nm | CDNA 4 训练+推理 | 2026 中期 |
| TPU v6 Trillium | Google | — | 训练+推理 | 全面开放 |
| Maia 100 | Microsoft | 5nm | Azure 内部推理 | 部署中 |
| Trainium2 | Amazon | — | AWS 训练芯片 | GA |
| MTIA v2 | Meta | — | 推荐/排序推理 | 内部部署 |

### 推理框架
| 框架 | 定位 | 状态 |
|------|------|------|
| vLLM | 通用 LLM serving | 生产级，支持 Blackwell FP4 |
| TensorRT-LLM | NVIDIA 优化推理 | 生产级 |
| SGLang | 结构化生成 | 成长期 |
| sglang | 批处理调度优化 | 活跃 |

---

## 月度时间线

### 2026年1月
- **[NVIDIA Blackwell] 大规模部署阶段** — GB200 NVL72 机架（72 GPU NVLink 互联），单机架 FP4 推理 ~720 PFLOPS
- **[Microsoft Maia 100] 扩大 Azure 部署** — 主要用于内部 Copilot 推理
- **[CoreWeave] 继续扩张** — 2025 年累计融资超 120 亿美元，GPU 保有量行业前列
- **[Meta MTIA v2] 扩大内部部署** — 推荐系统和排序推理

### 2026年2月
- **[AMD MI350] 技术细节披露** — CDNA 4，3nm，HBM3E，推理性能大幅提升
- **[Google TPU Trillium] 全面开放** — 单芯片训练性能比 v5e 提升 ~4.7x
- **[vLLM] 重大更新** — 长上下文(128K+)优化、多模态支持、Blackwell FP4/FP8 原生支持
- **[CapEx 指引] 各巨头公布 2026 投资**：
  - Microsoft: ~800 亿美元
  - Alphabet/Google: ~600-750 亿美元
  - Meta: ~500-600 亿美元

### 2026年3月
- **[NVIDIA GTC 2026]** — 披露 Vera Rubin 架构细节（HBM4、新 NVLink）
- **[Amazon Trainium2] EC2 trn2 全面可用** — 单实例 16 颗，UltraCluster 可扩展 10 万+
- **[TensorRT-LLM] Blackwell 优化** — FP4 量化 + NVLink 多机推理万亿参数 MoE
- **[SGLang] 社区活跃度提升** — 结构化输出、批处理调度优化

### 2026年4月
- **[FP4 量化] 成为主流推理精度** — 相比 FP8 再提升 ~2x 吞吐，质量损失可接受
- **[GPU 云扩张] CoreWeave/Lambda/Together AI** — 开始部署 GB200 NVL72
- **[AMD MI300X] 推理份额增长** — ROCm + vLLM 成熟，成本敏感场景获更多采用
- **[数据中心电力] 成为关键瓶颈** — 单机架 100-120kW，液冷全面铺开

### 2026年5月
- **[Vera Rubin] 供应链信息披露** — 3nm/2nm 工艺，HBM4，2026H2 推出
- **[推理加速] Speculative Decoding 成熟** — 配合量化实现 3-5x 延迟降低
- **[全球算力竞赛] 各国加大投资** — 沙特/阿联酋/日本/欧盟大规模数据中心计划，全球 AI 基础设施投资预计突破 3000 亿美元

### 2026年6月
- **[Vera Rubin] GTC Taipei 正式发布** — 下一代推理基础设施平台
- **[RTX Spark] AI PC 芯片发布** — NVIDIA 杀入 PC 市场
- **[Jetson Thor] 具身智能芯片发布**
- **[Alphabet] 800 亿美元融资**（6/2）— 伯克希尔 100 亿私募配售，2026 CapEx 1800-1900 亿
- **[Google Cloud] 订单积压超 4600 亿** — 营收增长 63%

---

## 关键洞察

1. **"铲子 vs 淘金者"持续** — 算力供给方（NVIDIA/Google/MS）确定性盈利，需求方（OpenAI/Anthropic）仍亏损
2. **FP4 成为推理标配** — Blackwell 硬件支持 + 软件生态成熟，4-bit 成为默认精度
3. **电力成为第一瓶颈** — 100kW+ 单机架功率，液冷/核能/可再生能源成为数据中心刚需
4. **多云/自研芯片并行** — 各大厂既用 NVIDIA 又自研，形成"保底自研+旗舰 NVIDIA"格局
5. **巴菲特入场** — 传统价值投资标杆首次大额押注 AI 基础设施，确认长期确定性

---

*最后更新：2026-06-05*
