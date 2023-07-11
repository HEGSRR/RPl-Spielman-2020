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

- `Key words`: Social vulnerability, evaluation, social indicators
- `Subject`: Social and Behavioral Sciences: Geography: Human Geography
- `Date created`: June 19, 2023
- `Date modified`: June 29, 2023
- `Spatial Coverage`: United States, excluding Puerto Rico
- `Spatial Resolution`: Counties and county equivalents
- `Spatial Reference System`: EPSG:4269
- `Temporal Coverage`: TBD (ADD)
- `Temporal Resolution`: TBD (ADD)
- `Funding Name`: name of funding for the project (ADD)
- `Funding Title`: title of project grant (ADD)
- `Award info URI`: web address for award information (ADD)
- `Award number`: award number (ADD)

#### Original study spatio-temporal metadata

- `Spatial Coverage`: United States, excluding Puerto Rico
- `Spatial Resolution`: Counties and county equivalents
- `Spatial Reference System`: EPSG:4269
- `Temporal Coverage`: 2008 - 2012 (data is the 2012 5-year ACS)
- `Temporal Resolution`: One-time measurement, does not address change over time

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
- CHECK WHICH OTHERS TO ADD

### Data and variables

For Spielman et al's original study, the data sources were the 2008-2012 5-year American Community Survey and the 2010 decennial census.
Spielman et al downloaded their data from Social Explorer; in our reproduction, we pull our data directly from the census into Python via a census API package known as pygris.
Since we are reproducing and replicating the work of Spielman et al, the variables we use are the same as those used in their study.
These variables are based on the original work by Cutter et al to create SoVI, and cover a wide range of social and demographic information, the particulars of which are described below.

#### 2008-2012 American Community Survey (5-year)

**Standard Metadata**

- `Abstract`: The 5-year ACS provides estimates surrounding demographic information in the USA. These estimates are more reliable than 1-year and 3-year estimates but less reliable than decennial census data. On the other hand, 5-year estimates are less current than 1-year and 3-year estimates because they represent measurements taken over 60 months. See the [census website](https://www.census.gov/programs-surveys/acs/guidance/estimates.html) for more details.
- `Spatial Coverage`: United States
- `Spatial Resolution`: County and county-equivalents
- `Spatial Reference System`: None, just attribute data
- `Temporal Coverage`: 2008-2012
- `Temporal Resolution`: One-time observations
- `Lineage`: Obtained directly from the census via API (ADD LINEAGE OF SPIELMAN DATA?)
- `Distribution`: This data is distributed via a census API. See the detailed tables on the [census website](https://www.census.gov/data/developers/data-sets/acs-5year/2012.html) and instructions for drawing census data directly into python on the [pygris website](https://walker-data.com/pygris/)
- `Constraints`: Legal constraints for *access* or *use* to protect *privacy* or *intellectual property rights* (ADD)
- `Data Quality`: State result of quality assessment or state "Quality unknown" (ADD)
- `Variables`: For each variable, enter the following information. If you have two or more variables per data source, you may want to present this information in table form (shown below)
  - `Label`: variable name as used in the data or code
  - `Alias`: intuitive natural language name
  - `Definition`: Short description or definition of the variable. Include measurement units in description.
  - `Type`: data type, e.g. character string, integer, real
  - `Accuracy`: e.g. uncertainty of measurements
  - `Domain`: Range (Maximum and Minimum) of numerical data, or codes or categories of nominal data, or reference to a standard codebook
  - `Missing Data Value(s)`: Values used to represent missing data and frequency of missing data observations
  - `Missing Data Frequency`: Frequency of missing data observations

|    | Label       | Alias                                                                         | Definition                                                                                                                                                                                                                         | Type    | Domain                 |   Missing Data Value(s) |   Missing Data Frequency |\n|---:|:------------|:------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------|:-----------------------|------------------------:|-------------------------:|\n|  0 | B01002_001E | median age                                                                    | MEDIAN AGE BY SEX: Estimate!!Median age!!Total                                                                                                                                                                                     | float64 | 21.7 - 63              |                     nan |                        0 |\n|  1 | B03002_001E | total population of respondents to race/ethnicity                             | HISPANIC OR LATINO ORIGIN BY RACE: Estimate!!Total                                                                                                                                                                                 | int64   | 66 - 9840024           |                     nan |                        0 |\n|  2 | B03002_004E | total Black population                                                        | HISPANIC OR LATINO ORIGIN BY RACE: Estimate!!Total!!Not Hispanic or Latino!!Black or African American alone                                                                                                                        | int64   | 0 - 1267825            |                     nan |                        0 |\n|  3 | B03002_005E | total Native American population                                              | HISPANIC OR LATINO ORIGIN BY RACE: Estimate!!Total!!Not Hispanic or Latino!!American Indian and Alaska Native alone                                                                                                                | int64   | 0 - 59060              |                     nan |                        0 |\n|  4 | B03002_006E | total Asian population                                                        | HISPANIC OR LATINO ORIGIN BY RACE: Estimate!!Total!!Not Hispanic or Latino!!Asian alone                                                                                                                                            | int64   | 0 - 1343920            |                     nan |                        0 |\n|  5 | B03002_012E | total Latinx population                                                       | HISPANIC OR LATINO ORIGIN BY RACE: Estimate!!Total!!Hispanic or Latino                                                                                                                                                             | int64   | 0 - 4694846            |                     nan |                        0 |\n|  6 | B06001_002E | total population under 5 years of age                                         | PLACE OF BIRTH BY AGE IN THE UNITED STATES: Estimate!!Total!!Under 5 years                                                                                                                                                         | float64 | 0 - 651662             |                     nan |                        0 |\n|  7 | B09020_001E | total population over 65 years of age                                         | RELATIONSHIP BY HOUSEHOLD TYPE (INCLUDING LIVING ALONE) FOR THE POPULATION 65 YEARS AND OVER: Estimate!!Total                                                                                                                      | int64   | 5 - 1078555            |                     nan |                        0 |\n|  8 | B01003_001E | total population                                                              | TOTAL POPULATION: Estimate!!Total                                                                                                                                                                                                  | int64   | 66 - 9840024           |                     nan |                        0 |\n|  9 | B25008_001E | total population in occupied housing units                                    | TOTAL POPULATION IN OCCUPIED HOUSING UNITS BY TENURE: Estimate!!Total                                                                                                                                                              | int64   | 62 - 9664175           |                     nan |                        0 |\n| 10 | B25002_002E | total occupied housing units                                                  | OCCUPANCY STATUS: Estimate!!Total!!Occupied                                                                                                                                                                                        | int64   | 35 - 3218511           |                     nan |                        0 |\n| 11 | B25003_003E | total renter occupied housing units                                           | TENURE: Estimate!!Total!!Renter occupied                                                                                                                                                                                           | int64   | 14 - 1695180           |                     nan |                        0 |\n| 12 | B25002_001E | total housing units for which occupancy status is known                       | OCCUPANCY STATUS: Estimate!!Total                                                                                                                                                                                                  | int64   | 70 - 3441416           |                     nan |                        0 |\n| 13 | B09020_021E | total 65+ living in group quarters                                            | RELATIONSHIP BY HOUSEHOLD TYPE (INCLUDING LIVING ALONE) FOR THE POPULATION 65 YEARS AND OVER: Estimate!!Total!!In group quarters                                                                                                   | int64   | 0 - 37611              |                     nan |                        0 |\n| 14 | B01001_026E | total female population                                                       | SEX BY AGE: Estimate!!Total!!Female                                                                                                                                                                                                | int64   | 20 - 4987765           |                     nan |                        0 |\n| 15 | B11001_006E | total female-headed family households                                         | HOUSEHOLD TYPE (INCLUDING LIVING ALONE): Estimate!!Total!!Family households!!Other family!!Female householder, no husband present                                                                                                  | int64   | 0 - 498851             |                     nan |                        0 |\n| 16 | B11001_001E | total households for which household type is known                            | HOUSEHOLD TYPE (INCLUDING LIVING ALONE): Estimate!!Total                                                                                                                                                                           | int64   | 35 - 3218511           |                     nan |                        0 |\n| 17 | B25002_003E | total vacant housing units                                                    | OCCUPANCY STATUS: Estimate!!Total!!Vacant                                                                                                                                                                                          | int64   | 35 - 245069            |                     nan |                        0 |\n| 18 | B19025_001E | aggregate household income                                                    | AGGREGATE HOUSEHOLD INCOME IN THE PAST 12 MONTHS (IN 2012 INFLATION-ADJUSTED DOLLARS): Estimate!!Aggregate household income in the past 12 months (in 2012 inflation-adjusted dollars)                                             | int64   | 1785600 - 263044380000 |                     nan |                        0 |\n| 19 | B23022_025E | total males unemployed for last 12 months                                     | SEX BY WORK STATUS IN THE PAST 12 MONTHS BY USUAL HOURS WORKED PER WEEK IN THE PAST 12 MONTHS BY WEEKS WORKED IN THE PAST 12 MONTHS FOR THE POPULATION 16 TO 64 YEARS: Estimate!!Total!!Male!!Did not work in the past 12 months   | int64   | 1 - 726803             |                     nan |                        0 |\n| 20 | B23022_049E | total females unemployed for last 12 months                                   | SEX BY WORK STATUS IN THE PAST 12 MONTHS BY USUAL HOURS WORKED PER WEEK IN THE PAST 12 MONTHS BY WEEKS WORKED IN THE PAST 12 MONTHS FOR THE POPULATION 16 TO 64 YEARS: Estimate!!Total!!Female!!Did not work in the past 12 months | int64   | 0 - 1131737            |                     nan |                        0 |\n| 21 | B23022_001E | total population for which unemployment and sex cross-tabulations known       | SEX BY WORK STATUS IN THE PAST 12 MONTHS BY USUAL HOURS WORKED PER WEEK IN THE PAST 12 MONTHS BY WEEKS WORKED IN THE PAST 12 MONTHS FOR THE POPULATION 16 TO 64 YEARS: Estimate!!Total                                             | int64   | 45 - 6658456           |                     nan |                        0 |\n| 22 | B17021_002E | total population below poverty level                                          | POVERTY STATUS OF INDIVIDUALS IN THE PAST 12 MONTHS BY LIVING ARRANGEMENT: Estimate!!Total!!Income in the past 12 months below poverty level                                                                                       | int64   | 0 - 1658231            |                     nan |                        0 |\n| 23 | B17021_001E | total population for which poverty information available                      | POVERTY STATUS OF INDIVIDUALS IN THE PAST 12 MONTHS BY LIVING ARRANGEMENT: Estimate!!Total                                                                                                                                         | int64   | 64 - 9684503           |                     nan |                        0 |\n| 24 | B25024_010E | number of mobile home housing units in structure                              | UNITS IN STRUCTURE: Estimate!!Total!!Mobile home                                                                                                                                                                                   | int64   | 0 - 85377              |                     nan |                        0 |\n| 25 | B25024_001E | total housing units in structure                                              | UNITS IN STRUCTURE: Estimate!!Total                                                                                                                                                                                                | int64   | 70 - 3441416           |                     nan |                        0 |\n| 26 | C24010_038E | total female employed                                                         | SEX BY OCCUPATION FOR THE CIVILIAN EMPLOYED POPULATION 16 YEARS AND OVER: Estimate!!Total!!Female                                                                                                                                  | int64   | 12 - 2056023           |                     nan |                        0 |\n| 27 | C24010_001E | total population for which sex and occupation known                           | SEX BY OCCUPATION FOR THE CIVILIAN EMPLOYED POPULATION 16 YEARS AND OVER: Estimate!!Total                                                                                                                                          | int64   | 54 - 4495118           |                     nan |                        0 |\n| 28 | B19055_002E | total households with social security income                                  | SOCIAL SECURITY INCOME IN THE PAST 12 MONTHS FOR HOUSEHOLDS: Estimate!!Total!!With Social Security income                                                                                                                          | int64   | 9 - 726298             |                     nan |                        0 |\n| 29 | B19055_001E | total households for which social security income status known                | SOCIAL SECURITY INCOME IN THE PAST 12 MONTHS FOR HOUSEHOLDS: Estimate!!Total                                                                                                                                                       | int64   | 35 - 3218511           |                     nan |                        0 |\n| 30 | B09002_002E | total children in married couple families                                     | OWN CHILDREN UNDER 18 YEARS BY FAMILY TYPE AND AGE: Estimate!!Total!!In married-couple families                                                                                                                                    | int64   | 0 - 1380977            |                     nan |                        0 |\n| 31 | B09002_001E | total children for which family type and age are known                        | OWN CHILDREN UNDER 18 YEARS BY FAMILY TYPE AND AGE: Estimate!!Total                                                                                                                                                                | int64   | 0 - 2032147            |                     nan |                        0 |\n| 32 | B19001_017E | total households with over 200k income                                        | HOUSEHOLD INCOME IN THE PAST 12 MONTHS (IN 2012 INFLATION-ADJUSTED DOLLARS): Estimate!!Total!!$200,000 or more                                                                                                                     | int64   | 0 - 208954             |                     nan |                        0 |\n| 33 | B06007_005E | total Spanish-speakers who speak english less than very well                  | PLACE OF BIRTH BY LANGUAGE SPOKEN AT HOME AND ABILITY TO SPEAK ENGLISH IN THE UNITED STATES: Estimate!!Total!!Speak Spanish!!Speak English less than "very well"                                                                   | float64 | 0 - 1695391            |                     nan |                        0 |\n| 34 | B06007_008E | total people who speak another language and speak English less than very well | PLACE OF BIRTH BY LANGUAGE SPOKEN AT HOME AND ABILITY TO SPEAK ENGLISH IN THE UNITED STATES: Estimate!!Total!!Speak other languages!!Speak English less than "very well"                                                           | float64 | 0 - 743418             |                     nan |                        0 |\n| 35 | B06007_001E | total population with known language spoken at home and English ability       | PLACE OF BIRTH BY LANGUAGE SPOKEN AT HOME AND ABILITY TO SPEAK ENGLISH IN THE UNITED STATES: Estimate!!Total                                                                                                                       | float64 | 66 - 9188362           |                     nan |                        0 |\n| 36 | B16010_002E | total population with less than a high school graduate education              | EDUCATIONAL ATTAINMENT AND EMPLOYMENT STATUS BY LANGUAGE SPOKEN AT HOME FOR THE POPULATION 25 YEARS AND OVER: Estimate!!Total!!Less than high school graduate                                                                      | int64   | 5 - 1508273            |                     nan |                        0 |\n| 37 | B16010_001E | total for which education, employment, language at home known                 | EDUCATIONAL ATTAINMENT AND EMPLOYMENT STATUS BY LANGUAGE SPOKEN AT HOME FOR THE POPULATION 25 YEARS AND OVER: Estimate!!Total                                                                                                      | int64   | 65 - 6380366           |                     nan |                        0 |\n| 38 | C24050_002E | total population in extractive industries                                     | INDUSTRY BY OCCUPATION FOR THE CIVILIAN EMPLOYED POPULATION 16 YEARS AND OVER: Estimate!!Total!!Agriculture, forestry, fishing and hunting, and mining                                                                             | int64   | 0 - 54942              |                     nan |                        0 |\n| 39 | C24050_001E | total population for which industry known                                     | INDUSTRY BY OCCUPATION FOR THE CIVILIAN EMPLOYED POPULATION 16 YEARS AND OVER: Estimate!!Total                                                                                                                                     | int64   | 54 - 4495118           |                     nan |                        0 |\n| 40 | C24050_029E | total people in service occupations                                           | INDUSTRY BY OCCUPATION FOR THE CIVILIAN EMPLOYED POPULATION 16 YEARS AND OVER: Estimate!!Total!!Service occupations                                                                                                                | int64   | 4 - 837607             |                     nan |                        0 |\n| 41 | B08201_002E | total households with no available vehicle                                    | HOUSEHOLD SIZE BY VEHICLES AVAILABLE: Estimate!!Total!!No vehicle available                                                                                                                                                        | int64   | 0 - 577967             |                     nan |                        0 |\n| 42 | B08201_001E | total households for which vehicle status and family size known               | HOUSEHOLD SIZE BY VEHICLES AVAILABLE: Estimate!!Total                                                                                                                                                                              | int64   | 35 - 3218511           |                     nan |                        0 |\n| 43 | B25064_001E | median gross rent                                                             | MEDIAN GROSS RENT (DOLLARS): Estimate!!Median gross rent                                                                                                                                                                           | int64   | 296 - 1678             |                     nan |                        0 |\n| 44 | B25077_001E | median home value                                                             | MEDIAN VALUE (DOLLARS): Estimate!!Median value (dollars)                                                                                                                                                                           | float64 | 19400 - 944100         |                     nan |                        1 |



| Label | Alias | Definition | Type | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| B01002_001E | median age | median age | float64 | Accuracy | 21.7 - 63 | Missing Data Value(s) | Missing Data Frequency |
| B03002_001E | population race/ethnicity | total population of respondents to race/ethnicity | int64 | Accuracy | 66 - 9840024 | Missing Data Value(s) | Missing Data Frequency |
| B03002_004E | Black | total Black population | int64 | Accuracy | 0 - 1267825 | Missing Data Value(s) | Missing Data Frequency |
| B03002_005E | Native American | total Native American population | int64 | Accuracy | 0 - 59060 | Missing Data Value(s) | Missing Data Frequency |
| B03002_006E | Asian | total Asian population | int64 | Accuracy | 0 - 1343920 | Missing Data Value(s) | Missing Data Frequency |
| B03002_012E | Latinx | total Latinx population | int64 | Accuracy | 0 - 4694846 | Missing Data Value(s) | Missing Data Frequency |
| B06001_002E | under 5 | total population under 5 years of age | float64 | Accuracy | 0 - 651662 | Missing Data Value(s) | Missing Data Frequency |
| B09020_001E | above 65 |  total population over 65 years of age | int64 | Accuracy | 5 - 1078555 | Missing Data Value(s) | Missing Data Frequency |
| B01003_001E | population | total population | int64 | Accuracy | 66 - 9840024 | Missing Data Value(s) | Missing Data Frequency |
| B25008_001E | population with housing | total population in occupied housing units | int64 | Accuracy | 62 - 9664175 | Missing Data Value(s) | Missing Data Frequency |
| B25002_002E | occupied housing | total occupied housing units | int64 | Accuracy | 35 - 3218511 | Missing Data Value(s) | Missing Data Frequency |
| B25003_003E | renter-occupied housing | total renter occupied housing units | int64 | Accuracy | 14 - 1695180 | Missing Data Value(s) | Missing Data Frequency |
| B25002_001E | housing units with known occupancy status | total housing units for which occupancy status is known | int64 | Accuracy | 70 - 3441416 | Missing Data Value(s) | Missing Data Frequency |
| B09020_021E | elderly in assisted living | total 65+ living in group quarters | int64 | Accuracy | 0 - 37611 | Missing Data Value(s) | Missing Data Frequency |
| B01001_026E | female | total female population | int64 | Accuracy | 20 - 4987765 | Missing Data Value(s) | Missing Data Frequency |
| B11001_006E | female-headed households | total female-headed family households | int64 | Accuracy | 0 - 498851 | Missing Data Value(s) | Missing Data Frequency |
| B11001_001E | total households | total households for which household type is known | int64 | Accuracy | 35 - 3218511 | Missing Data Value(s) | Missing Data Frequency |
| B25002_003E | vacant housing | total vacant housing units | int64 | Accuracy | 35 - 245069 | Missing Data Value(s) | Missing Data Frequency |
| B19025_001E | aggregate household income | aggregate household income | int64 | Accuracy | 1785600 - 263044380000 | Missing Data Value(s) | Missing Data Frequency |
| B23022_025E | unemployed males | total males unemployed for last 12 months | int64 | Accuracy | 1 - 726803 | Missing Data Value(s) | Missing Data Frequency |
| B23022_049E | unemployed females | total females unemployed for last 12 months | int64 | Accuracy | 0 - 1131737 | Missing Data Value(s) | Missing Data Frequency |
| B23022_001E | unemployment and sex known | total population for which unemployment and sex cross-tabulations known | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B17021_002E | impoverished | total population below poverty level | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B17021_001E | poverty status known | total population for which poverty information available | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B25024_010E | mobile homes | number of mobile home housing units in structure | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B25024_001E | housing units | total housing units in structure | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| C24010_038E | total female employed | total female employed | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| C24010_001E | sex and occupation known | total population for which sex and occupation known | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B19055_002E | households with social security | total households with social security income | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B19055_001E | households social security status known | total households for which social security income status known | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B09002_002E | children married couple families | total children in married couple families | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B09002_001E | children with known age and family type | total children for which family type and age are known | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B19001_017E | high-income households | total households with over 200k income | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B06007_005E | Spanish with poor English | total Spanish-speakers who speak english less than very well | float64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B06007_008E | other language with poor English | total people who speak another language and speak English less than very well | float64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B06007_001E | language known | total population with known language spoken at home and English ability | float64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B16010_002E | less than high school diploma | total population with less than a high school graduate education | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B16010_001E | known education, employment, language | total for which education, employment, language at home known | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| C24050_002E | extractive occupation | total population in extractive industries | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| C24050_001E | industry known | total population for which industry known | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| C24050_029E | service occupations | total people in service occupations | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B08201_002E | households without vehicles | total households with no available vehicle | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B08201_001E | households with known vehicle status and family size | total households for which vehicle status and family size known | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B25064_001E | median gross rent | median gross rent | int64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| B25077_001E | median home value | median home value | float64 | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |



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
