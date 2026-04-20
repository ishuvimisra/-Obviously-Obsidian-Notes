![[Pasted image 20260420133540.png]]
For a fairness audit, you want to prove a causal relationship: _If I change X (disability status), then Y (image attributes) changes._ By using counterfactual pairs with a fixed seed, you ensure that the **starting Gaussian noise** in the diffusion process is identical. Any drift in the resulting CLIP embeddings or visual features can be attributed more directly to the model's internal biases regarding that specific disability token.

In modern diffusion models, the Cross-Attention mechanism maps specific words to specific pixels.

- In **Process 1**, the "software engineer" part of the prompt will likely activate similar regions in both images.
    
- The "wheelchair" token will then force a localized drift in the attention map. This allows you to calculate the **Demographic Drift** by measuring the distance between the two resulting vectors in a shared embedding space (like CLIP).