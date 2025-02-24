# World Values Survey Data Analysis

## Overview
This repository contains data and code for analyzing the World Values Survey (WVS) dataset. The project involves data cleaning, processing, and merging GDP data with survey responses.

## Repository Structure
```
📂 osf-vwvs/                   # Root directory
 ├── 📂 clean/                 # Processed datasets  
 │    ├── WVS_GDP_merged_data.csv    # Merged WVS data with GDP  
 │    ├── WVS_random_subset.csv      # Random subset of WVS data  
 │    ├── WVS_subset.csv             # Subset of WVS data  
 │  
 ├── 📂 documentation/          # Documentation and metadata  
 │    ├── codebook.pdf          # Variable definitions and coding instructions  
 │  
 ├── 📂 raw/                    # Raw data files  
 │    ├── WVS_Cross-National_Wave_7_csv_v6_0.csv  # Original WVS dataset  
 │  
 ├── 📂 code/                   # Scripts for data processing  
 │    ├── cleaning.R            # Script to clean and process WVS data  
 │  
 ├── README.md                  # Project description and instructions  
```

## Data Description
- **Source**: The WVS dataset is publicly available at [World Values Survey](https://www.worldvaluessurvey.org/).  
- **Processed Data**: The `clean/` folder contains merged and subsetted datasets used for analysis.  
- **Raw Data**: The `raw/` folder holds the original dataset in `.csv` format.  
- **Documentation**: The `codebook.pdf` explains variable definitions and survey methodology.

## Code and Reproducibility
- **Main script**: `code/cleaning.R` cleans and processes the raw WVS data.
- **Requirements**:
  - R (version X.X.X)
  - Required packages: `tidyverse`, `haven`
- **Running the code**:
  1. Place the raw data in the `raw/` folder.
  2. Run `cleaning.R` to generate the processed datasets.

## License and Citation
- This project follows the **MIT License**.
- If using this data or code, please cite the original WVS dataset.

## Contact
For questions or collaboration, contact: **[Your Name]** at **[Your Email]**.
