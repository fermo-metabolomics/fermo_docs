## Description

Sample blanks (i.e. instrument runs without sample injection) are frequently used to determine molecular features that are not associated with the biological variability of a sample (e.g. background ions, instrument noise). 
Therefore, blank subtraction is an integral part of metabolomics data processing. The algorithm works as follows:

- Molecular features only observed in samples designated as “BLANK” are considered blank-associated
- Molecular features only observed in non-blank samples are never considered blank-associated
- For each feature observed in both non-blank and blank samples, a user-specified feature value (height or area) across “non-blank” and “blank” samples is compared using an user-specified algorithm. If the resulting quotient is greater than a user-specified ratio (fold-change), the feature is considered NOT blank-associated, else, it is considered blank-associated. This allows to retain features that are detected in sample blanks due to column retention/bleed.

## Parameters

<table style="width: 100%;">
 <tr>
  <td style="width: 25%;"><b>Key</b></td>
  <td style="width: 25%;"><b>Possible Values</b></td>
  <td style="width: 25%;"><b>Required</b></td>
  <td style="width: 25%;"><b>Default</b></td>
 </tr>
 <tr>
  <td style="width: 25%;">activate_module</td>
  <td style="width: 25%;">true, false</td>
  <td style="width: 25%;">True</td>
  <td style="width: 25%;">false</td>
 </tr>
 <tr>
  <td style="width: 25%;">factor</td>
  <td style="width: 25%;">>=1</td>
  <td style="width: 25%;">False</td>
  <td style="width: 25%;">10</td>
 </tr>
 <tr>
  <td style="width: 25%;">algorithm</td>
  <td style="width: 25%;">mean, median, maximum</td>
  <td style="width: 25%;">False</td>
  <td style="width: 25%;">mean</td>
 </tr>
 <tr>
  <td style="width: 25%;">value</td>
  <td style="width: 25%;">height, area</td>
  <td style="width: 25%;">False</td>
  <td style="width: 25%;">area</td>
 </tr>
</table>

### Explanation

- `algorithm`: algorithm to summarize value over non-blank samples and sample blanks (mean, median, maximum (highest value across non-blanks/blanks)).
- `value`: specifies type of value to be considered (height or area)
- `factor`: determines subtraction of features detected in both blank and non-blank samples.
