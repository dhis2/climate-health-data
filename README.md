## Chap-compatible CSV datasets

This repository contains **data only**. It does not include code or pipelines.

The datasets here are **already harmonized** (e.g. derived from OpenDengue) and are published in a format that can be consumed directly by [Chap](https://chap.dhis2.org). See the [Chap evaluation workflow documentation](https://chap.dhis2.org/chap-modeling-platform/chap-cli/evaluation-workflow) for detailed information on how to use these CSV files in a Chap evaluation.

---

## CSV structure (Chap schema)

All CSV files follow the same wide-table structure, with **one row per (time_period, location)**.

### Reserved fields

The following columns have special meaning to Chap:

**Required**

- `time_period` – temporal index (e.g. `YYYY-MM` for monthly, `YYYY-Wnn` for weekly)
- `location` – spatial unit identifier (e.g. DHIS2 org unit UID)
- `disease_cases` – outcome variable used for training

**Reserved but optional**

- `population`

All other columns are interpreted by Chap as **covariates / features** (e.g. temperature, precipitation, vegetation indices).

See the [Chap csv data format documentation](https://chap.dhis2.org/chap-modeling-platform/external_models/data_formats) for a full description.

---

## Temporal continuity

Chap assumes a **global, rectangular spatiotemporal grid**:

- all locations share the same start and end time
- all expected periods within that window are present for all locations

For this reason, the datasets in this repository:

- use a **single global time window** per file
- include **all (location × time_period) combinations** within that window

If data are missing for a given location and period, the row is still present and the value is recorded as **empty / NaN**.

Missing values are **not** filled or imputed in this repository.

---

## Interpreting missing values (NaNs)

Empty fields indicate that no observation was available for that location and time period in the source data.

How missing values are handled (e.g. imputation, masking, row removal) is a **modeling decision** and is intentionally left to downstream users and tools (including Chap).

---

## Scope and intent

- This repository publishes **final, model-ready data artifacts**
- It does not document upstream ingestion or harmonization pipelines
- It does not prescribe modeling or imputation strategies

The intent is to make temporal coverage explicit and transparent, so that any gaps are clearly visible and can be handled deliberately downstream rather than being hidden by implicit assumptions.
