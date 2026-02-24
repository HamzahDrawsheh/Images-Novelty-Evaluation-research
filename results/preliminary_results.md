# Preliminary Experimental Results

## Overview

We conducted an initial evaluation of SDXL using four semantic prompt categories:

- Realistic
- Attribute Violation
- Physical Law Violation
- Conceptual Visual Abstraction

Each prompt generated 4 images (total: 80 images).
We evaluated performance using three metrics:

- CLIP Alignment
- Intra-Prompt Diversity
- Approximate Novelty (CLIP-space distance from CIFAR-10 baseline)

---

## Results

| Level | CLIP Score | Diversity | Approx Novelty |
|-------|------------|------------|----------------|
| Realistic | 0.3125 | 0.0967 | 0.4574 |
| Attribute | 0.3124 | 0.1157 | 0.4250 |
| Physical | 0.3107 | 0.1380 | 0.4373 |
| Conceptual | 0.3215 | 0.1249 | 0.4487 |

---

## Observations

### 1. Alignment

Contrary to expectations, CLIP alignment did not significantly decrease with increased semantic constraint violations.

The Conceptual category even achieved slightly higher alignment than the Realistic baseline.

This suggests that SDXL maintains strong semantic coherence even under abstract or physically impossible prompts.

---

### 2. Diversity

Intra-prompt diversity increased consistently with semantic constraint violation:

Realistic < Attribute < Conceptual < Physical

This indicates that ambiguity and physical violations introduce greater generative variability.

This finding aligns with the hypothesis that semantic uncertainty increases sample dispersion in embedding space.

---

### 3. Novelty

Approximate novelty differences across categories were relatively small.

This suggests that the CIFAR-10 baseline may be insufficient as a robust novelty reference for high-resolution diffusion outputs.

---

## Why the Trade-Off Hypothesis Did Not Strongly Emerge

Our original hypothesis assumed a clear trade-off:

Higher Novelty → Lower Alignment

However, this relationship was not strongly observed.

Possible explanations:

1. CLIP embedding space may not sharply distinguish between realistic and abstract violations.
2. CIFAR-10 is a weak novelty baseline relative to SDXL's distribution.
3. Sample size (4 images per prompt) may be insufficient.
4. SDXL may genuinely preserve alignment under semantic abstraction.

---

## Limitations

- Small sample size
- Single model (SDXL only)
- Weak novelty baseline (CIFAR-10)
- No statistical significance testing
- No human evaluation

---

## Conclusion

The preliminary experiment reveals:

- Strong robustness of SDXL alignment under semantic violations.
- Increased diversity with physical constraint violations.
- Limited observable trade-off between alignment and novelty under current metrics.

These findings motivate a refined experimental design in future iterations.
