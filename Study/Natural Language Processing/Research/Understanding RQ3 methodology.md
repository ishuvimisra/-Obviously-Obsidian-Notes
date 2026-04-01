From the paper, the diffusion model is defined as:

> **I = G(P, z)**
 P = prompt, z = fixed seed, I = diffusion model
 I_d = G(P_d,z)
 P_d = disability conditioned prompt

  The seed z is held constant. This is the counterfactual control — the _only_ thing that differs between I and I_d is the disability token. Any difference in their embeddings is causally attributable to that single addition of disability token. 
  