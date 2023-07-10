# Title of Study : Pre-analysis Registration

### Authors

- Liam Smith\*, lwsmith@middlebury.edu, @Liam-W-Smith, ORCID link, Middlebury College
- Joseph Holler, josephh@middlebury.edu , @josephholler, ORCID link, Middlebury College

\* Corresponding author and creator

### Abstract

This study is a *replication* of:

> Spielman, S. E., Tuccillo, J., Folch, D. C., Schweikert, A., Davies, R., Wood, N., & Tate, E. (2020). Evaluating Social Vulnerability Indicators: Criteria and their Application to the Social Vulnerability Index. Natural Hazards, 100(1), 417–436. https://doi.org/10.1007/s11069-019-03820-z

The original paper develops methods to evaluate the validity of social vulnerability indicators and applies them to SoVI, revealing issues with internal consistency and construct validity.
Their paper implements these methods by calculating SoVI over various spatial extents in the USA.
We first reproduce their results and then extend their work with a replication study, determining how robust SoVI is to changes over time.


### Study Metadata

- `Key words`: social vulnerability, evaluation, social indicators
- `Subject`: select from the [BePress Taxonomy](http://digitalcommons.bepress.com/cgi/viewcontent.cgi?article=1008&context=reference)
- `Date created`: June 19, 2023
- `Date modified`: June 29, 2023
- `Spatial Coverage`: United States, excluding Puerto Rico
- `Spatial Resolution`: Counties and county equivalents
- `Spatial Reference System`: Specify the geographic or projected coordinate system for the study
- `Temporal Coverage`: TBD
- `Temporal Resolution`: TBD
- `Funding Name`: name of funding for the project
- `Funding Title`: title of project grant
- `Award info URI`: web address for award information
- `Award number`: award number

#### Original study spatio-temporal metadata

- `Spatial Coverage`: United States, excluding Puerto Rico
- `Spatial Resolution`: counties and county equivalents
- `Spatial Reference System`: spatial reference system of original study
- `Temporal Coverage`: 2008 - 2012 (data is the 2012 5-year ACS)
- `Temporal Resolution`: temporal resolution of original study

## Study design

First, we seek to computationally reproduce Spielman et al's original work using the code provided in [their Github repository](https://github.com/geoss/sovi-validity).
We adapt their code to work in an updated Python environment using updated packages, and we enhance reproducibility by drawing data directly from the census into Python via an API, rather than downloading data and reading it into Python.

Second, we seek to expand upon Spielman et al's work with a replication study.
In their work, Spielman et al assess internal consistency and construct validity by altering the spatial extent.
In our replication, we plan to employ the same methods to assess the validity of SoVI but change the temporal coverage rather than the spatial extent.
In this manner, our analysis will assess the validity of SoVI from the perspective of robustness to time rather than spatial extent.

Research questions for original paper:
1. What methods can we use to assess the validity of indices used to measure latent variables like SoVI?
2. Does SoVI fulfill the seven criteria identified by Spielman et al for assessing the validity of complex social indices, including internal consistency and theoretical consistency (construct validity)?

Research questions for our replication study:
1. To what extent is Spielman et al's paper reproducible?
2. Does SoVI exhibit qualities of internal consistency and construct validity when we calculate SoVI in the same location for several different years?

***If the study design includes subcomponents with different spatial or temporal characteristics than the overall study, or includes multi-level models, then enumerate the different subcomponents/levels and specify their spatial/temporal differences here.***

## Materials and procedure

### Computational environment

Currently, we are using a 2020 MacBook Pro running on macOS Ventura 13.3.1.
We anticipate collaborators working on the project from different computers and different operating systems, and we seek to containerize the project so that scripts can be run on many different machines.

The original study used Python for their analysis, so we first reproduce their results in Python, using a containerized conda environment to be provided in the project's GitHub repository.
This environment consists of the following software and packages:

- Python 3.9.16
- Pandas 1.4.4
- GeoPandas 0.13.2
- Pyhere 1.0.0
- SciPy 1.10.1
- NumPy 1.21.5
- Mapclassify 2.5.0
- MDP 3.5
- Pygris 0.1.5
- Libpysal 4.7.0

For our replication study, we may translate the Python code into R.
We seek to containerize our R environment for use from any computer.

### Data and variables

For Spielman et al's original study, the data sources were the 2008-2012 5-year American Community Survey and the 2010 decennial census.
Spielman et al downloaded their data from Social Explorer; in our reproduction, we pull our data directly from the census into Python via a census API package known as pygris.
Since we are reproducing and replicating the work of Spielman et al, the variables we use are the same as those used in their study.
These variables are based on the original work by Cutter et al to create SoVI, and cover a wide range of social and demographic information, the particulars of which are described below.

#### 2008-2012 American Community Survey (5-year)

**Standard Metadata**

- `Abstract`: Brief description of the data source
- `Spatial Coverage`: United States
- `Spatial Resolution`: county and county-equivalents
- `Spatial Reference System`: Specify the geographic or projected coordinate system for the study
- `Temporal Coverage`: 2008-2012
- `Temporal Resolution`: One-time observations
- `Lineage`: Obtained directly from the census via API
- `Distribution`: Describe how the data is distributed, including any persistent identifier (e.g. DOI) or URL for data access
- `Constraints`: Legal constraints for *access* or *use* to protect *privacy* or *intellectual property rights*
- `Data Quality`: State result of quality assessment or state "Quality unknown"
- `Variables`: For each variable, enter the following information. If you have two or more variables per data source, you may want to present this information in table form (shown below)
  - `Label`: variable name as used in the data or code
  - `Alias`: intuitive natural language name
  - `Definition`: Short description or definition of the variable. Include measurement units in description.
  - `Type`: data type, e.g. character string, integer, real
  - `Accuracy`: e.g. uncertainty of measurements
  - `Domain`: Range (Maximum and Minimum) of numerical data, or codes or categories of nominal data, or reference to a standard codebook
  - `Missing Data Value(s)`: Values used to represent missing data and frequency of missing data observations
  - `Missing Data Frequency`: Frequency of missing data observations

| Label | Alias | Definition | Type | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| variable1 | ... | ... | ... | ... | ... | ... | ... |
| variable2 | ... | ... | ... | ... | ... | ... | ... |

#### 2010 Decennial Census

**Standard Metadata**

- `Abstract`: Brief description of the data source
- `Spatial Coverage`: Specify the geographic extent of your study. This may be a place name and link to a feature in a gazetteer like GeoNames or OpenStreetMap, or a well known text (WKT) representation of a bounding box.
- `Spatial Resolution`: Specify the spatial resolution as a scale factor, description of the level of detail of each unit of observation (including administrative level of administrative areas), and/or or distance of a raster GRID size
- `Spatial Reference System`: Specify the geographic or projected coordinate system for the study
- `Temporal Coverage`: Specify the temporal extent of your study---i.e. the range of time represented by the data observations.
- `Temporal Resolution`: Specify the temporal resolution of your study---i.e. the duration of time for which each observation represents or the revisit period for repeated observations
- `Lineage`: Describe and/or cite data sources and/or methodological steps used to create this data source
- `Distribution`: Describe how the data is distributed, including any persistent identifier (e.g. DOI) or URL for data access
- `Constraints`: Legal constraints for *access* or *use* to protect *privacy* or *intellectual property rights*
- `Data Quality`: State result of quality assessment or state "Quality unknown"
- `Variables`: For each variable, enter the following information. If you have two or more variables per data source, you may want to present this information in table form (shown below)
  - `Label`: variable name as used in the data or code
  - `Alias`: intuitive natural language name
  - `Definition`: Short description or definition of the variable. Include measurement units in description.
  - `Type`: data type, e.g. character string, integer, real
  - `Accuracy`: e.g. uncertainty of measurements
  - `Domain`: Range (Maximum and Minimum) of numerical data, or codes or categories of nominal data, or reference to a standard codebook
  - `Missing Data Value(s)`: Values used to represent missing data and frequency of missing data observations
  - `Missing Data Frequency`: Frequency of missing data observations

| Label | Alias | Definition | Type | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| variable1 | ... | ... | ... | ... | ... | ... | ... |
| variable2 | ... | ... | ... | ... | ... | ... | ... |

### Prior observations  

Prior experience with the study area, prior data collection, or prior observation of the data can compromise the validity of a study, e.g. through p-hacking.
Therefore, disclose any prior experience or observations at the time of study pre-registration here, with example text below:

At the time of this study pre-registration, the authors had _____ prior knowledge of the geography of the study region with regards to the ____ phenomena to be studied.
This study is related to ____ prior studies by the authors

For each primary data source, declare the extent to which authors had already engaged with the data:

- [ ] no data collection has started
- [ ] pilot test data has been collected, but will not be analyzed
- [ ] data collection is in progress and data has not been observed
- [ ] data collection is in progress and __% of data has been observed
- [ ] data collection is complete and data has been observed. Explain how authors have already manipulated / explored the data.

For each secondary source, declare the extent to which authors had already engaged with the data:

- [ ] data is not available yet
- [ ] data is available, but only metadata has been observed
- [ ] metadata and descriptive statistics have been observed
- [ ] metadata and a subset or sample of the full dataset have been observed
- [ ] the full dataset has been observed. Explain how authors have already manipulated / explored the data.

### Threats to validity

Given the research design and primary data to be collected and/or secondary data to be used, discuss common threats to validity and the approach to mitigating those threats, with an emphasis on geographic threats to validity.

These include:
  - uneven primary data collection due to geographic inaccessibility or other constraints
  - edge or boundary effects
  - the modifiable areal unit problem
  - nonstationarity
  - spatial dependence or autocorrelation
  - temporal dependence or autocorrelation
  - spatial scale dependency
  - spatial anisotropies
  - confusion of spatial and a-spatial causation
  - ecological fallacy
  - uncertainty e.g. from spatial disaggregation, anonymization, differential privacy

### Data transformations

Describe all data transformations planned to prepare data sources for analysis.
This section should explain with the fullest detail possible how to transform data from its raw state from the time of acquisition or observation to the main analysis, including steps to check and mitigate threats to validity.
The method may anticipate contingencies, e.g. tests for normality and alternative decisions to make based on the results of the test.
More specifically, all the **geographic** and **variable** transformations required to prepare input data as described in the data and variables section above to match the study's spatio-temporal characteristics as described in the study metadata and study design sections.
Visual workflow diagrams may help communicate the methodology in this section.

Examples of **geographic** transformations include coordinate system transformations, aggregation, disaggregation, spatial interpolation, distance calculations, zonal statistics, etc.

Examples of **variable** transformations include standardization, normalization, constructed variables, imputation, classification, etc.

Be sure to include any steps planned to **exclude** observations with missing or outlier data, to **group** observations by attribute or geographic criteria, or to **impute** missing data.

### Analysis

Describe the methods of analysis that will directly test the hypotheses or provide results to answer the research questions.
This section should explicitly define any spatial / statistical models and their parameters, including significance thresholds.
Also explain any follow-up analyses or validations.

## Results

Describe how results are to be presented.

## Discussion

Describe how the results are to be interpreted *vis a vis* each hypothesis or research question.

## Integrity Statement

The authors of this preregistration state that they completed this preregistration to the best of their knowledge and that no other preregistration exists pertaining to the same hypotheses and research.

## References
