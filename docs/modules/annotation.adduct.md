## Description

This module annotates the ion identity of co-occurring molecular features (features with overlapping retention time ranges). In electrospray ionization (ESI), a single molecule can form adducts with different ions, resulting in different ion species and different molecular features. Therefore, annotation of related ion species does not only allow to reduce redundancy, but also gives information about the identity of the molecule (e.g. molecular weight). The annotation algorithm works as follows:

- For each sample, overlapping features are determined by simplifying features to one-dimensional vectors, denoted with two points x1 (retention time of the start of the feature) and x2 (end of the feature). For two features A,B with A(x1,x2) and B(x1,x2), if any of (Ax2 < Bx1) or (Bx2 < Ax1) is true, features do not overlap.
- For overlapping features, m/z values are compared. One of the two features is considered the [M+H]+ (positive mode) or the [M-H]- (negative mode) ‘base’ adduct, while the other peak is considered another adduct. If any of the registered mathematical operations (one for each different ion type) leads to a m/z match of the ‘base’ and the ‘adduct’ inside a user-specified mass deviation difference `mass_dev_ppm`, a match is registered.

## Limitations

- The algorithm currently does not triangulate the parent mass. Interpretation is the responsibility of the user.

Currently supported **positive** ion mode adduct types are:

- `sodium_adduct [M+Na]+`
- `dimer_sodium_adduct [2M+Na]+`
- `triple_h_adduct [M+3H]3+`
- `iron56 [M+56Fe-2H]+`
- `dimer_double [M+2H]2+ and [2M+H]+`
- `ammonium [M+NH4]+`
- `potassium [M+K]+`
- `water_add [M+H2O+H]+`
- `water_loss [M-H2O+H]+`
- `plus1_isotope [M+1+H]+`
- `plus2_isotope [M+2+H]+`
- `plus3_isotope [M+3+H]+`
- `plus4_isotope [M+4+H]+`
- `plus5_isotope [M+5+H]+`
- `double_plus1 [M+1+2H]2+`
- `double_plus2 [M+2+2H]2+`
- `double_plus3 [M+3+2H]2+`
- `double_plus4 [M+4+2H]2+`
- `double_plus5 [M+5+2H]2+`

Currently supported **negative** ion mode adducts are:

- `chloride_adduct [M+Cl]-`
- `double_dimer_pair_neg [M-2H]2- and [2M-H]-`
- `bicarbonate_adduct [M+HCO2]-`
- `tfa_adduct [M+TFA-H]- (trifluoroacetate)`
- `acetate_adduct [M+HAc-H]-`

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
  <td style="width: 25%;">true</td>
 </tr>
 <tr>
  <td style="width: 25%;">mass_dev_ppm</td>
  <td style="width: 25%;">0-100.0</td>
  <td style="width: 25%;">False</td>
  <td style="width: 25%;">10.0</td>
 </tr>
</table>

### Explanation

- `mass_dev_ppm`: the maximum allowed mass deviation difference to constitute a match.