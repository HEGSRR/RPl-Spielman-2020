
### USA Counties Cartographic Boundaries

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
