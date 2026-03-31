# Contributing

This repository is curated around a simple rule:

- **top-level sections follow scenario**
- **method details go into table columns**

That means we do **not** create a new top-level category for every method keyword such as `block-sparse`, `token pruning`, `KV cache`, `training-free`, or `hybrid sparse-linear`.

## Current taxonomy

The current top-level structure is:

- Surveys & Foundations
- Long-Context LLMs
- Diffusion / Video / Image Generation
- Theory / Analysis
- Systems / Kernels / Repos

Inside a section, if the list becomes too long, it is better to add a **small number of subgroups** such as:

- `Training-Free / Inference-Time`
- `Trainable / Native Sparse`
- `General Sparse Attention for DiTs`
- `Video Generation`
- `Hybrid Sparse-Linear / Structured Attention`

Do not split further unless the subgroup is already crowded.

## What to add

Please add papers/resources whose main contribution is one of the following:

- sparse attention
- native or trainable sparse attention
- token / block / KV sparsification
- long-context LLM attention acceleration
- sparse attention for diffusion, image generation, or video generation
- sparse-linear or strongly related hybrid efficient attention

Linear-attention-only papers are welcome when they are:

- foundational, or
- directly useful for understanding modern sparse/hybrid attention work

## What not to add

Please avoid adding:

- generic pruning or compression papers without an attention-specific contribution
- papers where sparse attention is only a minor implementation detail
- duplicate entries across multiple sections unless there is a very strong reason
- highly speculative entries without a public paper, repo, or project page

## Entry format

All paper sections should use the same four columns:

- `Title`
- `Main Idea`
- `Time / Venue`
- `Domain`

Recommended row format:

```md
| [Paper Title](paper link) | One-line main idea. | ICLR 2025 / arXiv 2026.03 | LLM, block-sparse, training-free |
```

Guidelines for each column:

- `Title`: prefer arXiv, official publication, or project page links
- `Main Idea`: keep it to one sentence and make the core contribution obvious
- `Time / Venue`: use a venue if confirmed; otherwise use `arXiv YYYY.MM`
- `Domain`: use short tags such as `LLM`, `KV-cache`, `block-sparse`, `video diffusion`, `hybrid sparse-linear`

Domain style:

- use lowercase tags by default
- keep established acronyms and proper names capitalized, such as `LLM`, `KV-cache`, `DiT`, `RoPE-aware`, `GPU-friendly`, `Triton`, `Monarch`
- prefer hyphenated compounds when they are standard, such as `block-sparse`, `token-sparse`, `long-context`, `kernel-aware`, `hardware-aware`, `query-aware`

## Classification rule

When deciding where a paper belongs:

1. classify by **main scenario** first
2. use `Main Idea` and `Domain` to encode the method details
3. if a paper fits multiple places, put it where a reader is most likely to look for it first

Examples:

- a paper on KV-cache sparsification for long-context reasoning goes to `Long-Context LLMs`
- a paper on sparse attention for Wan / Hunyuan / CogVideo goes to `Diffusion / Video / Image Generation`
- a paper mainly explaining why attention patterns emerge goes to `Theory / Analysis`

## Pull request checklist

Before opening a PR, please check:

- the paper is in the right top-level section
- the row uses the four standard columns
- the link works
- the one-line summary is accurate and not promotional
- `Time / Venue` is correct
- `Domain` uses short, readable tags

## Good future additions

These additions would improve the repo without making it messy:

- venue normalization across all rows
- benchmark-focused tables for `LongBench`, `RULER`, `VBench`, and related suites
- a compact taxonomy figure or timeline
- a bilingual companion such as `README.zh-CN.md`
