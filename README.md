Data Science Final Project
Climate & Temperature Analysis (1850–2020)
Author: Abdulsamad Sulyman 
________________


Overview
This project explores long-term climate and temperature change trends using multiple large historical datasets. The workflow covers dataset ingestion, cleaning, integration, feature development, and forecasting. Each notebook in this repository represents a specific stage in the pipeline, allowing the analysis to be run in sequence from raw data to final predictive modeling and visualization. The goal is to build a reproducible pipeline that transforms raw climate records into usable model-ready data and produces insight into temporal temperature patterns.
________________


Repository Contents and Purpose
(Execute notebooks in order for full pipeline functionality)
1. Notebook1_Setup_Cleaning.ipynb

   * Establish file directory paths for imports (mandatory to edit before running)
   * Load raw climate datasets and print shapes for verification
   * Perform cleaning operations (removing invalid entries, handling missing values, dropping unwanted columns)
   * Standardize dataset naming formats and date fields
   * Export cleaned versions for downstream notebooks

      2. Notebook2_FeatureEngineering.ipynb

         * Import cleaned data and merge on city/country/time when applicable
         * Create engineered features for modeling (ex: temperature deltas, rolling means, uncertainty handling)
         * Generate comparison tables and filtered subsets for analysis
         * Prepare modeling dataframe and save outputs for forecasting
         3. Notebook3_Modeling_Forecasting.ipynb

            * Build predictive temperature models using cleaned + engineered data
Train, test, evaluate, and visualize model performance over time
            * Produce forecast output graphs and statistical summaries
            * Interpret trend behavior across regions/cities and generate final results
________________


Important Path Note (Read Before Running)
Data access directories differ across machines. Developers must update the dataset file paths inside Notebook1 before execution. If the program cannot locate files, update the directory variables in the first code cell to match your system’s folder structure. Once corrected, downstream notebooks will run normally because they load files created during Notebook1 and Notebook2.
________________
System and Software Requirements
Python Version: 3.9+
Recommended Environment: Jupyter Notebook or Jupyter Lab
Required Python Libraries:
pandas, numpy, matplotlib, seaborn, tqdm, glob, os, sys
(Install missing packages with pip)
________________
Execution Order
               1. Open Notebook1_Setup_Cleaning and run cells top-to-bottom after correcting file paths.
               2. Proceed to Notebook2_FeatureEngineering once cleaned data is generated.
               3. Finish in Notebook3_Modeling_Forecasting to build and evaluate forecasting models.
________________
Expected Outputs
                  * Cleaned climate datasets ready for analysis
                  * Engineered feature tables for modeling workflows
                  * Forecast plots showing long-term climate trends
                  * Summary results useful for reporting and discussion
