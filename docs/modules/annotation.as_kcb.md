## Description


This module annotates molecular features using results from the [KnownClusterBlast](https://docs.antismash.secondarymetabolites.org/modules/clusterblast/) algorithm of the popular genome annotation tool [antiSMASH](https://antismash.secondarymetabolites.org). 
KnownClusterBlast performs a multigene BLAST comparison against entries in the [MIBiG repository](https://mibig.secondarymetabolites.org/), and registers significant hits with a score of percent similarity. 

This module parses the KnownClusterBlast matches, selects matches exceeding a user-specified similarity score, and extracts the metabolites experimentally associated with the MIBiG entries. 
From this subset of molecules, a targeted MS/MS spectral library is assembled (using experimental and in silico-generated spectra [CFM-ID](https://cfmid.wishartlab.com/) and used for spectral library matching. 

The assumption is that if two genomes contain two similar biosynthetic gene clusters (BGCs), the metabolites resulting from these two BGCs should also show chemical similarity, with similar MS/MS fragmentation that should allow spectral matching. 
Matches would likely be analogs (not exact matches), but could nevertheless help to annotate a feature.

## Limitations

- Currently, this module accepts a single antiSMASH results folder from the analysis of a single genome. Therefore, all LC-MS samples annotated by this method must also derive from the organism the genome is associated with. 
- The definition of similarity in the context of BGCs: while it is assumed that two similar BGCs should produce similar metabolites, there are many exceptions, and there are cases where a single BGC can produce chemically very different molecules. 

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

- `score_cutoff`: The minimum similarity (in percent) between antiSMASH BGC and MIBiG match required to be considered in annotation (i.e. 0.7 == 70% similarity).

## Parameters `modified cosine`

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
  <td style="width: 25%;">min_nr_matched_peaks</td>
  <td style="width: 25%;"> >=1 </td>
  <td style="width: 25%;">False</td>
  <td style="width: 25%;">5</td>
 </tr>
 <tr>
  <td style="width: 25%;">fragment_tol</td>
  <td style="width: 25%;"> >0 </td>
  <td style="width: 25%;">0.1</td>
 </tr>
 <tr>
  <td style="width: 25%;">score_cutoff</td>
  <td style="width: 25%;">0.0-1.0</td>
  <td style="width: 25%;">0.5</td>
 </tr>
 <tr>
  <td style="width: 25%;">max_precursor_mass_diff</td>
  <td style="width: 25%;"> >=1 </td>
  <td style="width: 25%;">600</td>
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
  <td style="width: 25%;"><b>Default</b></td>
 </tr>
 <tr>
  <td style="width: 25%;">activate_module</td>
  <td style="width: 25%;">true, false</td>
  <td style="width: 25%;">false</td>
 </tr>
 <tr>
  <td style="width: 25%;">score_cutoff</td>
  <td style="width: 25%;">0.0-1.0</td>
  <td style="width: 25%;">0.7</td>
 </tr>
 <tr>
  <td style="width: 25%;">max_precursor_mass_diff</td>
  <td style="width: 25%;"> >=1 </td>
  <td style="width: 25%;">600</td>
 </tr>
</table>

### Explanation

- `score_cutoff`: minimum score to consider a match
- `max_precursor_mass_diff`: maximum allowed difference between precursor m/z of feature and library m/z.


