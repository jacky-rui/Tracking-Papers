# 目标跟踪

## 专题：视觉语言跟踪 Visual Language Tracking

### 基准

| 数据集名称 | 发布年份 | 发布机构 | 数据规模 | 标注类型 | 语言描述类型 | 评估指标 | 场景类型 | 挑战属性 | 目标类别数 | 最优性能 | 下载链接 |
|-----------|---------|----------|----------|----------|--------------|----------|----------|----------|------------|----------|----------------|
|VastTrack|2024|中科院软件研究所|50,610 视频序列，420万帧|边界框、语言描述|自然语言描述|精度（PRE）、归一化精度（NPRE）、成功率（SUC）|多场景|隐蔽性、变形、旋转、尺度变化、光照变化、快速运动、运动模糊、背景杂乱、低分辨率|2,115|SeqTrack|[链接](https://github.com/HengLan/VastTrack)|
|SemTrack|2024|新加坡科技设计大学|视频数量：6,961；总帧数：6.7M|语义轨迹标注（目标位置、关联对象位置和类别、交互类型）|目标初始化句子|Semantic Tracking-mAP (ST-mAP)|12种不同场景（室内和室外）|多样化的交互类型、复杂的光照条件、遮挡、视角变化|115个对象类别|SemTracker + Meta-learning 方法最优|[访问链接](https://sutdcv.github.io/SemTrack/)|
|VLT-MI|2024|中科院自动化所|视频数量：3,619；总帧数：6.6M|多轮交互标注（文本更新、边界框修正）|多粒度（精简文本和详细文本）|精度（PRE）、归一化精度（N-PRE）、成功率（SR）、平均交互次数（AMI）、平均最大成功跟踪长度（AMSL）| 短期跟踪、长期跟踪、全局实例跟踪|多模态交互、目标丢失恢复|未明确提及|JointNLT 在不同任务中表现最优|[arXiv链接](https://arxiv.org/abs/2409.08887)|
|MGIT|2023|中科院自动化所|视频数量：150；总帧数：203万|多粒度标注（动作、活动、故事）|多粒度（动作、活动、故事）|精度（PRE）、归一化精度（N-PRE）、成功率（SR）|长视频、复杂时空关系、因果关系|复杂叙事内容、多模态信息融合、长文本处理|未明确提及|视觉基础方法优于多模态方法（如 MixFormer）|[MGIT下载链接](http://videocube.aitestunion.com/)|

### 当前研究

| 论文标题 | 时间 | 会议/期刊 | 主要难点 | 创新点 |
|---------|------|------------|----------|---------|
|Boost Tracking by Natural Language With Prompt-Guided Grounding|2025|TITS|1. 现有的视觉语言跟踪方法在复杂背景和不准确记忆信息下表现受限。2. 语言描述与视觉特征对齐困难，容易受到背景干扰。3. 传统的记忆模块无法有效更新历史信息，导致跟踪过程中出现错误判断。|1. 提出了一种全局-局部框架，包括提示引导的定位模块、本地跟踪模块和基于记忆的切换模块。2. 引入名词提示引导CLIP模型聚焦目标区域，减少背景干扰，实现视觉与语言特征的语义对齐。3. 开发基于记忆的切换模块，通过逆向跟踪更新历史信息，确保记忆的高质量。|
|Progressive Semantic-Visual Alignment and Refinement for Vision-Language Tracking|2025|TCSVT|1. 现有的视觉语言跟踪方法无法充分利用Transformer架构来挖掘多层级的跨模态上下文信息。2. 早期融合和晚期融合方法无法有效对齐视觉特征和语义特征，限制了跟踪性能。3. 如何在多模态特征中突出目标对象，并抑制背景干扰是一个挑战。|1. 提出了一种新的渐进式联合视觉语言Transformer（PJVLT），通过逐步对齐和细化视觉特征与语义特征，实现从粗到细的多模态特征融合。2. 引入语义感知实例编码器层（SAIEL），在Transformer的每一层中对齐视觉信号和语义信号。3. 提出通道通信和补丁交互层（CCPIL），用于激活与目标对象相关的多模态特征通道和补丁，提升跟踪精度。|
|Enhancing Vision-Language Tracking by Effectively Converting Textual Cues into Visual Cues|2025|ICASSP|现有的视觉语言跟踪（VLT）数据集中文本数据稀缺，限制了文本和视觉模态的有效对齐，导致难以充分利用文本线索进行跟踪|提出了一种名为CTVLT的插件式方法，通过将文本线索转换为视觉热图来增强跟踪性能，并设计了文本线索映射模块和热图引导模块，有效利用基础模型的文本-图像对齐能力|
|Divert More Attention to Vision-Language Object Tracking|2024|TPAMI|现有的视觉语言跟踪数据集规模较小且标注风格单一，导致模型难以泛化；现有方法中视觉和语言模态的交互学习效果不佳|提出了一种通用的属性标注策略，构建了一个包含超过23,000个视频的大规模视觉语言跟踪数据库；引入了一种新的框架，通过学习统一自适应的视觉语言表示来改进跟踪性能，包括提出的非对称架构搜索和模态混合器（ModaMixer）|
|How Texts Help? A Fine-grained Evaluation to Reveal the Role of Language in Vision-Language Tracking|2024|arXiv|1. 现有的视觉语言跟踪（VLT）方法在多种基准测试中表现不如单模态方法，语言信息有时甚至成为“干扰”。2. 缺乏对语言信息在不同挑战条件下的细粒度评估，导致难以理解语言在VLT中的作用。3. 现有VLT基准测试缺乏对视觉模态挑战因素的细粒度标注，限制了复杂场景下VLT跟踪器的评估能力。|1. 提出了VLTVerse——首个细粒度评估框架，涵盖10种挑战因素和6种多粒度语义信息，为VLT跟踪器提供灵活且多维度的评估空间。2. 通过60种挑战因素和语义类型的组合，系统性地对主流VLT跟踪器进行细粒度评估，揭示了传统评估方法无法捕捉的语言作用。3. 提供了对不同挑战条件下语言模态影响的解耦分析，为从数据、评估和算法维度提升VLT性能提供了重要指导。|
|Multi-Stage Image-Language Cross-Generative Fusion Network for Video-Based Referring Expression Comprehension|2024|TIP|1. 现有方法依赖于跟踪模板质量，缺乏标注数据时性能下降；2. 单帧特征学习无法有效捕捉帧间关系；3. 视觉与语言特征融合能力不足|1. 提出多阶段视觉-语言互生成融合网络MILCGF-Net，基于一阶段目标检测；2. 引入帧密集特征聚合模块，聚合密集相邻帧特征；3. 提出视觉语言互生成融合模块，通过多阶段学习生成跨模态特征；4. 引入一致性损失，增强视觉-语言相似性约束|
|Multi-modal Understanding and Generation for Object Tracking|2024|TCSVT|1. 视觉和语言模态之间存在不一致性，直接融合可能导致冲突。2. 语言描述在跟踪过程中可能无法适应目标状态的变化。3. 现有的视觉语言跟踪方法在处理复杂场景时性能受限。|1. 提出MugTracker框架，结合多模态理解与生成，通过图像到文本生成动态更新语言描述以解决模态不一致问题。2. 基于BLIP架构，开发动态文本生成器，实时更新文本描述以适应目标变化。3. 引入视觉TE-Adapter和语言Text-Adapter，增强模型对目标的理解和语义生成能力。|
|Vision-Language Tracking With CLIP and Interactive Prompt Learning|2024|TITS|1. 多模态数据稀缺限制了视觉语言跟踪的发展。2. 传统的模态融合模块复杂且计算负担重，难以实时部署。3. 现有的视觉语言跟踪方法在复杂场景下表现受限。|1. 提出了一种基于CLIP和交互式提示学习的单阶段视觉语言跟踪框架（CPIPTrack），将特征提取和多模态融合统一到一个框架中。2. 设计了三种类型的提示（语言查询提示、语言引导提示和联合提取融合提示），通过交互式提示学习实现视觉和语言模态的动态融合。|
Language-Guided Dual-Modal Local Correspondence for Single Object Tracking|2024|Trans. MM|1. 仅依赖视觉信息的传统单目标跟踪方法在目标外观变化时性能受限。2. 目标语义信息在外观特征中稀缺，难以应对目标外观的持续变化。3. 传统方法需要手动输入目标初始位置，难以实现完全自动化。|1. 提出一种视觉-语言双模态单目标跟踪框架，通过局部对应建模融合视觉和语言信息。2. 引入全局重定位方法，利用双模态语义和运动信息实现长期跟踪。3. 设计了前景感知记忆（FPM）、局部感知互注意力（LPMA）和视觉-语言局部对比（VLLC）模块，有效缩小模态间语义差距。4. 提出一种基于时间运动融合（TMF）、双模态候选生成（DCG）和视觉-语言引导融合（VLGF）的全局重定位方法，提升跟踪鲁棒性。|
|Consistencies are All You Need for Semi-supervised Vision-Language Tracking|2024|MM|1. 现有的视觉语言跟踪方法依赖于大量昂贵且耗时的人工标注数据。2. 无监督方法无法有效利用语言信息，难以处理目标的复杂外观变化。3. 如何在有限标注数据的情况下训练鲁棒的视觉语言跟踪器是一个挑战。|1. 提出了首个半监督学习框架用于视觉语言跟踪（SS-VLT），通过挖掘视频中的空间、时间和语义一致性来减少对标注数据的依赖。2. 设计了一个简单高效的跟踪器ATTracker（Asymmetrical Transformer Tracker），通过非对称的多源编码器和MLP解码器实现目标感知和噪声抑制。3. 引入了三种一致性损失（空间一致性、时间一致性和语义一致性），通过多阶段训练逐步优化跟踪器性能。|
| Context-Aware Integration of Language and Visual References for Natural Language Tracking | 2024 | CVPR | 语言描述与视觉模板不一致导致的跟踪漂移；多模态融合的复杂性 | 提出联合多模态跟踪框架，包含提示调制模块和统一目标解码模块，实现端到端的单步预测 |
|DTLLM-VLT: Diverse Text Generation for Visual Language Tracking Based on LLM|2024|CVPRW|1. 现有的视觉语言跟踪（VLT）基准数据集大多采用单一粒度的注释，缺乏统一的语义框架。2. 手动标注高质量的文本注释耗时且成本高。3. 现有方法难以充分利用复杂时空关系的长文本信息，且在多模态对齐能力上存在不足。|1. 提出DTLLM-VLT框架，利用大型语言模型（LLM）自动生成多样化、多粒度的文本描述，丰富数据集的语义信息。2. 为三个主流的VLT基准数据集（短期跟踪、长期跟踪和全局实例跟踪）生成四种粒度的文本描述，克服了单一粒度的限制。|
| Divert More Attention to Vision-Language Object Tracking | 2024 | TPAMI | 缺乏大规模视觉语言标注视频，现有方法中视觉语言交互学习效果不佳 | 提出一种通用属性标注策略，构建大规模视觉语言跟踪数据库，并设计新型框架，通过对比损失函数对齐不同模态 |
| MemVLT: Vision-Language Tracking with Adaptive Memory-based Prompts | 2024 | NeurIPs | 大多数视觉-语言跟踪器仍然过度依赖于初始固定的多模态提示，这些提示难以为目标的动态变化提供有效的指导 | 提出一种长期-短期多模态记忆系统，包括记忆储存，记忆交互和自适应提示生成。解决固定提示的带来的问题 |
| Unifying Visual and Vision-Language Tracking via Contrastive Learning | 2024 | AAAI | 大多数现有跟踪器专为部分参考设置设计，难以在所有三种参考设置（BBOX、NL、NL+BBOX）中表现良好。此外，由于视觉和语言模态之间的语义差距，基于自然语言的跟踪器在纯边界框参考设置中的表现有限 | 模态统一特征提取器：在浅层编码器层中分别提取视觉和语言特征，深层编码器层中融合；多模态对比损失：通过计算语义标记与搜索区域嵌入之间的相似度进行对齐；模态自适应边界框头：提出基于分布的交叉注意力机制 |
| CiteTracker: Correlating Image and Text for Visual Tracking | 2023 | ICCV | 文本提示对目标特征的总结更加抽象和稳定，有望解决单一模版的模糊歧义性在目标剧烈变化时的问题 | 提出文本增强跟踪系统，包括：文本生成模块、动态描述模块和基于注意力的相关模块 |
| Joint Visual Grounding and Tracking with Natural Language Specification | 2023 | CVPR | 大多数现有方法将视觉定位和跟踪分为两个独立的步骤，分别使用独立的模型来完成这两个任务。这种分离的框架忽略了视觉定位和跟踪之间的联系 | 多源关系建模；语义引导的时序建模；端到端学习和推理 |
| Type-to-Track: Retrieve Any Object via Prompt-based Tracking | 2023 | NeurIPS | 传统的多目标跟踪方法通常依赖于边界框或类别注释来识别和跟踪目标。这些方法在目标外观变化大、背景干扰多时有问题 | 将自然语言描述和视频帧中的目标对象嵌入到共同特征空间；使用Transformer架构捕捉时空特征；提供语言-多目标跟踪GroOT数据集 |

## 专题：改进单流跟踪器

| 论文标题 | 时间 | 会议/期刊 |主要难点 | 创新点 |
|---------|------|-----------|----------|----------|
|A Transformer-based network with adaptive spatial prior for visual tracking|2025|Neuro Computing|1. Transformer将图像分割为序列，破坏了目标内部的结构信息。2. Transformer在编码目标模板和搜索区域时容易混淆前景和背景特征。3. 现有方法在复杂场景下（如外观变化、遮挡、尺度变化）表现不佳。|1. 提出了一种基于Transformer的全结构化先验跟踪框架SPformer，通过自注意力空间先验模块（SSP）和交叉注意力结构先验模块（CSP）增强特征关联。2. 引入高斯先验模块（CGP）和随机先验模块（CRP）以适应不同场景下的语义交互。3. 在多个基准数据集上验证了SPformer的性能，证明其优于现有的SOTA跟踪器。|

## 专题：轨迹增强跟踪

| 论文标题 | 时间 | 会议/期刊 |主要难点 | 创新点 |
|---------|------|-----------|----------|----------|
|Historical states modeling for visual tracking|2025|Neural Computing and Applications|1. 现有的学习型跟踪器仅利用单张搜索图像和模板进行训练，缺乏时间信息，数据利用率低。2. 在复杂场景下（如目标变形、消失或被遮挡）跟踪性能受限。| 方法类似SwinTrack加入运动token。 1. 提出了轨迹引导跟踪框架TGTrack，通过历史轨迹预测目标当前位置。2. 引入轨迹预测模块，利用历史轨迹信息生成候选位置标记，为跟踪提供时间信息。3. 简化了预测头，消除了手动定制的后处理步骤。|

## 最新论文整理

### AAAI 2025
部分研究使用Mamba改进跟踪架构
| 论文标题 | 时间 | 会议/期刊 |主要难点 | 创新点 |
|---------|------|-----------|----------|----------|
|Robust Tracking via Mamba-based Context-aware Token Learning|2025|AAAI|1. 现有的目标跟踪方法通常通过输入大量图像（或特征）来结合时间和外观信息，导致计算成本高、学习负担重。 2. 输入过多图像可能会引入无用或干扰信息，影响跟踪性能。|1. 提出了一种简单而鲁棒的跟踪器 TemTrack，将时间信息学习与外观建模分离，通过一组代表性的时间标记（track tokens）提取时间关系，而不是直接从图像中提取。 2. 引入基于 Mamba 的 Temporal Module，结合自回归特性和全局感知能力，能够有效建模时间上下文信息。3. 在多个基准数据集上实现了实时速度和竞争性能的平衡，显著降低了计算成本。
|Exploring Enhanced Contextual Information for Video-Level Object Tracking|2025|AAAI|1. 现有视频级目标跟踪方法仅使用少量标记（tokens）来传递上下文信息，导致信息丢失，无法充分利用视频序列中的上下文信息。2. 如何高效地传递更丰富的上下文信息是一个亟待解决的挑战。|1. 提出了一种新的视频级目标跟踪框架 MCITrack，利用 Mamba 的隐藏状态来记录和传递丰富的上下文信息，从而增强模型的跟踪性能。2. 引入了 Contextual Information Fusion (CIF) 模块，包含 Mamba 层和交叉注意力层，能够将历史上下文信息与当前视觉特征深度融合，提升多层级上下文信息的利用效率。3. 在多个基准数据集上实现了新的最高性能（SOTA）。|

### CVPR 2024

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

### ICCV 2023
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

### TPAMI
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