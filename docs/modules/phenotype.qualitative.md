## Description

The “qualitative” module takes qualitative phenotype/bioactivity assay data. 
Samples are classified in a binary fashion: "positive” (e.g. showing antibiotic activity) or “negative" (e.g. showing no antibiotic activity). 
The algorithm works as follows:

- Features exclusively detected in the “positive” samples are considered phenotype/bioactivity-associated. 
- Features exclusively detected in the “negative” samples are considered NOT phenotype/bioactivity-associated. 
- Features detected both in "positive" and "negative" are considered phenotype/bioactivity-associated if the quotient (factor) of mean/median/minmax area/height between "positive" and "negative" samples is above a user-specified threshold. Optionally, this can be supplemented by Walsh's t-test if the user sets a significance threshold (switched off by default).

This function allows to retain features that may be bioactivity-associated but are present in sub-inhibitory concentrations in the “negative” samples (lack of phenotypic/bioactivity readout). 


## Limitations

- This method assumes that the prerequisites with regard to sample reproducibility are met (see [Input/Output](../home/input_output.md)).


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
  <td style="width: 25%;">factor</td>
  <td style="width: 25%;">>=1</td>
  <td style="width: 25%;">10</td>
 </tr>
 <tr>
  <td style="width: 25%;">algorithm</td>
  <td style="width: 25%;">minmax, median, mean</td>
  <td style="width: 25%;">minmax</td>
 </tr>
 <tr>
  <td style="width: 25%;">value</td>
  <td style="width: 25%;">height, area</td>
  <td style="width: 25%;">area</td>
 </tr>
 <tr>
  <td style="width: 25%;">p_val_cutoff</td>
  <td style="width: 25%;">0-1</td>
  <td style="width: 25%;">0</td>
 </tr>
</table>

### Explanation

- `factor`: the user-specified ratio (fold change) to differentiate features detected in both “positive” and “negative” samples.
- `value`: the value used in the determination of the quotient.
- `algorithm`: the algorithm to summarize values over “positive” and “negative” samples. Currently possible algorithms are “mean”, “median”, and “minmax”. The latter takes the **lowest** value across “positive” samples and the **highest** value across “negative” samples
- `p_val_cutoff`: the significance cutoff of Welsh's t-test (optional). Used to give additional discriminatory power when factor is low. Can be disabled by setting it to 0 (default).
