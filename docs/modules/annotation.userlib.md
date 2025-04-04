## Description

This module compares molecular features against a user-provided (targeted) spectral library. The matching algorithm works as follows:

- For each feature, its MS/MS fragmentation spectrum is matched pairwise with each library spectrum, using one or more different algorithms described below. 
- For the `modified cosine` algorithm, library matches are only retained if feature and library spectra share a minimum number of matched peaks within a certain fragment tolerance, reach a cutoff score, and are inside a maximum precursor mass difference.
- For the [MS2DeepScore](https://github.com/matchms/ms2deepscore) algorithm, library matches are only retained if feature and library spectra reach a certain cutoff score and are inside a maximum precursor mass difference.

## Limitations

- Spectral library matching is prohibitively slow with large spectral libraries (especially using the MS2DeepScore algorithm). Ideally, a targeted spectral library should be provided. For a more general library, see MS2Query annotation.

## Parameters `modified cosine`

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
  <td style="width: 25%;">min_nr_matched_peaks</td>
  <td style="width: 25%;"> >=1 </td>
  <td style="width: 25%;">False</td>
  <td style="width: 25%;">5</td>
 </tr>
 <tr>
  <td style="width: 25%;">fragment_tol</td>
  <td style="width: 25%;"> >0 </td>
  <td style="width: 25%;">False</td>
  <td style="width: 25%;">0.1</td>
 </tr>
 <tr>
  <td style="width: 25%;">score_cutoff</td>
  <td style="width: 25%;">0.0-1.0</td>
  <td style="width: 25%;">False</td>
  <td style="width: 25%;">0.7</td>
 </tr>
 <tr>
  <td style="width: 25%;">max_precursor_mass_diff</td>
  <td style="width: 25%;"> >=1 </td>
  <td style="width: 25%;">False</td>
  <td style="width: 25%;">600</td>
 </tr>
 <tr>
  <td style="width: 25%;">maximum_runtime</td>
  <td style="width: 25%;"> >=0 </td>
  <td style="width: 25%;">False</td>
  <td style="width: 25%;">0 (unlimited)</td>
 </tr>
</table>

### Explanation

- `fragment_tol`: the absolute tolerance for matching two MS/MS fragments, in m/z units.
- `min_nr_matched_peaks`: minimum number of fragments that must be matched between two MS/MS fragmentation spectra.
- `score_cutoff`: minimum score to consider a match
- `max_precursor_mass_diff`: maximum allowed difference between precursor m/z of feature and library m/z.

## Parameters `ms2deepscore`

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
  <td style="width: 25%;">score_cutoff</td>
  <td style="width: 25%;">0.0-1.0</td>
  <td style="width: 25%;">False</td>
  <td style="width: 25%;">0.8</td>
 </tr>
 <tr>
  <td style="width: 25%;">max_precursor_mass_diff</td>
  <td style="width: 25%;"> >=1 </td>
  <td style="width: 25%;">False</td>
  <td style="width: 25%;">600</td>
 </tr>
 <tr>
  <td style="width: 25%;">maximum_runtime</td>
  <td style="width: 25%;"> >=0 </td>
  <td style="width: 25%;">False</td>
  <td style="width: 25%;">0 (unlimited)</td>
 </tr>
</table>

### Explanation

- `score_cutoff`: minimum score to consider a match
- `max_precursor_mass_diff`: maximum allowed difference between precursor m/z of feature and library m/z.


