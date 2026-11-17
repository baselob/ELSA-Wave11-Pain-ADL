# ELSA Wave 11 Pain and ADL Analysis — Reproducibility Guide

## Project overview

This project develops and validates an analysis-ready dataset (ARD) from the English Longitudinal Study of Ageing (ELSA) Wave 11 to investigate associations between self-reported pain severity and limitations in six basic activities of daily living (ADLs).

The workflow includes cohort selection, phenotype derivation, data-quality validation, descriptive analyses and exploratory weighted logistic regression.

## Source data and access

Source: ELSA Wave 11, accessed through the UK Data Service under the applicable End User Licence.

Required source filename:

`wave_11_elsa_data_eul.dta`

The source dataset is not included in the reproducibility package because access and redistribution are subject to UK Data Service conditions. Researchers must obtain the dataset through an authorised access route.

## Required software

- R and RStudio, or another environment capable of rendering R Markdown.
- R packages: `rmarkdown`, `knitr`, `haven`, `ggplot2` and `scales`.

Install missing packages using:

```r
install.packages(c("rmarkdown", "knitr", "haven", "ggplot2", "scales"))
```

## Folder structure

The following folder structure must be established locally before running the analysis. The Raw data directory and original ELSA dataset are not included in this GitHub repository and must be obtained separately through authorised UK Data Service access.

```text
MSt assignment ELSA/
├── README.md
├── Raw data/
│   └── wave_11_elsa_data_eul.dta
└── ELSA_MSt_Assignment/
    ├── HDS_M1_BaselObeidat_2611.Rmd
    ├── ELSA_Synthetic_Reproducibility_Demonstration.Rmd
    ├── ELSA_Wave11_Pain_ADL_SYNTHETIC.csv
    └── outputs/
        ├── ELSA_Wave11_Pain_ADL_ARD.csv
        └── ELSA_Wave11_Pain_ADL_DataDictionary.csv
```

The `outputs` directory is created automatically by the export code.

## Reproduction steps

1. Obtain authorised access to ELSA Wave 11 and place the source `.dta` file in the `Raw data` folder.
2. Open the R Markdown file in RStudio.
3. Install the required R packages if necessary.
4. Knit the R Markdown document to HTML, or run the following command from RStudio. Set the working directory to the repository root first:

```r
rmarkdown::render("ELSA_MSt_Assignment/HDS_M1_BaselObeidat_2611.Rmd", knit_root_dir = "ELSA_MSt_Assignment")
```

5. Review the generated HTML report and the CSV files in the `outputs` folder.

The workflow uses the relative source path `../Raw data/wave_11_elsa_data_eul.dta`. If the project is stored elsewhere, preserve the same relative folder structure or update `data_path` accordingly.

## Expected outputs

**Analysis-ready dataset:** `ELSA_Wave11_Pain_ADL_ARD.csv`

Expected dimensions: 6,169 participant records and six variables:

- `participant_id`
- `pain_category`
- `adl_limitation`
- `age`
- `sex`
- `cross_sectional_weight`

**Data dictionary:** `ELSA_Wave11_Pain_ADL_DataDictionary.csv`

Documents source variables, coding decisions and missing-data rules.

**Technical report:** Knitted HTML document containing the methodology, validation checks, exploratory results and critical appraisal.

## Validation and limitations

The workflow checks participant uniqueness, analytical completeness, eligible survey weights, source-data consistency and agreement between derived and independently reconstructed pain and ADL classifications.

These checks assess technical integrity and internal consistency; they do not establish external clinical validity.

The analysis is cross-sectional. Weighted regression is exploratory and does not incorporate the complete ELSA complex survey design.

## Data governance

Participant-level data and derived outputs must be handled according to the UK Data Service End User Licence and applicable confidentiality requirements. Do not publicly distribute the source data or participant-level ARD without confirming that redistribution is authorised.

The R Markdown source, methodological documentation and data dictionary can be reviewed separately from restricted participant-level data, subject to any applicable disclosure requirements.

## GitHub repository

The reproducibility code, metadata, documentation and synthetic demonstration materials are available at:

https://github.com/baselob/ELSA-Wave11-Pain-ADL

The restricted ELSA source data and participant-level analysis-ready dataset are not publicly distributed.