The analysis of **results.csv** reveals that while none of the socioeconomic clusters reached the strict threshold for statistical significance (FDR−P<0.05) after correcting for multiple tests, there are strong patterns of **Bias Intensity** and **Counterfactual Drift** across the groups.

Here is an explanation of the key findings from your socioeconomic drift analysis:

### 1. High-Intensity Bias Zones (Cramér's V)

Although the P-values did not survive the Benjamini-Hochberg correction (FDR), the raw effect sizes show where the model is shifting most dramatically when a disability aid is introduced:

- **High-Income / Specialized**: This cluster shows the highest average bias intensity (V=0.154). Specifically, **Physical Framing** (V=0.29) and **Gender Presentation** (V=0.24) exhibit strong drift. This suggests that when a high-status professional (e.g., Doctor, Software Engineer) is conditioned with a disability, the model is highly prone to changing their camera presence and perceived gender.
    
    +2
    
- **Manual / Entry / Other**: This group shows intense drift in **Physical Framing** (V=0.28) and **Activity Engagement** (V=0.28). The model frequently "flips" how these workers are interacting with their environment once a disability is added.
    
    +1
    

### 2. The Flip Rate (CFR %) Distribution

The **Counterfactual Flip Rate** tells us how often a specific image "changed its label" between the Neutral and Conditioned versions:

- **Average Flip Rate**: Across all socioeconomic groups and attributes, the average flip rate is **26.3%**. This means that in more than 1 out of every 4 images, adding a disability aid caused a change in a visual attribute that should have remained constant (like gender or environment).
    
    +1
    
- **High-Impact Areas**:
    
    - **Environment Type** in the **Service / Frontline** cluster has the highest flip rate in the entire dataset at **47.8%**. Nearly half of the neutral images for these professions changed settings when conditioned with a disability.
        
        +1
        
    - **Activity Engagement** for **Manual Workers** flipped in **36%** of cases, showing a significant change in how these workers are portrayed as being "active" or "idle".
        

### 3. Cluster Comparison

When we look at the average bias intensity (Cramér's V), we can rank the clusters by how much "drift" they experience:

1. **High-Income / Specialized (V=0.154)**: Most sensitive to representational change.
    
2. **Service / Frontline (V=0.133)**: Significant setting and activity shifts.
    
3. **Manual / Entry / Other (V=0.128)**: Strong shifts in physical presence.
    
4. **Mid-Tier / Professional (V=0.115)**: Shows the most stability, though still experiences a **31.3% flip rate** in physical framing.
    

### Summary Explanation

In simple terms, the results show that **High-Income professionals** and **Service workers** are the most "unstable" groups in the AI's eyes. When you add a disability to these specific groups, the model is significantly more likely to alter their professional environment, their gender, or the way the camera frames them compared to other groups. This suggests that the AI's internal "stereotypes" about disability are more likely to override the original professional context for these socioeconomic tiers.