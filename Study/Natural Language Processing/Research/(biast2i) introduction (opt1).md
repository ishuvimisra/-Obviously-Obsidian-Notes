
The measurement of generative AI fairnes has been done before, mostly, by who appears in an image. Does the doctor look like a woman? Does the engineer appear to be of African descent? These are necessary questions of course, but they are not sufficient ones.

(change para1 is it too cliche? reread w pragyan)

Consider what happens when one prompts a state-of-the-art T2I model with: "A 45-year-old software engineer with a mental health condition." A model that passes every gender-parity benchmark might generate a technically competent image- and yet shift systematically from a masculine-presenting professional toward a feminine-presenting subject with negative affective sentiment and constricted, hunched posture. The bias is not simply in the demographic output. It is in the combination of who appears and how they are rendered.

 Alignment techniques- including Reinforcement Learning from Human Feedback (RLHF) [1] and automated prompt rewriting [2]- have become effective at satisfying the specific tests they are usually trained against. Models learn to produce gender-balanced outputs and racially diverse outputs. But these optimizations are evaluated over marginal identities, not intersectional ones. When disability enters the promt space along side professional co ntexts, models encounter a representational distribution outside the regions their alignment procedures target. The result is not improved fairness- as in them the surface metrics are satisfied while structural distotion increase.

Disability is one of the the least-studied axes in AI fairness research [3]. Existing T2I bias literature focuses overwhelmingly on gender [4] and race [5]. Disability, when studied, is treated as a unidimensional variable often evaluated on descriptive rather than professional prompts. We are not aware of prior work systematically examining how disability conditions, across mobility, vision, hearing, and mental health subtypes, interact with professional contexts to produce qualitatively distinct failure modes.

We hypothesize that when disability conditions are introduced into professional T2I prompts they act as an intersectional stress test revealing generational bias architecture: that standard diffusion architectures produce overt stereotyping; that modern aligned models exhibit demographic drift and contextual distortion that evades coarse parity metrics; and that commercial, policy-constrained models produce selective refusal  <mark style="background: #FFF3A3A6;">(remind pragyan that we have to go through the erasure images and then find one to write an example )</mark>- a failure mode that is itself a form of exclusion.

 This paper makes the following contributions:

1. We introduce the **DCDD framework**: a paired counterfactual audit methodology for evaluating disability-conditioned representational drift in T2I models.

2. We operationalize a **9-dimensional VLM extraction pipeline** with human-in-the-loop validation for sociotechnical image attributes.

3. We identify and formally characterize three evolutionary bias paradigms — **Explicit Stereotyping**, **Counterfactual Demographic Drift**, and **Algorithmic Erasure** — across three generations of model architecture and alignment philosophy.

<mark style="background: #FFF3A3A6;"><mark style="background: #FFF3A3A6;">4. We demonstrate that FLUX.1 Dev's alignment produces systematic White-Feminine demographic drift under disability conditioning- a finding invisible to standard fairness benchmarks.</mark> </mark>

(not sure )
 5We introduce the **CFR-V Dissociation** as a formal critique of surface-level fairness metrics in T2I evaluation.