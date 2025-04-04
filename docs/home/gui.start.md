# Usage

On the 'Start Analysis' page, new *FERMO* analysis jobs can be initiated.

Files can be uploaded using the individual upload fields. 
The analysis job can be started by clicking on the **'Start Analysis'** button at the bottom of the page.

The **only** file required is a **peaktable file** - all other files are optional.

While default parameters are provided, they need to be adjusted according to the **requirements of the data**.

*Nota bene: *FERMO* online versions employs some restrictions with regard to file size, computation time, and data storage to prevent excessive usage. Details can be found on the 'Start Analysis' page.*

#### Example

![full_run](../assets/images/screenshots/gui.start.full_run.gif){ width="60%" }

## Load parameters

This field allows to clone the parameter settings of a previous *FERMO* job (e.g. created by a colleague). 

To load the parameters, simply paste the *FERMO* job ID into the field, and click on the **'Load Job Parameters'** button.

*Nota bene: files and filenames are not retained and must be newly uploaded.*

#### Example

![load_params.png](../assets/images/screenshots/gui.load_params.gif){ width="60%" }

#### Troubleshooting

If an old job ID does not exist anymore but you still want to clone the parameters, you can simply upload a previously created *FERMO* **session.json** file under [Load Session](./gui.load.md).
Take the newly generated *FERMO* job ID and use it to load the parameters.

## Peaktable

The peaktable is the only file that is mandatory for analysis.

See [**here**](./input_output.md#molecular-feature-peaktable) for more information on the required peaktable format.

## MS/MS

*(optional)*

Availability of MS/MS data is very important for annotation tasks. 
If MS/MS data is available, it is highly recommended to include such a file in the analysis.
However, even if MS/MS data is provided, usually not all molecular features have associated MS/MS information, and *FERMO* will ignore such features in annotation tasks requiring MS/MS data.

See [**here**](./input_output.md#msms-spectrum-information) for more information on the required MS/MS file format.

By default, *FERMO* performs quality-filtering of MS/MS fragments. See [here](../modules/filter.msms.md) for additional information.

## Group Metadata

*(optional)*

Group Metadata allows to provide sample context information. 
Using sample grouping, the abundance of features across groups (area, intensity) can be compared. 
Additionally, sample blanks can be designated to identify background ions.

See [**here**](./input_output.md#group-metadata) for more information on the required Group Metadata file format.

## Phenotype Data

*(optional)*

Phenotype data allows to correlate feature abundance with a phenotype/bioactivity signal. 
*FERMO* supports three different data formats/strategies:

- qualitative phenotype data
- percentage activity-based quantitative data
- concentration-based quantitative data

See [**here**](./input_output.md#phenotype-bioactivity-data) for more information on the required Phenotype Data file format.

## Spectral Library

*(optional)*

*FERMO* accepts a user-provided spectral library for feature annotation. 
Spectral library matching can be performed with two different algorithms: 

- **Modified Cosine**: Ideal to detect close similarity.
- **MS2DeepScore**: Can detect also distant similarity.

Ideally, a library targeted towards the research question/organism is used.
This can help to reduce the chance of non-sensical spurious hits (e.g. matching of human metabolites against a bacterial dataset.)

See [**here**](https://external.gnps2.org/gnpslibrary) for a collection of different spectral libraries.

See [**here**](./input_output.md#spectral-library) for more information on the required Spectral Library file format.


## MS2Query Annotation

*(optional)*

*FERMO* accepts result files coming from the [MS2Query](https://github.com/iomega/ms2query) annotation program.

See [**here**](./input_output.md#ms2query-results-file) for more information on the required MS2Query results file format.

## antiSMASH Job Integration

*(optional)*

*FERMO* can also integrate results coming from the popular genome mining software [antiSMASH](https://antismash.secondarymetabolites.org).
For this, *FERMO* requires only an existing **antiSMASH job ID**.

Keep in mind that only a single genome is used for annotation. 
In this case, all samples are assumed to result from organism the genome is associated with.

See [**here**](../modules/annotation.as_kcb.md) for more information on the annotation logic.

See [**here**](./input_output.md#antismash-results) for more information on the expected format.

## Notification Settings

*(optional, only in online mode)*

If an email address was provided, a notification will be sent on job completion (success or failure).