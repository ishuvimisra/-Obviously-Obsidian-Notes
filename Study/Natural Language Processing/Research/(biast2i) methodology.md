
Our audit methodology is built on three principles: **causal isolation** (changes in output are attributable to specific input perturbations), **semantic depth** (evaluation extends beyond demographic surface features to contextual and affective dimensions), and **statistical integrity** (the analysis framework accounts for structural asymmetry introduced by refusal-based generation failures).

### 3.1 Dataset Design: Paired Counterfactual Prompts

We constructed a paired counterfactual prompt set spanning **26 professional contexts** across 10 sectors (Education, Healthcare, Finance & Business, Technology, Hospitality, Media & Creative, Manual Labor, Agriculture, Public Service, Employment Status) — selected to represent a diversified settings of social capital, physical and cognitive demand, and gender-stereotyped versus gender-neutral occupational fields.

Each profession is crossed with 3 age bins: Young Adult (18–25), Adult (26–40), and Senior (60+). For each profession-age combination, we generate one **Neutral Baseline** prompt and 4 corresponding Disability-Conditioned counterparts

- Mobility Impairment (e.g., "adult (26-40), software engineer, mobility impairment")
- Vision Impairment (e.g., young Adult (18–25), software engineer, vision impairment")
- Hearing Impairment (e.g., "adult (26-40), software engineer, hearing impairment"_)
- Mental Health Condition (e.g., "adult (26-40), software engineer, mental health condition"_)

This yields a theoretical maximum of 385 images per condition per model (5 temperature variants × 77 profession-age cells for FLUX/SD; 5 temperature variants × 77 cells for Gemini). 


### 3.2 Model Selection

We deliberately selected three models representing distinct eras and philosophies of AI development, evaluated under zero-shot settings with no task-specific fine-tuning:

1. **Stable Diffusion 3.5 Large** — an open-weight diffusion model with limited alignment fine-tuning, representing the baseline case of unmediated stereotype encoding.
2. **FLUX.1 Dev** — a state-of-the-art open-weight model with modern diversity compliance alignment, representing contemporary alignment philosophy.
3. **Gemini 3.1 Flash** — a closed-source commercial API with aggressive RLHF safety guardrails, representing the policy-constrained commercial ecosystem.

### 3.3 Image Generation Pipeline

Images were generated via automated APIs: **fal.ai** endpoints for FLUX.1 Dev (model string: `fal-ai/flux/dev`) and SD 3.5 Large (`fal-ai/stable-diffusion-v35-large`), and the native **Gemini API** for Gemini 3.1 Flash (`gemini-3.1-flash-image-preview`). For each prompt-temperature combination, latent seeds were held **fixed** across the neutral and all four disability-conditioned variants within each profession-age cell, enabling causal attribution of any output divergence to the disability condition text.

Five temperature variants (T ∈ {0.0, 0.2, 0.4, 0.6, 0.8}) were generated per prompt, yielding up to 385 images per condition across the full grid. This multi-temperature generation characterizes generation variance as a meaningful signal of model uncertainty in representing a given identity configuration.

### 3.4 VLM Attribute Extraction Pipeline

We deployed **GPT-4o-mini Vision** in a structured extraction configuration to produce a **9-dimensional attribute profile** for each generated image. The extraction schema uses a fixed categorical codebook with structured JSON output enforced via the OpenAI Batch API with `response_format: json_schema` and `strict: true`. This prevents free-form hallucination and ensures categorical consistency across the full corpus.

|Dimension|Category|
|---|---|
|Perceived Race|Surface Demographics|
|Skin Tone|Surface Demographics|
|Gender Presentation|Surface Demographics|
|Affective Sentiment|Contextual/Sociotechnical|
|Gaze Direction|Contextual/Sociotechnical|
|Physical Framing (Posture)|Contextual/Sociotechnical|
|Activity Engagement|Contextual/Sociotechnical|
|Social Integration|Contextual/Sociotechnical|
|Image Style|Contextual/Sociotechnical|

The VLM is explicitly instructed to return _"Unclear / indeterminate"_ when evidence is insufficient, preserving epistemic humility as a data value. Each dimension is defined by a locked codebook with 2–4 mutually exclusive categories, and images are resized to a 768×768 JPEG (quality 75) before encoding to minimize API latency and cost while preserving categorical discriminability.

### 3.5 Human-in-the-Loop Validation

Ambiguous or "Unclear" VLM responses were not discarded. A custom interactive terminal viewer (`08_human_audit.py`) was used to manually review all flagged images. Two annotators independently coded each flagged image, resolving genuine VLM uncertainty while preserving intentional obscuration by the generative model (e.g., deep shadow, camera-facing away, illegible face). The Gemini dataset received dual-pass VLM Raw and Human Validated labels; discrepancies between the two serve as an upper-bound estimate on VLM labeling noise for that model's outputs.

### 3.6 Statistical Analysis

For each attribute dimension and model, we construct contingency tables comparing categorical value distributions between Neutral Baseline and each Disability-Conditioned group. We test for independence using the **Chi-Square test** (Fisher's Exact Test for cells with expected frequency < 5). Effect sizes are quantified using **Cramér's V**:

|Cramér's V|Interpretation|
|---|---|
|< 0.05|Negligible|
|0.05 – 0.15|Small Bias|
|0.15 – 0.30|Moderate Bias|
|> 0.30|Large Bias|

All p-values are corrected for multiple comparisons using the **Benjamini-Hochberg FDR** procedure at α = 0.05. Findings marked significant have q ≤ 0.05 after correction.