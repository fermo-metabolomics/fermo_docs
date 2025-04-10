## Description

This module annotates molecular features by performing spectral similarity networking (also known as “molecular networking” coined by the GNPS software).
MS/MS fragmentation spectra of features are compared in a pairwise fashion, and features with similar spectra are then grouped. 
This is based on the observation that similar molecules usually show similar MS/MS fragmentation patterns, and therefore, similar fragmentation patterns indicate related molecules (chemical families). 

FERMO performs spectral similarity networking as follows:

- The modified cosine algorithm [Watrous 2012](https://doi.org/10.1073/pnas.1203689109), a robust algorithm most useful to cluster highly similar MS/MS spectra, with a generally low false-positive rate
- The MS2DeepScore algorithm [Huber 2021](https://doi.org/10.1186/s13321-021-00558-4), a more experimental algorithm capable of detecting distant similarity, but with a higher false-positive detection rate

## Limitations

- MS/MS fragmentation spectra are needed for spectral similarity networking. Sometimes, molecular features lack this information and are excluded from the networking.
- Given the difficulty in objectively quantifying chemical similarity and the arbitrary nature of cutoff scores, spectral similarity (sub)networks can be drawn in various ways, and even small changes in parameter settings can lead to differences in connectivity. Likewise, different algorithms can result in different networks. Therefore, spectral similarity networking should not be seen as “ground truth” and should be interpreted with caution.


## Parameters `modified cosine`:

<table style="width: 100%;">
 <tr>
  <td style="width: 25%;"><b>Key</b></td>
  <td style="width: 25%;"><b>Possible Values</b></td>
  <td style="width: 25%;"><b>Default</b></td>
 </tr>
 <tr>
  <td style="width: 25%;">activate_module</td>
  <td style="width: 25%;">true, false</td>
  <td style="width: 25%;">true</td>
 </tr>
 <tr>
  <td style="width: 25%;">msms_min_frag_nr</td>
  <td style="width: 25%;"> >=1 </td>
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
  <td style="width: 25%;">0.7</td>
 </tr>
 <tr>
  <td style="width: 25%;">max_nr_links</td>
  <td style="width: 25%;"> >=1 </td>
  <td style="width: 25%;">10</td>
 </tr>
</table>

### Explanation

- `msms_min_frag_nr`: minimum number of fragments a MS/MS fragmentation spectrum must have to be considered in spectral similarity networking
- `fragment_tol`: the absolute tolerance for matching two MS/MS fragments, in m/z units.
- `score_cutoff`: minimum score to consider a match
- `max_nr_links`: maximum number of links to other molecular features any molecular feature is allowed to have in a network.

## Parameters `ms2deepscore`:

<table style="width: 100%;">
 <tr>
  <td style="width: 25%;"><b>Key</b></td>
  <td style="width: 25%;"><b>Possible Values</b></td>
  <td style="width: 25%;"><b>Default</b></td>
 </tr>
 <tr>
  <td style="width: 25%;">activate_module</td>
  <td style="width: 25%;">true, false</td>
  <td style="width: 25%;">true</td>
 </tr>
 <tr>
  <td style="width: 25%;">msms_min_frag_nr</td>
  <td style="width: 25%;"> >=1 </td>
  <td style="width: 25%;">5</td>
 </tr>
 <tr>
  <td style="width: 25%;">score_cutoff</td>
  <td style="width: 25%;">0.0-1.0</td>
  <td style="width: 25%;">0.8</td>
 </tr>
 <tr>
  <td style="width: 25%;">max_nr_links</td>
  <td style="width: 25%;"> >=1 </td>
  <td style="width: 25%;">10</td>
 </tr>
</table>

### Explanation

- `score_cutoff`: minimum score to consider a match
- `msms_min_frag_nr`: minimum number of fragments a MS/MS fragmentation spectrum must have to be considered in spectral similarity networking.
- `max_nr_links`: maximum number of links to other molecular features any molecular feature is allowed to have in a network.


