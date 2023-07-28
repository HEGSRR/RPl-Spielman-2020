# Title of Study : Pre-analysis Registration

### Authors

- Liam Smith\*, lwsmith@middlebury.edu, @Liam-W-Smith, ORCID link, Middlebury College
- Joseph Holler, josephh@middlebury.edu , @josephholler, ORCID link, Middlebury College

\* Corresponding author and creator

### Abstract

This study is a *replication* of:

> Spielman, S. E., Tuccillo, J., Folch, D. C., Schweikert, A., Davies, R., Wood, N., & Tate, E. (2020). Evaluating Social Vulnerability Indicators: Criteria and their Application to the Social Vulnerability Index. Natural Hazards, 100(1), 417–436. https://doi.org/10.1007/s11069-019-03820-z

The Spielman et al (2020) paper is in turn a replication of:

> Cutter, S. L., Boruff, B. J., & Shirley, W. L. (2003). Social vulnerability to environmental hazards. Social Science Quarterly, 84(2), 242–261. https://doi.org/10.1111/1540-6237.8402002

Spielman et al (2020) developed methods to evaluate the internal consistency and construct validity of the Cutter, Boruff and Shirley (2003) Social Vulnerability Index (SoVI).
First, they reproduce a national SoVI model and validate it against an SPSS procedure provided by the original research group (Hazards Vulnerability Research Institute at University of South Carolina).
The original SoVI uses 42 independent z-score normalized variables from the U.S. Census, reduces the data to factors using Principal Components Analysis, selects the first eleven factors, inverts factors with inverse relationships to social vulnerability, and sums the factors together to produce a SoVI score.
The reproduced SoVI model was slightly different than the original model due to changes in U.S. Census data, using only 28 variables.

Spielman et al. modify the geographic extent of the SoVI calculation by calculating SoVI on a national extent, and then recalculating for each of ten Federal Emergency Management Agency (FEMA) regions, and again for a single state or cluster of states within each of the ten regions, resulting in 21 total indices.
Internal consistency is assessed by calculating the spearman rank correlation coefficient of the SoVI score for counties in the state model compared to the FEMA region model and national model.
Construct validity is assessed by summing the loadings for each input variable across the PCA factors in each model and calculating the variables sign (positive/negative) and the rank of the variable's total loading compared to the other variables.
These signs and ranks are summarized across all 21 versions of the SoVI model with regard to the number of times the sign is different from the national model and the distributions of ranks.

In this replication study, we extend Spielman et al's work by addressing the robustness of SoVI in the temporal dimension.
Specifically, we will construct a national SoVI model using 1-year, 3-year, and 5-year ACS data for each year between 2009 and 2013.
We will employ the same methods as Spielman et al, evaluating internal consistency by calculating Spearman's rank correlations between model's of the same year and addressing theoretical consistency by summarizing the distributions of sign and rank amongst all models for each variable.

### Study Metadata

- `Key words`: Social vulnerability, evaluation, social indicators
- `Subject`: Social and Behavioral Sciences: Geography: Human Geography
- `Date created`: June 19, 2023
- `Date modified`: July 28, 2023
- `Spatial Coverage`: United States, excluding Puerto Rico
- `Spatial Resolution`: Counties and county equivalents
- `Spatial Reference System`: EPSG:4269
- `Temporal Coverage`: 2008-2021
- `Temporal Resolution`: New dataset collected annually
- `Funding Name`: NSF Division of Behavioral and Cognitive Sciences
- `Funding Title`: Transforming Theory and STEM Education Through Reproductions and Replications in the Geographical Sciences
- `Award info URI`: https://www.nsf.gov/awardsearch/showAward?AWD_ID=2049837
- `Award number`: 2049837

#### Original study spatio-temporal metadata

- `Spatial Coverage`: United States, excluding Puerto Rico
- `Spatial Resolution`: Counties and county equivalents
- `Spatial Reference System`: EPSG:4269
- `Temporal Coverage`: 2009 - 2013
- `Temporal Resolution`: One-time measurement, does not address change over time

## Study design

In our previous work, we computationally reproduced Spielman et al's original paper using the code provided in [their Github repository](https://github.com/geoss/sovi-validity).
( ALSO LINK TO OUR REPRODUCTION PERHAPS )

The original paper was a replication study testing the sensitivity of SoVI to changes in geographic extent.
Spielman et al addressed the following hypotheses in their work:

> OR-H1: SoVI is internally inconsistent.

To address this hypothesis, Spielman et al illustrated that SoVI is not robust to changes in geographic extent by calculating SoVI scores for ten selected states or groups of states on three geographic extents: national, FEMA region, and state(s).
The counties within the state(s) of interest were then selected and ranked according to their SoVI score.
OR-H1 was tested by calculating Spearman's rank correlation between the state and FEMA region models and between the state and national models.

> OR-H2: SoVI is theoretically inconsistent.

To address this hypothesis, Spielman et al used the same SoVI models as described under OR-H1.
For each model, they summed all of the PCA factors together to determine the net influence of each variable in each model.
Then they recorded the signs of each variable and calculated the number of deviations of the ten state and FEMA region models from the national model.
They also ranked the variables by absolute value for each model and calculated summary statistics regarding the distribution of ranks for each variable amongst all models.
Spielman et al did not use a particular statistical method to test OR-H2, but illustrated substantial disagreements between variable rankings and signs amongst the 21 SoVI models.

In this study, we plan to replicate Spielman et al's work, using the same methods to evaluate internal and theoretical consistency but doing so with respect to temporal extent rather than spatial extent.
In our replication, we begin with the same hypotheses as Spielman et al, but we will test those hypotheses by varying the temporal extent rather than spatial extent.

> RPr-H1: SoVI is internally inconsistent.

To address this hypothesis, we will calculate SoVI scores for the entire nation (excluding Puerto Rico) using three temporal extents: 1-year ACS data, 3-year ACS data, and 5-year ACS data.
We will do this for every year that such data is available, which happens to be the years 2009 through 2013.
We will then rank the counties in each model according to their SoVI scores and test RPr-H1 by calculating Spearman's rank correlation coefficients between the 1-year and 3-year models and between the 1-year and 5-year models for each year.

> RPr-H2: SoVI is theoretically inconsistent.

To address this hypothesis, we will use the same SoVI models as described under RPr-H1.
For each model, we will sum all of the PCA components together to determine the net influence of each variable in each model.
Then we will record the signs of each variable and calculate the number of deviations of variables' signs from the signs that we expect.
(DIFFERENT FROM SPIELMAN ET AL, WHO COMPARE THE 20 STATE AND FEMA MODELS TO THE NATIONAL MODEL)
We will also rank the variables by absolute value for each model and calculate summary statistics regarding the distribution of ranks for each variable amongst all models.

## Materials and procedure

### Computational environment

Currently, we are using a 2020 MacBook Pro running on macOS Ventura 13.3.1.
We anticipate collaborators working on the project from different computers and different operating systems, and we seek to containerize the project so that scripts can be run on many different machines.

In our reproduction of the original study, we used a containerized conda environment consisting of the following software and packages:

- Python 3.9.16
- pandas 1.4.4
- geopandas 0.13.2
- pyhere 1.0.0
- scipy 1.10.1
- numpy 1.21.5
- MDP 3.5
- pygris 0.1.5
- libpysal 4.7.0
- lxml 4.9.3
- tabulate 0.9.0
- matplotlib 3.7.1
- mapclassify 2.5.0

We will use the same environment for our replication study, adding in additional packages if necessary.

### Data and variables

(STOPPED HERE 7/28)
For Spielman et al's original study, the data sources were the 2008-2012 5-year American Community Survey and the 2010 decennial census.
Spielman et al downloaded their data from Social Explorer; in our reproduction, we pull our data directly from the census into Python via a census API package known as pygris.
Since we are reproducing and replicating the work of Spielman et al, the variables we use are the same as those used in their study.
These variables are based on the original work by Cutter et al to create SoVI, and cover a wide range of social and demographic information, the particulars of which are described below.

#### (1) 2008-2012 American Community Survey (5-year) -- used in both original study and reproduction

**Standard Metadata**

- `Abstract`: The 5-year ACS provides estimates surrounding demographic information in the USA. These estimates are more reliable than 1-year and 3-year estimates but less reliable than decennial census data. On the other hand, 5-year estimates are less current than 1-year and 3-year estimates because they represent measurements taken over 60 months. See the [census website](https://www.census.gov/programs-surveys/acs/guidance/estimates.html) for more details.
- `Spatial Coverage`: United States, excluding Puerto Rico
- `Spatial Resolution`: County and county-equivalents
- `Spatial Reference System`: None, just attribute data
- `Temporal Coverage`: 2008-2012
- `Temporal Resolution`: One-time observations
- `Lineage`: Original data downloaded from Social Explorer and then placed in the [original study's GitHub repository](https://github.com/geoss/sovi-validity). Reproduction data obtained directly from the census via API.
- `Distribution`: The reproduction data is distributed via a census API. See the detailed tables on the [census website](https://www.census.gov/data/developers/data-sets/acs-5year/2012.html) and instructions for drawing census data directly into python on the [pygris website](https://walker-data.com/pygris/). Spielman et al originally accessed the ACS data with Social Explorer from the following two tables.
  - http://www.socialexplorer.com/pub/reportdata/HtmlResults.aspx?reportid=R10728365
  - http://www.socialexplorer.com/pub/reportdata/HtmlResults.aspx?reportid=R10775556
- `Constraints`: Census data is available in the public domain
- `Data Quality`: Margin of error provided by the Census Bureau for relevant variables
- `Variables`:

| Reproduction Label   | Spielman Label      | Alias                                                                         | Definition                                                                                                                                                                                                                         | Type    | Domain                 |   Missing Data Value(s) |   Missing Data Frequency |
|:---------------------|:--------------------|:------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------|:-----------------------|------------------------:|-------------------------:|
| B01002_001E          | ACS12_5yr_B01002001 | median age                                                                    | MEDIAN AGE BY SEX: Estimate!!Median age!!Total                                                                                                                                                                                     | float64 | 21.7 - 63              |                     nan |                        0 |
| B03002_001E          | ACS12_5yr_B03002001 | total population of respondents to race/ethnicity                             | HISPANIC OR LATINO ORIGIN BY RACE: Estimate!!Total                                                                                                                                                                                 | int64   | 66 - 9840024           |                     nan |                        0 |
| B03002_004E          | ACS12_5yr_B03002004 | total Black population                                                        | HISPANIC OR LATINO ORIGIN BY RACE: Estimate!!Total!!Not Hispanic or Latino!!Black or African American alone                                                                                                                        | int64   | 0 - 1267825            |                     nan |                        0 |
| B03002_005E          | ACS12_5yr_B03002005 | total Native American population                                              | HISPANIC OR LATINO ORIGIN BY RACE: Estimate!!Total!!Not Hispanic or Latino!!American Indian and Alaska Native alone                                                                                                                | int64   | 0 - 59060              |                     nan |                        0 |
| B03002_006E          | ACS12_5yr_B03002006 | total Asian population                                                        | HISPANIC OR LATINO ORIGIN BY RACE: Estimate!!Total!!Not Hispanic or Latino!!Asian alone                                                                                                                                            | int64   | 0 - 1343920            |                     nan |                        0 |
| B03002_012E          | ACS12_5yr_B03002012 | total Latinx population                                                       | HISPANIC OR LATINO ORIGIN BY RACE: Estimate!!Total!!Hispanic or Latino                                                                                                                                                             | int64   | 0 - 4694846            |                     nan |                        0 |
| B06001_002E          | ACS12_5yr_B06001002 | total population under 5 years of age                                         | PLACE OF BIRTH BY AGE IN THE UNITED STATES: Estimate!!Total!!Under 5 years                                                                                                                                                         | float64 | 0 - 651662             |                     nan |                        0 |
| B09020_001E          | ACS12_5yr_B09020001 | total population over 65 years of age                                         | RELATIONSHIP BY HOUSEHOLD TYPE (INCLUDING LIVING ALONE) FOR THE POPULATION 65 YEARS AND OVER: Estimate!!Total                                                                                                                      | int64   | 5 - 1078555            |                     nan |                        0 |
| B01003_001E          | ACS12_5yr_B01003001 | total population                                                              | TOTAL POPULATION: Estimate!!Total                                                                                                                                                                                                  | int64   | 66 - 9840024           |                     nan |                        0 |
| B25008_001E          | ACS12_5yr_B25008001 | total population in occupied housing units                                    | TOTAL POPULATION IN OCCUPIED HOUSING UNITS BY TENURE: Estimate!!Total                                                                                                                                                              | int64   | 62 - 9664175           |                     nan |                        0 |
| B25002_002E          | ACS12_5yr_B25002002 | total occupied housing units                                                  | OCCUPANCY STATUS: Estimate!!Total!!Occupied                                                                                                                                                                                        | int64   | 35 - 3218511           |                     nan |                        0 |
| B25003_003E          | ACS12_5yr_B25003003 | total renter occupied housing units                                           | TENURE: Estimate!!Total!!Renter occupied                                                                                                                                                                                           | int64   | 14 - 1695180           |                     nan |                        0 |
| B25002_001E          | ACS12_5yr_B25002001 | total housing units for which occupancy status is known                       | OCCUPANCY STATUS: Estimate!!Total                                                                                                                                                                                                  | int64   | 70 - 3441416           |                     nan |                        0 |
| B09020_021E          | ACS12_5yr_B09020021 | total 65+ living in group quarters                                            | RELATIONSHIP BY HOUSEHOLD TYPE (INCLUDING LIVING ALONE) FOR THE POPULATION 65 YEARS AND OVER: Estimate!!Total!!In group quarters                                                                                                   | int64   | 0 - 37611              |                     nan |                        0 |
| B01001_026E          | ACS12_5yr_B01001026 | total female population                                                       | SEX BY AGE: Estimate!!Total!!Female                                                                                                                                                                                                | int64   | 20 - 4987765           |                     nan |                        0 |
| B11001_006E          | ACS12_5yr_B11001006 | total female-headed family households                                         | HOUSEHOLD TYPE (INCLUDING LIVING ALONE): Estimate!!Total!!Family households!!Other family!!Female householder, no husband present                                                                                                  | int64   | 0 - 498851             |                     nan |                        0 |
| B11001_001E          | ACS12_5yr_B11001001 | total households for which household type is known                            | HOUSEHOLD TYPE (INCLUDING LIVING ALONE): Estimate!!Total                                                                                                                                                                           | int64   | 35 - 3218511           |                     nan |                        0 |
| B25002_003E          | ACS12_5yr_B25002003 | total vacant housing units                                                    | OCCUPANCY STATUS: Estimate!!Total!!Vacant                                                                                                                                                                                          | int64   | 35 - 245069            |                     nan |                        0 |
| B19025_001E          | ACS12_5yr_B19025001 | aggregate household income                                                    | AGGREGATE HOUSEHOLD INCOME IN THE PAST 12 MONTHS (IN 2012 INFLATION-ADJUSTED DOLLARS): Estimate!!Aggregate household income in the past 12 months (in 2012 inflation-adjusted dollars)                                             | int64   | 1785600 - 263044380000 |                     nan |                        0 |
| B23022_025E          | ACS12_5yr_B23022025 | total males unemployed for last 12 months                                     | SEX BY WORK STATUS IN THE PAST 12 MONTHS BY USUAL HOURS WORKED PER WEEK IN THE PAST 12 MONTHS BY WEEKS WORKED IN THE PAST 12 MONTHS FOR THE POPULATION 16 TO 64 YEARS: Estimate!!Total!!Male!!Did not work in the past 12 months   | int64   | 1 - 726803             |                     nan |                        0 |
| B23022_049E          | ACS12_5yr_B23022049 | total females unemployed for last 12 months                                   | SEX BY WORK STATUS IN THE PAST 12 MONTHS BY USUAL HOURS WORKED PER WEEK IN THE PAST 12 MONTHS BY WEEKS WORKED IN THE PAST 12 MONTHS FOR THE POPULATION 16 TO 64 YEARS: Estimate!!Total!!Female!!Did not work in the past 12 months | int64   | 0 - 1131737            |                     nan |                        0 |
| B23022_001E          | ACS12_5yr_B23022001 | total population for which unemployment and sex cross-tabulations known       | SEX BY WORK STATUS IN THE PAST 12 MONTHS BY USUAL HOURS WORKED PER WEEK IN THE PAST 12 MONTHS BY WEEKS WORKED IN THE PAST 12 MONTHS FOR THE POPULATION 16 TO 64 YEARS: Estimate!!Total                                             | int64   | 45 - 6658456           |                     nan |                        0 |
| B17021_002E          | ACS12_5yr_B17021002 | total population below poverty level                                          | POVERTY STATUS OF INDIVIDUALS IN THE PAST 12 MONTHS BY LIVING ARRANGEMENT: Estimate!!Total!!Income in the past 12 months below poverty level                                                                                       | int64   | 0 - 1658231            |                     nan |                        0 |
| B17021_001E          | ACS12_5yr_B17021001 | total population for which poverty information available                      | POVERTY STATUS OF INDIVIDUALS IN THE PAST 12 MONTHS BY LIVING ARRANGEMENT: Estimate!!Total                                                                                                                                         | int64   | 64 - 9684503           |                     nan |                        0 |
| B25024_010E          | ACS12_5yr_B25024010 | number of mobile home housing units in structure                              | UNITS IN STRUCTURE: Estimate!!Total!!Mobile home                                                                                                                                                                                   | int64   | 0 - 85377              |                     nan |                        0 |
| B25024_001E          | ACS12_5yr_B25024001 | total housing units in structure                                              | UNITS IN STRUCTURE: Estimate!!Total                                                                                                                                                                                                | int64   | 70 - 3441416           |                     nan |                        0 |
| C24010_038E          | ACS12_5yr_C24010038 | total female employed                                                         | SEX BY OCCUPATION FOR THE CIVILIAN EMPLOYED POPULATION 16 YEARS AND OVER: Estimate!!Total!!Female                                                                                                                                  | int64   | 12 - 2056023           |                     nan |                        0 |
| C24010_001E          | ACS12_5yr_C24010001 | total population for which sex and occupation known                           | SEX BY OCCUPATION FOR THE CIVILIAN EMPLOYED POPULATION 16 YEARS AND OVER: Estimate!!Total                                                                                                                                          | int64   | 54 - 4495118           |                     nan |                        0 |
| B19055_002E          | ACS12_5yr_B19055002 | total households with social security income                                  | SOCIAL SECURITY INCOME IN THE PAST 12 MONTHS FOR HOUSEHOLDS: Estimate!!Total!!With Social Security income                                                                                                                          | int64   | 9 - 726298             |                     nan |                        0 |
| B19055_001E          | ACS12_5yr_B19055001 | total households for which social security income status known                | SOCIAL SECURITY INCOME IN THE PAST 12 MONTHS FOR HOUSEHOLDS: Estimate!!Total                                                                                                                                                       | int64   | 35 - 3218511           |                     nan |                        0 |
| B09002_002E          | ACS12_5yr_B09002002 | total children in married couple families                                     | OWN CHILDREN UNDER 18 YEARS BY FAMILY TYPE AND AGE: Estimate!!Total!!In married-couple families                                                                                                                                    | int64   | 0 - 1380977            |                     nan |                        0 |
| B09002_001E          | ACS12_5yr_B09002001 | total children for which family type and age are known                        | OWN CHILDREN UNDER 18 YEARS BY FAMILY TYPE AND AGE: Estimate!!Total                                                                                                                                                                | int64   | 0 - 2032147            |                     nan |                        0 |
| B19001_017E          | ACS12_5yr_B19001017 | total households with over 200k income                                        | HOUSEHOLD INCOME IN THE PAST 12 MONTHS (IN 2012 INFLATION-ADJUSTED DOLLARS): Estimate!!Total!!$200,000 or more                                                                                                                     | int64   | 0 - 208954             |                     nan |                        0 |
| B06007_005E          | ACS12_5yr_B06007005 | total Spanish-speakers who speak english less than very well                  | PLACE OF BIRTH BY LANGUAGE SPOKEN AT HOME AND ABILITY TO SPEAK ENGLISH IN THE UNITED STATES: Estimate!!Total!!Speak Spanish!!Speak English less than "very well"                                                                   | float64 | 0 - 1695391            |                     nan |                        0 |
| B06007_008E          | ACS12_5yr_B06007008 | total people who speak another language and speak English less than very well | PLACE OF BIRTH BY LANGUAGE SPOKEN AT HOME AND ABILITY TO SPEAK ENGLISH IN THE UNITED STATES: Estimate!!Total!!Speak other languages!!Speak English less than "very well"                                                           | float64 | 0 - 743418             |                     nan |                        0 |
| B06007_001E          | ACS12_5yr_B06007001 | total population with known language spoken at home and English ability       | PLACE OF BIRTH BY LANGUAGE SPOKEN AT HOME AND ABILITY TO SPEAK ENGLISH IN THE UNITED STATES: Estimate!!Total                                                                                                                       | float64 | 66 - 9188362           |                     nan |                        0 |
| B16010_002E          | ACS12_5yr_B16010002 | total population with less than a high school graduate education              | EDUCATIONAL ATTAINMENT AND EMPLOYMENT STATUS BY LANGUAGE SPOKEN AT HOME FOR THE POPULATION 25 YEARS AND OVER: Estimate!!Total!!Less than high school graduate                                                                      | int64   | 5 - 1508273            |                     nan |                        0 |
| B16010_001E          | ACS12_5yr_B16010001 | total for which education, employment, language at home known                 | EDUCATIONAL ATTAINMENT AND EMPLOYMENT STATUS BY LANGUAGE SPOKEN AT HOME FOR THE POPULATION 25 YEARS AND OVER: Estimate!!Total                                                                                                      | int64   | 65 - 6380366           |                     nan |                        0 |
| C24050_002E          | ACS12_5yr_C24050002 | total population in extractive industries                                     | INDUSTRY BY OCCUPATION FOR THE CIVILIAN EMPLOYED POPULATION 16 YEARS AND OVER: Estimate!!Total!!Agriculture, forestry, fishing and hunting, and mining                                                                             | int64   | 0 - 54942              |                     nan |                        0 |
| C24050_001E          | ACS12_5yr_C24050001 | total population for which industry known                                     | INDUSTRY BY OCCUPATION FOR THE CIVILIAN EMPLOYED POPULATION 16 YEARS AND OVER: Estimate!!Total                                                                                                                                     | int64   | 54 - 4495118           |                     nan |                        0 |
| C24050_029E          | ACS12_5yr_C24050029 | total people in service occupations                                           | INDUSTRY BY OCCUPATION FOR THE CIVILIAN EMPLOYED POPULATION 16 YEARS AND OVER: Estimate!!Total!!Service occupations                                                                                                                | int64   | 4 - 837607             |                     nan |                        0 |
| B08201_002E          | ACS12_5yr_B08201002 | total households with no available vehicle                                    | HOUSEHOLD SIZE BY VEHICLES AVAILABLE: Estimate!!Total!!No vehicle available                                                                                                                                                        | int64   | 0 - 577967             |                     nan |                        0 |
| B08201_001E          | ACS12_5yr_B08201001 | total households for which vehicle status and family size known               | HOUSEHOLD SIZE BY VEHICLES AVAILABLE: Estimate!!Total                                                                                                                                                                              | int64   | 35 - 3218511           |                     nan |                        0 |
| B25064_001E          | ACS12_5yr_B25064001 | median gross rent                                                             | MEDIAN GROSS RENT (DOLLARS): Estimate!!Median gross rent                                                                                                                                                                           | int64   | 296 - 1678             |                     nan |                        0 |
| B25077_001E          | ACS12_5yr_B25077001 | median home value                                                             | MEDIAN VALUE (DOLLARS): Estimate!!Median value (dollars)                                                                                                                                                                           | float64 | 19400 - 944100         |                     nan |                        1 |
| GEOID | Geo_FIPS | FIPS code unique identifier | Unique code for every county and county-equivalent in USA | string | 01001 - 56045 | None | 0 |


#### (2) 2010 Decennial Census -- used in Spielman et al's original study

**Standard Metadata**

- `Abstract`: Collected once every ten years, the decennial census documents demographic and population data in the United States.
- `Spatial Coverage`: United States, excluding Puerto Rico
- `Spatial Resolution`: County and county-equivalents
- `Spatial Reference System`: None, just attribute data
- `Temporal Coverage`: 2010
- `Temporal Resolution`: One-time observations
- `Lineage`: Original data downloaded from Social Explorer and then placed in the [original study's GitHub repository](https://github.com/geoss/sovi-validity).
- `Distribution`: Visit [this URL](http://www.socialexplorer.com/pub/reportdata/HtmlResults.aspx?reportid=R10728369) for access
- `Constraints`: Census data is available in the public domain
- `Data Quality`: Margin of error provided by the Census Bureau for relevant variables
- `Variables`:

| Label | Alias | Definition | Type | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| SE_T02A_002 | Land area | Area (Land) in square miles | float64 |  ... | 1.998779 - 145504.8 | nan | 0 |
| Geo_FIPS | FIPS code unique identifier | Unique code for every county and county-equivalent in USA | string | ... | g01001 - g56045 | None | 0 |


#### (3) USA Counties Shapefile -- used in Spielman et al's original study

**Standard Metadata**

- `Abstract`: No metadata provided, so it is unclear exactly where Spielman et al acquired this file but they likely downloaded it directly or indirectly from the census. The shapefile provides the geometries of counties and county-equivalents in the United States, with limited attribute information including county name and a unique identifier.
- `Spatial Coverage`: United States, excluding Puerto Rico
- `Spatial Resolution`: County and county-equivalents
- `Spatial Reference System`: EPSG:4269
- `Temporal Coverage`: Unknown
- `Temporal Resolution`: One-time observations
- `Lineage`: Unknown
- `Distribution`: Unknown. Presumably downloaded from census.
- `Constraints`: Census data is available in the public domain
- `Data Quality`: (ADD)
- `Variables`: For each variable, enter the following information. If you have two or more variables per data source, you may want to present this information in table form (shown below)

| Label | Alias | Definition | Type | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| geoFIPS | FIPS code unique identifer | Unique code for every county and county-equivalent in USA | string | ... | g01001 - g56045 | None | 0 |


#### (4) USA Counties Cartographic Boundaries -- used in replication study

**Standard Metadata**

- `Abstract`: The cartographic boundary files provided by the US census are simplified representations of the MAF/TIGER files. We use the 2010 boundary file because the census has not made such a file available for 2012 or 2011 and the original paper also used land area from 2010. This shapefile provides the geometries of counties and county-equivalents in the United States, with limited attribute information including land area.
- `Spatial Coverage`: United States, excluding Puerto Rico
- `Spatial Resolution`: County and county-equivalents
- `Spatial Reference System`: EPSG:4269
- `Temporal Coverage`: Specify the temporal extent of your study---i.e. the range of time represented by the data observations.
- `Temporal Resolution`: One-time observations
- `Lineage`: We use [pygris](https://walker-data.com/pygris/) to pull the data directly from the census into python.
- `Distribution`: This file is distributed via a census API. See more information on the [census website](https://www.census.gov/geographies/mapping-files/time-series/geo/carto-boundary-file.2010.html#list-tab-1556094155) and instructions for drawing census data directly into python on the [pygris website](https://walker-data.com/pygris/).
- `Constraints`: Census data is available in the public domain
- `Data Quality`: (ADD))
- `Variables`: For each variable, enter the following information. If you have two or more variables per data source, you may want to present this information in table form (shown below)

| Label | Alias | Definition | Type | Accuracy | Domain | Missing Data Value(s) | Missing Data Frequency |
| :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
| STATE | State-level FIPS code | State-level FIPS code | string | ... | 01 - 56 | None | 0 |
| COUNTY | County-level FIPS code | County-level FIPS code | string | ... | 001 - 840 | None | 0 |
| CENSUSAREA | land area | land area in square miles | float64 | ... | 1.999 - 145504.789 | nan | 0 |

#### ADD IN DATA FOR REPLICATION (ADD)

### Prior observations  

At the time of this study pre-registration, the authors had examined the python code and data from the original study and modified the code to reproduce the original results in a current environment.
This study is related to 0 prior studies by the authors.

We have already thoroughly observed datasets (1) through (4), as we have already reproduced the original study.
Specifically, we imported the data used by Spielman et al into a python script, and then used pygris to pull analogous data directly from the census into python.
We checked that our data and Spielman et al's data were equivalent despite coming from different sources, and then conducted Spielman et al's analysis on our new data.

ADD IN NOTE FOR OTHER DATA --> to be used in replication

### Threats to validity (ADD)

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

### Data transformations (ADD: is it necessary to do this for all SoVI vars?)

Describe all data transformations planned to prepare data sources for analysis.
This section should explain with the fullest detail possible how to transform data from its raw state from the time of acquisition or observation to the main analysis, including steps to check and mitigate threats to validity.
The method may anticipate contingencies, e.g. tests for normality and alternative decisions to make based on the results of the test.
More specifically, all the **geographic** and **variable** transformations required to prepare input data as described in the data and variables section above to match the study's spatio-temporal characteristics as described in the study metadata and study design sections.
Visual workflow diagrams may help communicate the methodology in this section.

Examples of **geographic** transformations include coordinate system transformations, aggregation, disaggregation, spatial interpolation, distance calculations, zonal statistics, etc.

Examples of **variable** transformations include standardization, normalization, constructed variables, imputation, classification, etc.

Be sure to include any steps planned to **exclude** observations with missing or outlier data, to **group** observations by attribute or geographic criteria, or to **impute** missing data.

### Analysis (ADD: discuss with Joe)

Describe the methods of analysis that will directly test the hypotheses or provide results to answer the research questions.
This section should explicitly define any spatial / statistical models and their parameters, including significance thresholds.
Also explain any follow-up analyses or validations.

## Results (ADD)

Describe how results are to be presented.

## Discussion (ADD)

Describe how the results are to be interpreted *vis a vis* each hypothesis or research question.

## Integrity Statement

The authors of this preregistration state that they completed this preregistration to the best of their knowledge and that no other preregistration exists pertaining to the same hypotheses and research.

## References (ADD)
