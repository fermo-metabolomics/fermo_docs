## Description

Samples are frequently grouped to compare intergroup variability (instead of only inter-sample variability). 

FERMO allows to specify multiple categories of groups (each column in the group metadata file is considered one category), with multiple groups inside each category. 
For each category, features associated to multiple groups are identified and their relative abundance is calculated as follows:

- For each feature, association to the groups of a category is determined.
- If a feature is detected in two or more groups, user-specified values detected across the samples belonging to each group are summarized via a user-specified algorithm, the values compared pairwise, and the resulting quotient is registered if >= 1.
- This process is repeated for each specified category.

## Limitations

- Groups from different categories are never compared. Only categories inside groups are compared.

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
  <td style="width: 25%;">algorithm</td>
  <td style="width: 25%;">mean, median, maximum</td>
  <td style="width: 25%;">mean</td>
 </tr>
 <tr>
  <td style="width: 25%;">value</td>
  <td style="width: 25%;">height, area</td>
  <td style="width: 25%;">area</td>
 </tr>
</table>

### Explanation

- `algorithm`: the algorithm to summarize values across a group with. Possible algorithms are `mean`, `median`, and `maximum` (highest value across samples of a group)
- `value`: specifies the value to be considered: `height` (=intensity) or `area` of feature.


