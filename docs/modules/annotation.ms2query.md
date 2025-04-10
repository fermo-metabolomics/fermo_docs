## Description

For feature annotation, *FERMO* accepts results created by [MS2Query](https://github.com/iomega/ms2query), a machine-learning based annotation algorithm. 
MS2Query comes with its own spectral library derived from the GNPS library and can do exact and/or analog matching.

For compatibility with *FERMO*, the MS2Query results file must come with a column `feature_id` or `id` matching the peaktable feature IDs (default since MS2Query >= `v1.5.3`)

For more information on the algorithmm see the [MS2Query Documentation](https://github.com/iomega/ms2query).

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
  <td style="width: 25%;">score_cutoff</td>
  <td style="width: 25%;">0.0-1.0</td>
  <td style="width: 25%;">0.7</td>
 </tr>
</table>

### Explanation

- `score_cutoff`: minimum score in `ms2query_model_prediction` to consider a match to be valid. Matches with a score lower than `score_cutoff` are not considered for molecular feature annotation.
