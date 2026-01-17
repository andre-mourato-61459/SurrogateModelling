## Major Comments

### Response 1: Young's Modulus Sampling U(1,4) MPa

**Insight:** The reviewer wants to understand the rationale—is this for data augmentation or physiological representativeness?

**Suggested response strategy:**
- Reference [35] (Duprey et al., 2010) already cited supports this range for ATAA tissue
- Clarify the dual purpose: (1) capture inter-patient variability in stiffness, and (2) ensure sufficient coverage of the input space for robust training
- Acknowledge the limitation that uniform sampling doesn't reflect the true population distribution

**Draft response:**
> Thank you for this pertinent question. The uniform distribution U(1,4) MPa was chosen based on experimental characterisation of ascending thoracic aortic aneurysm tissue by Duprey et al. [35], who reported physiological and maximum elastic moduli within this range. The sampling strategy serves a dual purpose: (i) to represent the documented inter-patient variability in aortic wall stiffness, and (ii) to ensure adequate coverage of the input space for robust surrogate model training. We acknowledge that uniform sampling does not reflect the true population distribution, which is a limitation we now address in the revised Discussion section.

**Manuscript modification:** Add a sentence in Section 2.4 clarifying this rationale.

---

### Response 2: Figure 3 Clarity

**Insight:** This is a valid criticism—the figure lacks a legend explaining A, B, C, D labels.

**Suggested response strategy:**
- Add a proper legend explaining that A, B, C, D represent cases with decreasing agreement levels (shown in detail in Figs. 4–5)
- Consider adding histograms or box plots showing error distributions
- Add summary statistics (mean, median, percentiles) either in the figure or a companion table

**Draft response:**
> We thank the reviewer for highlighting this deficiency. The labels A, B, C, and D correspond to representative test cases illustrating very high, high, moderate, and low agreement levels, respectively, which are detailed in Figures 4 and 5. We have revised Figure 3 to include: (i) a clear legend explaining these labels, (ii) marginal histograms showing the distribution of NMAE and R values, and (iii) added Table X summarising the distribution statistics (mean, median, interquartile range) for both metrics.

**Manuscript modification:** Revise Figure 3 with legend and consider adding marginal histograms or a summary statistics table.

---

### Response 3: "Big" and "Small" Curvature (BC/SC)

**Insight:** The terminology may be confusing. In aortic anatomy, the terms "greater curvature" and "lesser curvature" are more standard.

**Suggested response strategy:**
- Clarify that BC refers to the outer/convex curvature (greater curvature) and SC to the inner/concave curvature (lesser curvature)
- Reference standard anatomical nomenclature
- Consider changing terminology to standard terms

**Draft response:**
> We appreciate this observation. The terms "big curvature" (BC) and "small curvature" (SC) refer to the outer (convex) and inner (concave) aspects of the ascending aorta, respectively. These correspond to the "greater curvature" and "lesser curvature" in standard anatomical nomenclature. We have revised the manuscript to adopt the more widely accepted terminology and added a clarifying statement with appropriate anatomical references.

**Manuscript modification:** Replace BC/SC with "greater curvature" and "lesser curvature" throughout, or add clear definitions.

---

### Response 4: Mesh Convergence Study

**Insight:** This is a standard requirement for FEM-based studies. The reviewer expects evidence of mesh independence.

**Suggested response strategy:**
- If a convergence study was performed, present it (even briefly or in supplementary material)
- If not, acknowledge this limitation and justify the mesh density based on literature or practical considerations
- Reference the mesh specifications (n = 1354 elements)

**Draft response (if study was done):**
> A mesh convergence study was conducted during the development of the numerical pipeline. Three mesh densities were tested (coarse: ~700 elements, medium: ~1350 elements, fine: ~2700 elements), and the relative difference in peak stress between the medium and fine meshes was below 3%. The medium mesh (n = 1354 elements) was selected as a compromise between accuracy and computational efficiency for the large-scale simulation campaign. These details have been added to Section 2.4 and supplementary material.

**Draft response (if study was not done):**
> We acknowledge that a formal mesh convergence study was not presented in the original manuscript. The mesh density (n = 1354 surface elements) was selected based on preliminary analyses and is consistent with similar studies in the literature [cite relevant works]. We have now included a mesh sensitivity analysis in the revised manuscript/supplementary material demonstrating that the chosen discretisation provides mesh-independent results within acceptable tolerance.

**Manuscript modification:** Add mesh convergence results (ideally perform if not done).

---

### Response 5: Aggregated Performance Assessment & Error-Input Correlation

**Insight:** This is a two-part critique:
1. No global summary statistics over the full dataset
2. Section 3.3 interpretation about error-input correlation is speculative without analysing training data distribution

**Suggested response strategy:**

**Part A - Global statistics:**
- Add a summary table with: mean, std, median, IQR, percentiles for NMAE and R
- Include aggregate metrics (e.g., R² over all predictions vs targets)
- Consider a parity plot (predicted vs. target) for the entire dataset

**Part B - Training data distribution:**
- Analyse and present the distribution of training samples across input bins
- Either support the causal interpretation with evidence, or soften the claims
- Acknowledge that higher errors at low pressure could be due to: (a) training imbalance, (b) lower signal-to-noise ratio, or (c) inherent model limitations

**Draft response:**
> We thank the reviewer for this valuable feedback.
> 
> Regarding the aggregated assessment: We have added Table X presenting summary statistics (mean, standard deviation, median, and interquartile range) for NMAE and R across the full test dataset, for both stress and strain predictions. Additionally, we include parity plots comparing predicted versus target values aggregated over all test samples.
> 
> Regarding the error-input correlation analysis: The reviewer raises a valid point about potential confounding factors. We have now analysed the distribution of training samples across the input parameter bins (presented in new Figure X / Supplementary Figure). The analysis reveals [describe findings—e.g., "relatively uniform sampling across all input ranges" or "slight underrepresentation at extreme pressure values"]. Based on this analysis, we have revised the interpretation in Section 3.3 to acknowledge that the observed trend at low pressures may be attributable to [training data distribution / inherent challenges in predicting small deformations / lower signal magnitude], rather than establishing a causal relationship between input parameters and model performance.

**Manuscript modifications:**
- Add summary statistics table
- Add training data distribution analysis
- Revise Section 3.3 interpretation

---

## Minor Comments

### Typos

Simply correct all listed typos:
- "In tis case" → "In this case"
- "a acceptable" → "an acceptable"
- "Section 3 present" → "Section 3 presents"
- "Source Pointss (SPs)" → "Source Points (SPs)"
- "These SP" → "These SPs"
- "The Second and third" → "The second and third"

**Draft response:**
> We thank the reviewer for carefully identifying these typographical errors. All listed corrections have been made in the revised manuscript.

---

### Inconsistency: Deformation Gradient vs. Right Cauchy-Green

**Insight:** The Introduction mentions "deformation gradient tensor" but the rest uses "Right Cauchy-Green strain tensor". These are related but different quantities (C = F^T F).

**Suggested response strategy:**
- Verify which quantity is actually predicted by the model
- Correct the Introduction to match the rest of the manuscript
- Note that the deformation gradient F can be recovered from C under certain assumptions, if relevant

**Draft response:**
> We thank the reviewer for identifying this inconsistency. The surrogate model predicts the Right Cauchy-Green strain tensor (C), not the deformation gradient tensor (F). The Introduction has been corrected to consistently refer to the Second Piola-Kirchhoff stress tensor and the Right Cauchy-Green strain tensor throughout the manuscript.

**Manuscript modification:** Correct the Introduction text.

---

## Summary Table for Tracking Revisions

| Comment | Action | Section | Highlight |
|---------|--------|---------|-----------|
| Young's modulus rationale | Add justification text | 2.4 | Yes |
| Figure 3 legend | Add legend + histograms/table | 3.2 | Yes |
| BC/SC terminology | Change to standard terms | 3.2.1 | Yes |
| Mesh convergence | Add study results | 2.4 | Yes |
| Global statistics | Add summary table | 3.2 | Yes |
| Training distribution | Analyse and present | 3.3 | Yes |
| Error interpretation | Soften claims | 3.3 | Yes |
| Typos | Correct all | Various | Yes |
| F vs C inconsistency | Correct Introduction | 1 | Yes |