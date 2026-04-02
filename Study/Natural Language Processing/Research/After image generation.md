Stage 1 ATTRIBUTE EXTRACTION 
every image through ==GPT 4o== to get structured labels
Input: tightly engineered prompt
output: JSON structure (just classification)
what to expect as output: ![[Pasted image 20260402150402.png]]
 **Stage 2 — CLIP Embeddings (RQ3)** 
 Run every image through CLIP ViT-L/14 
 we get a vector per image
 Compute cosine similarity for every neutral–disability pair sharing the same seed
 output: ∆rep values per profession.

RQ1 
Three parallel computations, all in pure Python/scipy:

- **RQ1:** Take the GPT-4o labels from Stage 1
-compute normalized Shannon entropy per attribute dimension separately for neutral and disability-conditioned image
calculate ∆H 
will tell if disability conditioning reduces representational diversity.

- **RQ2:** Convert categorical labels to ordinal scores 
-compute ∆D per pair per attribute dimension
-run paired Wilcoxon signed-rank tests with Bonferroni correction
-Tells you which specific attributes drift and by how much.
- **RQ3:** Take the cosine similarities from Stage 2, compute ∆rep = baseline − disability similarity, run statistical tests. Tells you if identity shifts at the latent level beyond what's visible. 