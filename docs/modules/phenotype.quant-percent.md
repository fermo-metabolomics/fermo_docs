## Description

The “quantitative-percentage” module takes phenotype/bioactivity data where samples have a measured percentage of bioactivity/phenotype at a specified concentration. 

Multiple measurements can be specified for each sample, and multiple assays (each at a determined concentration) can be provided. The algorithm works as follows:

- Values below zero are set to zero.
- Duplicate measurements per sample are averaged using either the mean or median.
- The areas of molecular features detected in more than three samples are z-transformed along with the phenotype measurements.
- Transformed feature areas and percentage values are correlated using Pearson correlation.
- The resulting p-values are corrected for multiple hypothesis testing using a user-specified correction method (e.g. Bonferroni).
- Features that exceed user-defined thresholds for both correlation coefficient and adjusted p-value are considered phenotype-associated.

## Limitations

- This method assumes that the prerequisites with regard to sample reproducibility are met (see [Input/Output](../home/input_output.md)).
- This method assumes a positive linear correlation between phenotype (percentage) and concentration (area of feature).
- This method does not take into account any synergistic or quenching effects.

## Parameters

<table style="width: 100%;">
 <tr>
  <td style="width: 25%;"><b>Key</b></td>
  <td style="width: 25%;"><b>Possible Values</b></td>
  <td style="width: 25%;"><b>Default</b></td>
 </tr>
 <tr>
  <td style="width: 25%;">activate_module</td>
  <td style="width: 25%;">true, false</td>
  <td style="width: 25%;">false</td>
 </tr>
 <tr>
  <td style="width: 25%;">sample_avg</td>
  <td style="width: 25%;">mean, median</td>
  <td style="width: 25%;">mean</td>
 </tr>
 <tr>
  <td style="width: 25%;">value</td>
  <td style="width: 25%;">area</td>
  <td style="width: 25%;">area</td>
 </tr>
 <tr>
  <td style="width: 25%;">algorithm</td>
  <td style="width: 25%;">pearson</td>
  <td style="width: 25%;">pearson</td>
 </tr>
 <tr>
  <td style="width: 25%;">fdr_corr</td>
  <td style="width: 25%;">bonferroni, sidak, holm-sidak, holm, simes-hochberg, hommel, fdr_bh, fdr_by, fdr_tsbh, fdr_tsbky</td>
  <td style="width: 25%;">bonferroni</td>
 </tr>
 <tr>
  <td style="width: 25%;">p_val_cutoff</td>
  <td style="width: 25%;">0.0-1.0</td>
  <td style="width: 25%;">0.05</td>
 </tr>
 <tr>
  <td style="width: 25%;">coeff_cutoff</td>
  <td style="width: 25%;">0.0-1.0</td>
  <td style="width: 25%;">0.7</td>
 </tr>
</table>

### Explanation

- `sample_avg`: specifies the algorithm to summarize multiple measurements per sample for same assay. Possible algorithms are `mean` and `median`.
- `value`: specifies value per feature to be correlated with percentage. Only `area` is currently allowed.
- `algorithm`: specifies the statistical algorithm to use. Only `pearson` is currently allowed.
- `fdr_corr`: the method used for false-discovery-rate correction. FERMO uses the [statsmodels](https://www.statsmodels.org/dev/generated/statsmodels.stats.multitest.multipletests.html) library for this purpose - please see their documentation for information on the different algorithms.
- `p_val_cutoff`: Maximum FDR-corrected p-value to consider, with zero disabling cutoff filtering for both p-value and coefficient.
- `coeff_cutoff`: Minimum correlation coefficient to consider, with zero disabling cutoff filtering for both p-value and coefficient.


