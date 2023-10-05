# Replication of Spielman et al's 2020 Evaluation of the Social Vulnerability Index

### Description

This study is a *reproduction* and *replication* of:

> Spielman, S. E., Tuccillo, J., Folch, D. C., Schweikert, A., Davies, R., Wood, N., & Tate, E. (2020). Evaluating Social Vulnerability Indicators: Criteria and their Application to the Social Vulnerability Index. Natural Hazards, 100(1), 417–436. https://doi.org/10.1007/s11069-019-03820-z

The original paper develops methods to evaluate the validity of social vulnerability indicators and applies them to SoVI, revealing issues with internal consistency and construct validity.
Their paper implements these methods by calculating SoVI over various spatial extents in the USA.
We first reproduce their results and then extend their work with a replication study, determining how robust SoVI is to changes over time.

### Contributors

- Liam Smith\*, lwsmith@middlebury.edu, @Liam-W-Smith, ORCID link, Middlebury College
- Joseph Holler, josephh@middlebury.edu , @josephholler, ORCID link, Middlebury College

\* Corresponding author and creator

### Study Metadata

- `Key words`: social vulnerability, evaluation, social indicators
- `Subject`: select from the [BePress Taxonomy](http://digitalcommons.bepress.com/cgi/viewcontent.cgi?article=1008&context=reference)
- `Date created`: 2023-06-12
- `Date modified`: 2023-08-02
- `Spatial Coverage`: United States, excluding Puerto Rico
- `Spatial Resolution`: Counties and county equivalents
- `Spatial Reference System`: EPSG 4269 NAD83
- `Temporal Coverage`: 2008 - 2012 (data is the 2012 5-year ACS)
- `Temporal Resolution`: Specify the temporal resolution of your study---i.e. the duration of time for which each observation represents or the revisit period for repeated observations
- `Funding Name`: NSF Directorate for Social, Behavioral and Economic Sciences
- `Funding Title`: Transforming theory-building and STEM education through reproductions and replications in the geographical sciences
- `Award info URI`: https://www.nsf.gov/awardsearch/showAward?AWD_ID=2049837
- `Award number`: BCS-2049837

### Related to

- `OSF Project`: https://doi.org/10.17605/OSF.IO/DZPE9
- `Reproduction Report Registration`: https://doi.org/10.17605/OSF.IO/4S62B
- `Replication Analysis Preregistration`: https://doi.org/10.17605/OSF.IO/9NTDS
- `Replication Report Registration`:
- `Preprint`:
- `Conference Presentation`:
- `Publication`:
- `Prior Study`: https://doi.org/10.1007/s11069-019-03820-z and https://github.com/geoss/sovi-validity
- `Prior Study`: https://doi.org/10.1111/1540-6237.8402002
- `Binder`: https://mybinder.org/v2/gh/HEGSRR/RPl-Spielman-2020/HEAD

### Metadata for access

- `Rights`: [LICENSE](LICENSE): BSD 3-Clause "New" or "Revised"
- `Resource type`: Collection
- `Resource language`: English
- `Conforms to`: Template for Reproducible and Replicable Research in Human-Environment and Geographical Sciences, DOI:[10.17605/OSF.IO/W29MQ](https://doi.org/10.17605/OSF.IO/W29MQ)

### Compendium structure and contents

This research compendium is structured with four main directories:

- `data`: contains subdirectories for `raw` data and `derived` data.
- `docs`: contains subdirectories for `manuscript`, `presentation`, and `report`
- `procedure`: contains subdirectories for `code` or software scripts, information about the computational `environment` in which the research was conducted, and non-code research `protocols`
- `results`: contains subdirectories for `figures`, formatted data `tables`, or `other` formats of research results.

The data, procedures, and results of this repository are outlined in three tables:
- Data: [data/data_index.csv](data/data_index.csv)
- Procedures: [procedure/procedure_index.csv](procedure/procedure_index.csv)
- Results: [results/results_index.csv](results/results_index.csv)

Important local **documents** include:
- Replication pre-analysis plan: [docs/report/RPl-Spielman-2020-analysis-plan.pdf](docs/report/RPl-Spielman-2020-analysis-plan.pdf)
- Reproduction study report: [docs/report/RPr-Spielman-2020-report.pdf](docs/report/RPr-Spielman-2020-report.pdf)
- Manuscript: ...
- Presentation: ...

#### Compendium reference

The [template_readme.md](template_readme.md) file contains more information on the design of this template and references used in the design.
The [Template_LICENSE](Template_LICENSE) file provides the BSD 3-Clause license for using this template.
To cite the template, please use [template_reference.bib](template_reference.bib) or:
> Kedron, P., & Holler, J. (2023). Template for Reproducible and Replicable Research in Human-Environment and Geographical Sciences. https://doi.org/10.17605/OSF.IO/W29MQ
