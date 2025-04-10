## Description

This module filters molecular features that do not fit specified cutoff settings. 

It has been observed that under certain circumstances, a large part of molecular features can be attributed to instrument noise [Samples 2023](https://doi.org/10.1021/acs.analchem.2c04632). 
Therefore, *FERMO* allows to filter certain molecular features from the analysis:

- For a given range of relative signal height/height (0-1.0, relative to the feature with the highest intensity), molecular features that are not inside this range **in at least one sample** are discarded
- For a given range of relative signal area (0-1.0, relative to the feature with the highest area), molecular features that are not inside this range **in at least one sample** are discarded

These filters can be combined with each other to yield certain slices of the original data.

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
  <td style="width: 25%;">filter_rel_int_range_min</td>
  <td style="width: 25%;">0.0-1.0</td>
  <td style="width: 25%;">0.0</td>
 </tr>
 <tr>
  <td style="width: 25%;">filter_rel_int_range_max</td>
  <td style="width: 25%;">0.0-1.0</td>
  <td style="width: 25%;">1.0</td>
 </tr>
 <tr>
  <td style="width: 25%;">filter_rel_area_range_min</td>
  <td style="width: 25%;">0.0-1.0</td>
  <td style="width: 25%;">0.0</td>
 </tr>
 <tr>
  <td style="width: 25%;">filter_rel_area_range_max</td>
  <td style="width: 25%;">0.0-1.0</td>
  <td style="width: 25%;">1.0</td>
 </tr>
</table>

### Explanation

- `filter_rel_int_range_min`: specifies the minimum value of relative intensity to retain in analysis
- `filter_rel_int_range_max`: specifies the maximum value of relative intensity to retain in analysis
- `filter_rel_area_range_min`: specifies the minimum value of relative area to retain in analysis
- `filter_rel_area_range_max`: specifies the maximum value of relative area to retain in analysis
