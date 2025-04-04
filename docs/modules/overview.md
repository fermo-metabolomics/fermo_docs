*FERMO* functionality is separated in modules: each module has a certain functionality and takes certain parameters that modify its behavior. 
All modules are optional and can be switched on/off as desired.

In the *FERMO* GUI, these parameters can be set using the input forms. 

*FERMO* in command line mode (`fermo_core`) requires a specifically formatted `parameters` file in `JSON` format. 
The parameters are described in the individual modules.

## Filtering

- [Feature Filtering](filter.feature.md)
- [MS/MS Filtering](filter.msms.md)

## Networking

- [Spectral Similarity (Molecular) Networking](networking.md)

## Annotation

- [Adduct Annotation](annotation.adduct.md)
- [Neutral Loss Annotation](annotation.loss.md)
- [Fragment Annotation](annotation.fragment.md)
- [Spectral Library Annotation](annotation.userlib.md)
- [MS2Query Annotation](annotation.ms2query.md)
- [antiSMASH KnownClusterBlast Annotation](annotation.as_kcb.md)

## Group Metadata

- [Blank Assignment](metadata.blank.md)
- [Group Assignment](metadata.group_fold.md)

## Phenotype Assignment

- [Phenotype Qualitative](phenotype.qualitative.md)
- [Phenotype Quantitative-Percentage](phenotype.quant-percent.md)
- [Phenotype Quantitative-Concentration](phenotype.quant-concentr.md)

## Scores

- [Feature Scores Calculation](scores.features.md)
- [Sample Scores Calculation](scores.samples.md)


