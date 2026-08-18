<mark style="background: #FFB8EBA6;">Reviewer 1</mark>
The necessity of pairwise counterfactual drift analysis is unclear. The authors pair each neutral-prompt generation with its disability-conditioned counterpart and measure the attribute flip rate to quantify pairwise counterfactual drift. However, if the model yields the same gender proportions with and without the disability condition, one can already conclude that the disability condition does not substantially affect gender. It would be helpful if the paper clarified what additional insight into model bias pairwise counterfactual drift provides beyond what distributional representational shift already captures.

Solution: 

For SD and FLUX, the authors use matched generation seeds to control randomness, whereas for Nano Banana 2 they instead fix the sampling temperature. It is unclear whether fixing the temperature is sufficient to control randomness in a comparable way. If randomness is not properly controlled, measuring the attribute flip rate over paired samples does not appear meaningful.

Solution: Randomness PIpeline

The authors first obtain attribute labels for the generated images using a VLM and then have two human annotators verify them. However, judgments about affective framing and social agency are likely to be heavily influenced by annotator bias and subjectivity. Involving additional annotators and reporting annotator agreement may improve the reliability of these labels.

Solution: Inter Annotator score and vlm+ human score

Remarks for changes before resubmission:
1. annotation
2. seed matching explanation in case of nanobanana
3. reasoning for counterfactual drift 

<mark style="background: #FFB8EBA6;">Reviewer 2</mark>

Remarks before submission:

 - The authors should either adopt an identity-preserving generation/editing method and quantitatively verify identity similarity, or consistently reframe the study as measuring disability-conditioned output drift under shared noise rather than changes to the “same person.”
    
- The revision should separate instability from harm by comparing outputs against an explicit normative or empirical reference distribution. It should acknowledge that movement away from the neutral baseline is not inherently unfair when that baseline is already stereotyped.
    
- The refusal experiments should include prompt paraphrases and matched controls involving non-disability medical diagnoses, emotionally sensitive language, and safety-associated terms. Refusal reasons should be categorized where possible, and the “algorithmic erasure” claim should be moderated unless disability-specific causation is established.
  
<mark style="background: #FFB8EBA6;">Reviewer 3 </mark>

Expansion of human in loop validation 

