# Grid Distillation — CVPR 2026 Project Page

**Grid Distillation: Compositional Image Distillation via Structured Generative Grids**

> Biplab Ch Das¹·² · Shouvik Das¹ · Viswanath Gopalakrishnan²
>
> ¹Samsung R&D Institute, Bangalore · ²IIIT Bangalore
>
> *This work is part of Biplab Ch Das's PhD research at IIIT Bangalore.*
> *Project page prepared by Shouvik Das.*

---

## 🔗 Links

| Resource | Link |
|----------|------|
| 🌐 Project Page | [shouvikdas-2611.github.io/Grid-Distillation](https://shouvikdas-2611.github.io/Grid-Distillation/) |
| 📄 Paper (PDF) | [Camera-Ready Paper](https://shouvikdas-2611.github.io/Grid-Distillation/static/pdfs/paper.pdf) |
| 📋 Poster | [CVPR 2026 Poster](https://shouvikdas-2611.github.io/Grid-Distillation/static/pdfs/poster.pdf) |
| 🔍 OpenReview | [vUHnPazM2j](https://openreview.net/forum?id=vUHnPazM2j) |
| 💻 Code | Coming Soon |

---

## 📖 Abstract

We present **Grid Distillation**, a generative dataset distillation framework that compresses
large-scale datasets into a compact set of informative synthetic samples. Our method constructs
high-resolution compositional grids via **spectral submodular optimization**, which injects world
knowledge from CLIP representations to maximize semantic coverage and diversity. These grids are
then downsampled into low-resolution distilled images optimized for diversity and representational
efficiency. During training, a **single-step diffusion reconstruction** (based on Stable Diffusion
Turbo) restores fine-grained spatial details from diffusion priors, bridging the gap between compact
representations and natural image statistics. A **grid-aware cropping strategy** further enhances
discriminability by probabilistically aligning crops with grid boundaries, maintaining compatibility
with standard 224×224 inference inputs. Experiments on ImageWoof, ImageNette, ImageIDC, ImageNet-1K,
and UCF-101 demonstrate consistent improvements over existing dataset distillation methods across
multiple IPC settings.

---

## 🏆 Key Results

| Benchmark | IPC | Backbone | Ours | Prev. SOTA (VLCP) | Gain |
|-----------|-----|----------|------|-------------------|------|
| ImageWoof | 10 | ResNet-18 | **65.5%** | 39.9% | +25.6 pp |
| ImageWoof | 50 | ResNet-18 | **84.3%** | 58.9% | +25.4 pp |
| ImageNette | 10 | ResNetAP-10 | **83.3%** | 64.8% | +18.5 pp |
| ImageNet-1K | 10 | ResNet-18 | **50.0%** | 46.7% | +3.3 pp |
| UCF-101 | 1-shot | ResNet-50 | **73.9%** | 66.8% (LDC) | +7.1 pp |

---

## 🛠️ Method Overview

Grid Distillation operates in three stages:

1. **Spectral Submodular Grid Selection (SSDIM)** — Selects L² exemplars via a principled
   submodular objective over CLIP embeddings, jointly maximizing coverage (α=1.0),
   diversity (β=0.6), and spectral informativeness (γ=0.3).

2. **Single-Step Diffusion Detail Reconstruction** — Adapts InvSR's diffusion inversion
   with Stable Diffusion Turbo and class-conditioned prompts to restore fine-grained
   spatial details lost during downsampling. Adds only +16.9% one-time overhead.

3. **Grid-Aware Cropping Strategy** — Mixes grid-aligned crops (p=0.6) with random
   crops (p=0.4) during training, maintaining full compatibility with standard
   224×224 inference inputs.

### Hyperparameters (fixed across all datasets)

| α | β | γ | L | p_align | r |
|---|---|---|---|---------|---|
| 1.0 | 0.6 | 0.3 | 4 | 0.6 | 32 |

---

## 📁 Repository Structure

```
Grid-Distillation/
├── index.html              # Main project page
├── static/
│   ├── css/                # Bulma + FontAwesome CSS
│   ├── js/                 # Bulma carousel + FontAwesome JS
│   ├── images/
│   │   ├── teaser.png      # Figure 1 — qualitative comparison
│   │   ├── pipeline.png    # Figure 2 — SSDIM pipeline
│   │   ├── submodular_effect.png  # Figure 3 — random vs SSDIM grid
│   │   ├── cropping.png    # Figure 4 — grid-aware cropping
│   │   └── poster_thumb.png
│   ├── videos/
│   │   └── demo_compressed.mp4
│   └── pdfs/
│       ├── paper.pdf
│       └── poster.pdf
└── README.md
```

---

## 📜 BibTeX

```bibtex
@inproceedings{das2026griddistillation,
  title     = {Grid Distillation: Compositional Image Distillation
               via Structured Generative Grids},
  author    = {Das, Biplab Ch and Das, Shouvik and
               Gopalakrishnan, Viswanath},
  booktitle = {Proceedings of the IEEE/CVF Conference on
               Computer Vision and Pattern Recognition (CVPR)},
  year      = {2026}
}
```

---

## 📬 Contact

| Author | Email |
|--------|-------|
| Biplab Ch Das | biplab.das@iiitb.ac.in |
| Shouvik Das | shouvik.das@samsung.com |
| Viswanath Gopalakrishnan | viswanath.g@iiitb.ac.in |

---

## 🙏 Acknowledgements

This project page was built using the
[Academic Project Page Template](https://github.com/eliahuhorwitz/Academic-project-page-template)
adopted from [Nerfies](https://nerfies.github.io).
Licensed under [CC BY-SA 4.0](http://creativecommons.org/licenses/by-sa/4.0/).
