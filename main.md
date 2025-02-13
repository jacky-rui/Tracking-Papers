# 目标跟踪

## CVPR 2024

| 论文标题 | 时间 | 会议/期刊 | 跟踪类型 | 主要难点 | 创新点 |
|---------|------|-----------|----------|----------|---------|
| Multi-Object Tracking in the Dark | 2024 | CVPR 2024 | 多目标跟踪 | 低光照环境下目标跟踪困难，缺乏相关数据集 | 构建低光照多目标跟踪数据集（LMOT），提出LTrack方法，包含自适应低通降采样模块和退化抑制学习策略 |
| Towards Generalizable Multi-Object Tracking | 2024 | CVPR 2024 | 多目标跟踪 | 现有跟踪器泛化能力差，难以适应多种场景 | 提出"点到实例"关系框架（GeneralTrack），通过跟踪场景属性指导设计更具泛化能力的跟踪器 |
| Self-Supervised Multi-Object Tracking with Path Consistency | 2024 | CVPR 2024 | 多目标跟踪 | 无监督学习中目标匹配的鲁棒性不足 | 提出路径一致性概念，通过生成不同观察路径并强制关联结果一致来训练模型 |
| RTracker: Recoverable Tracking via PN Tree Structured Memory | 2024 | CVPR 2024 | 多目标跟踪 | 未明确指出，但可能涉及目标跟踪的恢复性和记忆管理 | 提出PN树结构记忆，用于可恢复的目标跟踪 |
| ARTrackV2: Prompting Autoregressive Tracker Where to Look and How to Describe | 2024 | CVPR 2024 | 多目标跟踪 | 自回归跟踪器的引导和描述能力有限 | 提出ARTrackV2，通过提示机制引导跟踪器关注位置和描述方式 |
| OneTracker: Unifying Visual Object Tracking with Foundation Models and Efficient Tuning | 2024 | CVPR 2024 | 单/多目标跟踪 | 不同输入模态（RGB、RGB+X）的跟踪任务难以统一 | 提出OneTracker框架，通过大规模预训练和提示调整实现多模态跟踪任务的统一 |
| DiffusionTrack: Point Set Diffusion Model for Visual Object Tracking | 2024 | CVPR 2024 | 单目标跟踪 | 现有跟踪器容易因单次前向评估而漂移到相似外观的干扰物 | 提出DiffusionTrack，将跟踪视为点集扩散过程，通过多步去噪扩散实现动态目标定位 |
| iKUN: Speak to Trackers Without Retraining | 2024 | CVPR 2024 | 多目标跟踪（基于文本描述） | 需要重新训练整个框架，优化困难，文本描述的开放集长尾分布问题 | 提出iKUN框架，包含知识统一模块（KUM）和神经卡尔曼滤波器（NKF），并提出测试时相似性校准方法 |
| NetTrack: Tracking Highly Dynamic Objects with a Net | 2024 | CVPR 2024 | 多目标跟踪 | 高动态性目标（如快速运动、变形、遮挡）的跟踪困难 | 提出NetTrack框架，通过点级视觉线索构建动态感知关联，引入细粒度采样和匹配方法 |
| Context-Aware Integration of Language and Visual References for Natural Language Tracking | 2024 | CVPR 2024 | 单目标 | 语言描述与视觉模板不一致导致的跟踪漂移；多模态融合的复杂性 | 提出联合多模态跟踪框架，包含提示调制模块和统一目标解码模块，实现端到端的单步预测 |
| HIPTrack: Visual Tracking with Historical Prompts | 2024 | CVPR 2024 | 单目标 | 目标外观变化（如变形和遮挡）导致的跟踪性能下降 | 提出历史提示网络，利用历史前景掩码和视觉特征为跟踪器提供精确的历史信息，无需重新训练模型 |
| DeconfuseTrack: Dealing with Confusion for Multi-Object Tracking | 2024 | CVPR 2024 | 多目标 | 多目标跟踪中的数据关联问题，如ID切换和分配错误 | 提出分解数据关联（DDA）方法和遮挡感知非极大值抑制（ONMS），有效减少混淆 |
| Autoregressive Queries for Adaptive Tracking with Spatio-Temporal Transformers | 2024 | CVPR 2024 | 单目标 | 目标外观复杂变化，现有算法依赖手工设计的时空信息聚合 | 提出基于时空Transformer的自回归查询方法，有效学习时空信息，减少手工设计组件 |
| DiffMOT: A Real-time Diffusion-based Multiple Object Tracker with Non-linear Prediction | 2024 | CVPR 2024 | 多目标 | 实时多目标跟踪中的非线性预测问题 | 基于扩散模型的实时多目标跟踪器，采用非线性预测方法 |
| Delving into the Trajectory Long-tail Distribution for Muti-object Tracking | 2024 | CVPR 2024 | 多目标 | 多目标跟踪数据中的轨迹长尾分布问题 | 提出针对轨迹长尾分布的数据增强策略（SVA和DVA）和分组Softmax模块，减少长尾分布对性能的影响 |

## ICCV 2023
| 论文标题 | 时间 | 会议/期刊 | 跟踪类型 | 主要难点 | 创新点 |
|---------|------|---------------|-------------|----------|---------|
| Tracking Anything with Decoupled Video Segmentation | 2023 | ICCV 2023 | 单/多目标（视频分割任务） | 视频分割任务中训练数据标注成本高 | 提出解耦视频分割方法（DEVA），结合图像级分割和双向时间传播，减少对视频数据的依赖 |
| TrackFlow: Multi-Object Tracking with Normalizing Flows | 2023 | ICCV 2023 | 多目标 | 多目标跟踪中多模态信息融合的复杂性 | 提出基于归一化流的概率方法，将多种信息（如2D运动、视觉外观）融合到一个统一的代价模型中 |
| Robust Object Modeling for Visual Tracking | 2023 | ICCV 2023 | 单目标 | 单独模板学习缺乏模板与搜索区域之间的通信，混合模板学习可能引入干扰 | 提出ROMTrack框架，同时建模固有模板和混合模板特征，引入变化令牌（variation tokens）以适应目标变形和外观变化 |
| Exploring Lightweight Hierarchical Vision Transformers for Efficient Visual Tracking | 2023 | ICCV 2023 | 单目标 | 现有Transformer跟踪器速度慢，难以在计算能力有限的设备上应用 | 提出HiT模型，引入桥接模块（Bridge Module）和双图像位置编码技术，提升速度和性能 |
| Integrating Boxes and Masks: A Multi-Object Framework for Unified Visual Tracking and Segmentation | 2023 | ICCV 2023 | 多目标 | 联合跟踪和分割在初始化和预测中缺乏框和掩码的完全兼容，多关注单目标场景 | 提出MITS框架，支持框和掩码初始化，提出精准框预测器，统一处理目标对象 |
| MeMOTR: Long-Term Memory-Augmented Transformer for Multi-Object Tracking | 2023 | ICCV 2023 | 多目标 | 现有方法主要利用相邻帧之间的目标特征，缺乏长期时间信息建模能力 | 提出MeMOTR方法，通过长期记忆注入和定制的记忆注意力层，提高目标关联能力 |
| Heterogeneous Diversity Driven Active Learning for Multi-Object Tracking | 2023 | ICCV 2023 | 多目标 | 获取大量标注数据在实际应用中不现实 | 提出HD-AMOT方法，通过编码几何和语义信息定义多样化信息表示，学习最优采样策略 |
| Collaborative Tracking Learning for Frame-Rate-Insensitive Multi-Object Tracking | 2023 | ICCV 2023 | 多目标 | 低帧率视频中，现有方法因帧间差异大而性能下降 | 提出ColTrack方法，通过历史查询联合跟踪，插入信息细化模块，提出跟踪目标一致性损失 |
| CiteTracker: Correlating Image and Text for Visual Tracking | 2023 | ICCV 2023 | 单目标 | 目标外观变化剧烈，仅用单一目标图像样本难以定位 | 尚未提供详细创新点，但可能涉及图像与文本关联以增强目标表示 |
| PVT++: A Simple End-to-End Latency-Aware Visual Tracking Framework | 2023 | ICCV 2023 | 单目标 | 未明确指出 | 提出PVT++框架，可能是针对延迟感知的端到端视觉跟踪的简单框架 |

## TPAMI
| 论文标题 | 时间 | 会议/期刊 | 跟踪类型 | 主要难点 | 创新点 |
|---------|------|-----------|----------|----------|---------|
| OmniTracker: Unifying Visual Object Tracking by Tracking-with-Detection | 2025年1月15日 | IEEE TPAMI | 单目标/多目标 | 不同任务（实例跟踪和类别跟踪）导致冗余训练和参数开销 | 提出"跟踪与检测"范式，通过统一的网络架构、模型权重和推理流程，解决所有跟踪任务，减少冗余 |
| One-Stage Anchor-Free Online Multiple Target Tracking With Deformable Local Attention and Task-Aware Prediction | 2024年1月15日 | IEEE TPAMI | 多目标 | 多目标跟踪中的遮挡、目标外观变化和复杂场景 | 提出单阶段无锚点的在线多目标跟踪方法，结合可变形局部注意力和任务感知预测，提升跟踪精度和效率 |
| Divert More Attention to Vision-Language Object Tracking | 2024年6月4日 | IEEE TPAMI | 单目标/多目标 | 缺乏大规模视觉语言标注视频，现有方法中视觉语言交互学习效果不佳 | 提出一种通用属性标注策略，构建大规模视觉语言跟踪数据库，并设计新型框架，通过对比损失函数对齐不同模态 |
| Correlation-Embedded Transformer Tracking: A Single-Branch Framework | 2024年1月15日 | IEEE TPAMI | 单目标 | 单目标跟踪中的目标外观变化、背景干扰 | 提出基于相关性嵌入的单分支Transformer跟踪框架，利用Transformer架构提升特征提取和目标建模能力 |
| Unveiling the Power of Self-Supervision for Multi-View Multi-Human Association and Tracking | 2024年9月19日 | IEEE TPAMI | 多目标（多视角多人） | 多视角多目标关联和跟踪需要复杂标注，且跨视角关联难度大 | 采用自监督学习方法，利用空间-时间自一致性原理设计损失函数，实现多视角多人关联和跟踪 |
| Recursive Least-Squares Estimator-Aided Online Learning for Visual Tracking | 2022年3月7日 | IEEE TPAMI | 单目标 | 单目标跟踪中的在线适应性问题，如何快速适应目标变化 | 提出递归最小二乘估计器辅助的在线学习方法，无需离线训练即可实现快速在线适应，防止灾难性遗忘 |
| OffsetNet: Towards Efficient Multiple Object Tracking, Detection, and Segmentation | 2024年11月4日 | IEEE TPAMI | 多目标 | 多目标跟踪、检测和分割的效率和精度问题 | 提出OffsetNet框架，通过像素偏移表示统一多任务处理，引入内存增强线性自注意力模块，提升时空特征聚合能力 |
| Weakly Supervised Tracklet Association Learning With Video Labels for Person Re-Identification | 2023年12月22日 | IEEE TPAMI | 单目标（行人重识别） | 弱监督学习中噪声轨迹干扰，如何利用视频标签提升性能 | 提出弱监督轨迹关联学习模型，通过包内轨迹判别学习和包间轨迹关联学习，利用视频标签提升行人重识别性能 |