[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

# Awesome Sparse Attention

> A curated list of papers and resources on sparse attention, with a small related coverage of linear and hybrid efficient attention.

Last updated: **2026-03-31**

## How This List Is Organized

This repository uses a **scenario-first taxonomy**:

- top-level sections are organized by **application setting**
- each section uses a **table** with the same four columns:
  `Title`, `Main Idea`, `Time / Venue`, `Domain`
- fine-grained method details such as `block-sparse`, `token pruning`, `KV-cache`, `training-free`, and `hybrid sparse-linear` are placed in `Main Idea` and `Domain`, instead of becoming too many top-level categories

Why this structure:

- if categories are too fine, the repo becomes fragmented
- if categories are too coarse, readers cannot quickly find the key papers
- most sparse-attention papers naturally live at the intersection of **scenario** and **method type**

## Contents

- [Surveys & Foundations](#surveys--foundations)
- [Long-Context LLMs](#long-context-llms)
- [Diffusion / Video / Image Generation](#diffusion--video--image-generation)
- [Theory / Analysis](#theory--analysis)
- [Systems / Kernels / Repos](#systems--kernels--repos)
- [Contributing](#contributing)

## Surveys & Foundations

### Surveys

| Title | Main Idea | Time / Venue | Domain |
|---|---|---|---|
| [Attention in Diffusion Model: A Survey](https://arxiv.org/abs/2504.03738) | Survey of attention designs across diffusion models and modalities. | arXiv 2025.04 | survey, diffusion, attention |
| [Unveiling Redundancy in Diffusion Transformers (DiTs): A Systematic Study](https://arxiv.org/abs/2411.13588) | Systematic analysis of redundancy in DiTs, useful background for sparsification and caching. | arXiv 2024.11 | analysis, diffusion, DiT |

### Foundations

| Title | Main Idea | Time / Venue | Domain |
|---|---|---|---|
| [Sparse Transformer](https://arxiv.org/abs/1904.10509) | Early structured sparse attention with factorized/local patterns. | arXiv 2019.04 | foundation, sparse attention |
| [Reformer: The Efficient Transformer](https://arxiv.org/abs/2001.04451) | Efficient Transformer design with locality-sensitive hashing and reversible layers. | ICLR 2020 | foundation, long-context, sparse attention |
| [Longformer](https://arxiv.org/abs/2004.05150) | Sliding-window plus task-specific global attention for long documents. | arXiv 2020.04 | foundation, local-global attention |
| [Big Bird](https://arxiv.org/abs/2007.14062) | Random, local, and global sparse patterns with theoretical guarantees. | NeurIPS 2020 | foundation, sparse attention |
| [Linear Transformers Are Secretly Fast Weight Programmers](https://arxiv.org/abs/2006.16236) | Canonical linear-attention formulation relevant to later sparse-linear hybrids. | arXiv 2020.06 | foundation, linear attention |
| [Performer](https://arxiv.org/abs/2009.14794) | Kernelized linear attention with random feature approximations. | ICLR 2021 | foundation, linear attention |
| [FlashAttention](https://arxiv.org/abs/2205.14135) | IO-aware exact attention kernel that serves as the modern implementation baseline. | NeurIPS 2022 | kernel, dense baseline |

## Long-Context LLMs

### Training-Free

| Title | Main Idea | Time / Venue | Domain |
|---|---|---|---|
| [Quest](https://arxiv.org/abs/2406.10774) | Query-aware KV page selection for long-context decoding. | ICML 2024 | LLM, KV-cache, dynamic sparse |
| [Loki](https://arxiv.org/abs/2406.02542) | Uses low-rank key structure to rank and select important tokens. | NeurIPS 2024 | LLM, token selection, low-rank |
| [FlexPrefill](https://arxiv.org/abs/2502.20766) | Adaptive sparse prefill with context-aware head-wise sparsity decisions. | ICLR 2025 | LLM, prefill, adaptive sparse |
| [XAttention](https://arxiv.org/abs/2503.16428) | Block sparse attention with antidiagonal scoring for efficient block selection. | arXiv 2025.03 | LLM, block-sparse, long-context |
| [SampleAttention](https://arxiv.org/abs/2406.15486) | Structured sparse attention with CRA-based recall control for near-lossless acceleration. | arXiv 2024.06 | LLM, structured sparse, prefill |
| [Delta Attention](https://arxiv.org/abs/2505.11254) | Corrects sparse-attention distribution shift during inference. | arXiv 2025.05 | LLM, correction, sparse inference |
| [Twilight](https://arxiv.org/abs/2502.02770) | Hierarchical top-p pruning for adaptive sparse budgeting. | arXiv 2025.02 | LLM, adaptive sparse, pruning |
| [AttentionPredictor](https://arxiv.org/abs/2502.04077) | Predicts temporal attention patterns for better KV compression. | NeurIPS 2025 | LLM, KV-cache, prediction |
| [Top-Theta Attention](https://arxiv.org/abs/2502.08363) | Uses calibrated thresholds as an alternative to top-k sparsification. | arXiv 2025.08 | LLM, thresholding, sparse inference |
| [BLASST](https://arxiv.org/abs/2512.12087) | Softmax-thresholding sparse attention designed to fit FlashAttention-style kernels. | arXiv 2025.12 | LLM, kernel-aware, block-sparse |
| [SlimInfer](https://arxiv.org/abs/2508.06447) | Dynamic hidden-state token pruning with asynchronous KV management for long-context inference. | arXiv 2025.08 | LLM, token pruning, KV-cache |
| [SparseD](https://arxiv.org/abs/2509.24014) | Sparse attention for diffusion language models with head-specific patterns reused across denoising steps. | arXiv 2025.09 | diffusion LLM, sparse attention, denoising |
| [Sparse-dLLM](https://arxiv.org/abs/2508.02558) | Dynamic cache eviction and sparse attention for diffusion LLMs. | arXiv 2025.08 | diffusion LLM, KV-cache eviction, sparse attention |
| [LongCat ZigZag Attention](https://arxiv.org/abs/2512.23966) | Zigzag sparse attention for efficient context scaling up to million-token settings. | arXiv 2025.12 | LLM, long-context, sparse attention |
| [Token Sparse Attention](https://arxiv.org/abs/2602.03216) | Interleaved token selection inside attention, allowing tokens to be reconsidered later. | arXiv 2026.02 | LLM, token-sparse, dynamic |
| [Prism](https://arxiv.org/abs/2602.08426) | Spectral-aware block selection that addresses RoPE pooling blind spots. | arXiv 2026.02 | LLM, block-sparse, RoPE-aware |
| [S2O](https://arxiv.org/abs/2602.22575) | Online permutation plus early stopping to raise the practical sparsity ceiling. | arXiv 2026.02 | LLM, online permutation, early stopping |
| [FASA](https://arxiv.org/abs/2602.03152) | Frequency-aware sparse attention using dominant RoPE frequency chunks. | ICLR 2026 | LLM, query-aware, KV-cache eviction |
| [Stem](https://arxiv.org/abs/2603.06274) | Position-decayed top-k designed around causal information flow. | arXiv 2026.03 | LLM, causal sparse, prefill |
| [Scaling Attention via Feature Sparsity](https://arxiv.org/abs/2603.22300) | Explores feature-space sparsity as an additional scaling path beyond token/block sparsity. | arXiv 2026.03 | LLM, feature sparsity, efficient attention |

### Trainable / Native Sparse

| Title | Main Idea | Time / Venue | Domain |
|---|---|---|---|
| [SSA: Sparse Sparse Attention](https://arxiv.org/abs/2511.20102) | Aligns sparse and full attention outputs during training to improve native sparse models. | arXiv 2025.11 | LLM, native sparse, trainable |
| [Elastic Attention](https://arxiv.org/abs/2601.17367) | Learns to route heads between sparse and full computation at test time. | arXiv 2026.01 | LLM, adaptive routing, sparse-full hybrid |
| [vAttention: Verified Sparse Attention](https://arxiv.org/abs/2510.05688) | Combines top-k and sampling with explicit approximation guarantees. | arXiv 2025.10 | LLM, verified sparse, decoding |
| [UniSparse: A Unified Sparse Attention via Multi-Granularity Compression](https://arxiv.org/abs/2512.14082) | Composite-token framework for unified sparse attention across tasks and modalities. | arXiv 2025.12 | LLM, multi-granularity, unified sparse |
| [DeepSeek-V3](https://arxiv.org/abs/2501.12948) | Introduces DeepSeek Sparse Attention (DSA), a production-oriented sparse attention with dynamic KV compression for efficient long-context attention. | NeurIPS 2025 | LLM, long-context, native sparse |
| [NSA: Native Sparse Attention](https://arxiv.org/abs/2502.08928) | Hardware-aligned native sparse attention with optimized sparse pattern for training and inference. | arXiv 2025.02 | LLM, native sparse, hardware-aware |

## Diffusion / Video / Image Generation

### Training-Free

| Title | Main Idea | Time / Venue | Domain |
|---|---|---|---|
| [SpargeAttention](https://arxiv.org/abs/2502.18137) | Training-free sparse attention that targets language, image, and video generation models. | ICML 2025 | diffusion, generation, training-free |
| [Re-ttention: Ultra Sparse Visual Generation via Attention Statistical Reshape](https://arxiv.org/abs/2505.22918) | Uses historical softmax statistics to support very high sparsity in visual generation. | arXiv 2025.05 | visual generation, sparse attention, ultra-sparse |
| [HilbertA](https://arxiv.org/abs/2509.26538) | Reorders image tokens along Hilbert curves for 2D-aware and GPU-efficient sparse attention. | arXiv 2025.09 | image generation, sparse attention, token reordering |
| [PAROAttention](https://arxiv.org/abs/2506.16054) | Pattern-aware token reordering for sparse and quantized attention in visual generation. | arXiv 2025.06 | visual generation, sparse attention, quantization |
| [PISA: Piecewise Sparse Attention Is Wiser for Efficient Diffusion Transformers](https://arxiv.org/abs/2602.01077) | Exact-or-approximate sparse attention that keeps critical blocks exact and approximates the rest. | arXiv 2026.02 | diffusion, block-sparse, approximation |
| [Sparse VideoGen](https://arxiv.org/abs/2502.01776) | Classifies heads into spatial or temporal sparse patterns for training-free acceleration. | arXiv 2025.04 | video diffusion, training-free, spatiotemporal sparse |
| [Fast Video Generation with Sliding Tile Attention](https://arxiv.org/abs/2502.04507) | Hardware-aware sliding tile attention for efficient 3D local attention. | ICML 2025 | video diffusion, local sparse, kernel-aware |
| [DraftAttention](https://arxiv.org/abs/2505.14708) | Low-resolution draft attention guides sparse full-resolution attention. | arXiv 2025.05 | video diffusion, guided sparse, GPU-friendly |
| [GRAT: Grouping First, Attending Smartly](https://arxiv.org/abs/2505.14687) | Groups neighboring tokens and shares attendable regions for training-free acceleration. | arXiv 2025.05 | video diffusion, structured sparse, training-free |
| [RainFusion](https://arxiv.org/abs/2505.21036) | Online adaptive recognition of spatial, temporal, and textural sparse patterns. | arXiv 2025.06 | video diffusion, adaptive sparse, online profiling |
| [Sparse-vDiT](https://arxiv.org/abs/2506.03065) | Offline sparse diffusion search with per-pattern sparse kernels for video DiTs. | arXiv 2025.06 | video diffusion, sparse search, pattern-aware |
| [Astraea](https://arxiv.org/abs/2506.05096) | Token-wise acceleration framework for video diffusion transformers. | arXiv 2025.09 | video diffusion, token-wise acceleration |
| [FG-Attn](https://arxiv.org/abs/2509.16518) | Fine-grained sparsity beyond coarse block skipping for diffusion transformers. | arXiv 2025.09 | video diffusion, fine-grained sparse attention |
| [Radial Attention](https://arxiv.org/abs/2506.19852) | Static sparse attention with decaying compute density based on spatiotemporal distance. | NeurIPS 2025 | video diffusion, static sparse, subquadratic |
| [Compact Attention](https://arxiv.org/abs/2508.12969) | Adaptive tile grouping and temporal windows for structured video sparsity. | arXiv 2025.08 | video diffusion, structured sparse, hardware-aware |
| [Sparse VideoGen2](https://arxiv.org/abs/2505.18875) | Semantic-aware permutation to cluster important tokens contiguously for GPUs. | arXiv 2025.10 | video diffusion, permutation, semantic sparse |
| [LiteAttention](https://arxiv.org/abs/2511.11062) | Exploits temporal coherence of sparse patterns across denoising steps. | arXiv 2025.11 | video diffusion, temporal sparse, kernel |
| [Rectified SpaAttn](https://arxiv.org/abs/2511.19835) | Rectifies bias induced by sparse attention using implicit full-attention references. | arXiv 2025.11 | video diffusion, rectified sparse, Triton |

### Trainable / Native Sparse

| Title | Main Idea | Time / Venue | Domain |
|---|---|---|---|
| [SparseDiT](https://arxiv.org/abs/2412.06028) | Spatial-temporal token sparsification for efficient diffusion transformers. | NeurIPS 2025 | diffusion, token sparsification, DiT |
| [DiffCR: Layer- and Timestep-Adaptive Differentiable Token Compression Ratios](https://arxiv.org/abs/2412.16822) | Learns token compression ratios across layers and denoising timesteps. | CVPR 2025 | diffusion, token compression, adaptive routing |
| [Faster Video Diffusion with Trainable Sparse Attention](https://arxiv.org/abs/2505.13389) | Introduces VSA, a trainable hardware-efficient sparse attention that replaces full attention in both training and inference. | arXiv 2025.05 | video diffusion, trainable sparse, hardware-aware |
| [VORTA](https://arxiv.org/abs/2505.18809) | Routing framework that replaces dense 3D attention with specialized sparse attention variants. | NeurIPS 2025 | video diffusion, trainable sparse, routing |
| [VMoBA](https://arxiv.org/abs/2506.23858) | Mixture-of-block attention adapted to video diffusion with recurrent block partitioning and native training support. | arXiv 2025.06 | video diffusion, native sparse, block-sparse |
| [Bidirectional Sparse Attention for Faster Video Diffusion Training](https://arxiv.org/abs/2509.01085) | Dynamically sparsifies both queries and key-value blocks for faster video diffusion training. | arXiv 2025.09 | video diffusion, trainable sparse, bidirectional sparse |
| [Shiva-DiT](https://arxiv.org/abs/2602.05605) | Differentiable top-k token selection with static budgets for hardware-friendly DiT pruning. | arXiv 2026.02 | diffusion, trainable sparse, token pruning |
| [SpargeAttention2](https://arxiv.org/abs/2602.13515) | Trainable sparse attention with hybrid top-k/top-p masking and distillation fine-tuning. | arXiv 2026.02 | diffusion, trainable sparse, hybrid masking |

### Hybrid Sparse-Linear / Structured Attention

| Title | Main Idea | Time / Venue | Domain |
|---|---|---|---|
| [SLA: Beyond Sparsity in Diffusion Transformers via Fine-Tunable Sparse-Linear Attention](https://arxiv.org/abs/2509.24006) | Sparse-linear decomposition of attention with lightweight fine-tuning. | arXiv 2025.09 | diffusion, sparse-linear, hybrid attention |
| [Attention Surgery: An Efficient Recipe to Linearize Your Video Diffusion Transformer](https://arxiv.org/abs/2509.24899) | Distills pretrained video diffusion models into linear or hybrid attention variants. | arXiv 2025.11 | video diffusion, hybrid attention, linearization |
| [ReHyAt: Recurrent Hybrid Attention for Video Diffusion Transformers](https://arxiv.org/abs/2601.04342) | Hybrid softmax-linear attention with recurrent chunk-wise formulation. | arXiv 2026.01 | video diffusion, hybrid attention, linear memory |
| [SALAD: Achieve High-Sparsity Attention via Efficient Linear Attention Tuning for Video Diffusion Transformer](https://arxiv.org/abs/2601.16515) | Adds a lightweight linear branch to support higher sparse ratios with limited fine-tuning. | arXiv 2026.01 | video diffusion, sparse-linear, trainable |
| [SLA2: Sparse-Linear Attention with Learnable Routing and QAT](https://arxiv.org/abs/2602.12675) | Learnable routing and quantization-aware tuning for stronger sparse-linear attention. | arXiv 2026.02 | video diffusion, sparse-linear, routing |
| [VMonarch](https://arxiv.org/abs/2601.22275) | Structured attention with Monarch matrices for sparse spatiotemporal patterns. | arXiv 2026.01 | video diffusion, structured attention, Monarch |
| [MonarchRT](https://arxiv.org/abs/2602.12271) | Real-time video generation with expressive structured sparse attention. | arXiv 2026.02 | video generation, structured sparse, real-time |
| [Switch Attention: Towards Dynamic and Fine-grained Hybrid Transformers](https://arxiv.org/abs/2603.26380) | Dynamically switches between full attention and sliding-window attention. | arXiv 2026.03 | efficient attention, hybrid attention, dynamic routing |

### Pipelines / Serving / Unified Acceleration

| Title | Main Idea | Time / Venue | Domain |
|---|---|---|---|
| [BLADE](https://arxiv.org/abs/2508.10774) | Jointly combines block-sparse attention and step distillation for efficient video generation. | arXiv 2025.08 | video diffusion, block-sparse, step distillation |
| [USV](https://arxiv.org/abs/2512.05754) | Joint sparsification over attention, token merging, and denoising steps. | arXiv 2025.12 | video diffusion, unified sparsification, end-to-end |
| [Block Cascading](https://arxiv.org/abs/2511.20426) | Training-free block-parallel generation for block-causal video models. | arXiv 2025.11 | video generation, parallel inference, block-causal |
| [TIMERIPPLE](https://arxiv.org/abs/2511.12035) | Accelerates vDiTs by modeling latent spatio-temporal correlations. | arXiv 2025.11 | video diffusion, correlation-aware acceleration |
| [HiStream](https://arxiv.org/abs/2512.21338) | Streaming framework with spatial, temporal, and timestep compression for high-resolution video generation. | arXiv 2025.12 | video generation, streaming, compression |
| [RainFusion2.0](https://arxiv.org/abs/2512.24086) | Hardware-efficient sparse attention with low-overhead pattern prediction for video and image generation. | arXiv 2025.12 | diffusion, sparse attention, hardware-aware |
| [StreamDiffusionV2](https://arxiv.org/abs/2511.07399) | Serving-oriented streaming system for interactive video generation with rolling KV cache and pipeline orchestration. | arXiv 2025.11 | video generation, serving, KV-cache |
| [Jenga: Training-Free Efficient Video Generation via Dynamic Token Carving](https://arxiv.org/abs/2505.16864) | Combines dynamic attention carving with progressive resolution generation. | NeurIPS 2025 | video diffusion, dynamic token carving, pipeline |

## Theory / Analysis

| Title | Main Idea | Time / Venue | Domain |
|---|---|---|---|
| [The emergence of sparse attention: impact of data distribution and benefits of repetition](https://arxiv.org/abs/2505.17863) | Studies when sparse attention patterns emerge during training and why repetition helps. | NeurIPS 2025 | theory, emergence, sparse attention |
| [Why Attention Patterns Exist: A Unifying Temporal Perspective Analysis](https://arxiv.org/abs/2601.21709) | Temporal perspective for explaining predictable versus unpredictable attention patterns. | arXiv 2026.01 | analysis, attention patterns, LLM |

## Systems / Kernels / Repos

### Implementation Repos

| Title | Main Idea | Time / Venue | Domain |
|---|---|---|---|
| [flash-attention](https://github.com/Dao-AILab/flash-attention) | Core dense attention kernel baseline used by most modern sparse-attention work. | Repo | kernel, baseline |
| [Block-Sparse-Attention](https://github.com/mit-han-lab/Block-Sparse-Attention) | MIT Han Lab repository for block-sparse attention kernels and related efficient-attention work. | Repo | kernel, block-sparse |

## Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](./CONTRIBUTING.md) before opening a PR.

The default entry format is:

```md
| [Paper Title](link) | One-line main idea. | ICLR 2025 / arXiv 2026.03 | LLM, block-sparse, training-free |
```
