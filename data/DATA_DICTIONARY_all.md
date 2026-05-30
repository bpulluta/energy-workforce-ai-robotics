# Data Dictionary — `hydropower_rai_matches_full.csv`

## Overview

The full, annotated match table behind the hydropower RAI workforce analysis. Each row is a single **match between an O\*NET occupational task and a Robotics-and-AI (RAI) technology**, enriched with the technology's development phase, application grouping, performer/supporter roles, the RAI exposure level (0–9 scale), and supporting literature.

This file is the source of truth for task-, technology-, and role-level analyses.

- **Rows:** 3,151
- **Unit of observation:** task × RAI-technology match
- **Source occupations:** O\*NET-SOC, mapped from hydropower O&M job titles
- **RAI taxonomy:** internal RAI technology library derived from structured literature review, structured by family (AI / Digital Twins / IoT / Robotics), `Application_Grouping`, and `RAI_Type`

## Columns

### Identifiers

| Column | Type | Description | Domain / example |
|---|---|---|---|
| `Task ID` | string | Internal identifier for the task statement | e.g., "M99" | (Codes starts with M are added manually based on hydropower occupation map, otherwise derived from O*NET task database)
| `Task` | string | Task statement text | full task text |
| `ONET code` | string | O\*NET-SOC code for the matched occupation | e.g., "47-2111.00" |
| `Unique Code` | string | RAI technology identifier; **first digit encodes the technology family** (see Code Schemes) | e.g., "120.2.022" |

### Hydropower application

| Column | Type | Description | Domain / example |
|---|---|---|---|
| `Hydropower Application` | string | How the task applies in a hydropower O&M context (lowercase column from upstream export) | free text |
| `Hydropower_Application_Code` | int | Numeric code for the specific hydropower application | e.g., 22, 27, 90 |
| `Application_Grouping` | categorical | High-level hydropower application area (**4 values total**) | `Equipment Fault Diagnosis and Predictive Maintenance` (1,386); `Intelligent Security and Condition Monitoring` (1,299); `Energy Management and Market-Oriented Optimization` (272); `Hydrological Forecasting and Water-Resource Scheduling` (194) |
| `Application_Grouping_Code` | int | Numeric code for `Application_Grouping` | 1–4 |

### RAI technology

| Column | Type | Description | Domain / example |
|---|---|---|---|
| `RAI_Type` | categorical | Granular technology type (**19 values**) | top values: `Machine Learning (ML)`, `Artificial Neural Network (ANN)`, `Artificial Intelligence (AI)`, `Digital Twins`, `Internet of Things (IoT)`, `ROV`, `Deep Learning`, `Robotics - ROV`, `LLM`, `Unmanned Aerial Vehicles` |
| `RAI_Code` | int | Numeric code for the RAI technology family; **identical to the first digit of `Unique Code`** | 1 (AI), 2 (Digital Twins), 3 (IoT), 4 (Robotics) |
| `RAI Technology Detail` | string | Free-text description of the matched technology | e.g., "ML-based condition monitoring, fault diagnosis, and prognostics/predictive maintenance" |

### Performer / Supporter (based on Coactive Design Framework)

| Column | Type | Description | Domain / example |
|---|---|---|---|
| `Primary Performer` | categorical | Who primarily performs the task | `RAI` (2,031), `Human` (1,120) |
| `Performer capability` | categorical | Full capability annotation for the primary performer | `G`, `O`, `O/Y`, `Y`, `G/Y`, `G/Y/O` |
| `PR` | categorical | Simplified single-letter capability code for the primary performer | `G`, `O`, `Y` |
| `Supporter` | categorical | Who supports the primary performer | `Human` (2,031), `RAI` (1,120) |
| `Supporter role` | string | Capability code + descriptive text for the supporter's contribution | e.g., "G (efficiency and consistency)" |
| `SR` | categorical | Simplified single-letter capability code for the supporter | `G`, `O`, `Y`, `R` |

> Note: `Primary Performer` and `Supporter` are always paired one-of-each (RAI/Human or Human/RAI), reflecting the assumption that every match involves both parties in defined roles.

### RAI exposure level

| Column | Type | Description | Domain |
|---|---|---|---|
| `Automation` | float | **Granular RAI exposure level (0–9 scale)** See Table 1 for definition

### Supporting literature (provenance)

| Column | Type | Description | Nulls |
|---|---|---|---|
| `Requirement` | string | Technical or operational requirements reported by the source | 400 / 3,151 |
| `Performance` | string | Performance results reported by the source | 479 / 3,151 |
| `Limitations` | string | Limitations or open issues reported by the source | 444 / 3,151 |
| `Citation` | string | Bibliographic citation(s); may contain multiple references concatenated with `\r\n` | 371 / 3,151 |
| `Publication Year` | float | Year of source publication | 467 / 3,151 |

### Occupation mapping

| Column | Type | Description | Example |
|---|---|---|---|
| `Input Job Title` | string | Hydropower O&M job title used as input for occupation matching | e.g., "Electrician" |
| `ONET Title` | string | O\*NET occupation title | e.g., "Electricians" |
| `Additional Occupation Titles` | string | Other occupation titles to which this task also applies | e.g., "Electrician" |
