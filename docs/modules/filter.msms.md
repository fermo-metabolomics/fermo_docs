## Description

This module performs filtering of MS/MS fragmentation spectra of features. 
MS/MS spectra regularly contain fragments caused by instrument noise, which obfuscate and prolongate the analysis. 

By default, *FERMO* will quality-filter MS/MS fragments and remove the fragment corresponding to the precursor *m/z* and all fragments +- 10 *m/z* units around the precursor *m/z*.
These fragments are usually artifacts and do not correspond to any meaningful neutral losses. 

Additionally, *FERMO* can remove fragments with a relative intensity lower than a user-specified value.
This is recommended to remove noise peaks from the spectrum. Filtering takes place after the initial precursor *m/z* removal.

## Parameters

<table style="width: 100%;">
 <tr>
  <td style="width: 25%;"><b>Key</b></td>
  <td style="width: 25%;"><b>Possible Values</b></td>
  <td style="width: 25%;"><b>Default</b></td>
 </tr>
 <tr>
  <td style="width: 25%;">filepath</td>
  <td style="width: 25%;"><i>(the filepath)</i></td>
  <td style="width: 25%;">N/A</td>
 </tr>
 <tr>
  <td style="width: 25%;">format</td>
  <td style="width: 25%;">mgf</td>
  <td style="width: 25%;">N/A</td>
 </tr>
 <tr>
  <td style="width: 25%;">rel_int_from</td>
  <td style="width: 25%;">0.0-1.0</td>
  <td style="width: 25%;">0.01</td>
 </tr>
</table>

### Explanation

- `rel_int_from`: specifies the minimum relative intensity to retain fragments in an MS/MS spectrum. If 0.0, all fragments are retained. A value of 0.01 would remove all fragments with an intensity of less than 1% of the most intense fragment.
