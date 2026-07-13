**GitHub repository**: https://github.com/bennettoxford/op-seasonality

# 1. Project Team/Authors

- **Abdulrasheed, Nasir**: Conceptualisation, formal analysis, methodology, software, validation, visualisation.
- **Andrews, Colm**: Conceptualisation, supervision, project administration, methodology, software, validation.
- **Ojedele, Lola**: Project administration, supervision, software, validation

# 2. Background

**Research question**: *How well does FFT-based seasonality autodetection perform compared to ARIMA models on the monthly practice-level English Prescribing Data (EPD) from March 2016 to April 2026?*

Autodetecting seasonality in prescription patterns of drugs is a useful, albeit difficult-to-implement, capability. The difficulty stems from the complexity of time-series data, with the best method being different depending on the data. This implementation will use a Fast Fourier Transform (FFT)-based method and build on the work in source 1 below. While FFT-based and hybrid FFT/ARIMA methods for time series analysis have been developed and applied elsewhere, they have yet to be applied to the EPD and automated in this manner.

This project will help provide an automated process and tool to detect seasonality patterns in primary care medication prescribing in England.

## 3. Objectives
### 3.1. Primary Objectives
- To build a Quarto notebook that takes monthly prescribing time-series data and detects seasonality in the prescribing of any of the drugs in the data (if any) using an FFT-based approach.
- To compare the performance of the approach above with more traditional modelling methods, such as ARIMA, on the same dataset using drugs with established prescribing seasonality, such as antidepressants for seasonal affective disorder (SAD).
- To test the tool with the prescribing data for a set of medications with suspected seasonal variation.

### 3.2. Secondary Objectives
- To test the tool with the prescribing data for a set of medications with suspected seasonal variations.
- To decompose and investigate the region-level and/or ICB-level differences in the seasonal pattern of the drugs in the examined data.


# 4. Methods

## 4.1. Study Design
This study is a retrospective time-series analysis of monthly practice-level prescribing data in English primary care. Antidepressants have been established to elicit a circannual variation in prescribing from previous studies. This study will use data on antidepressants from May 2016 to April 2026 (? exclude COVID-19 period) to develop the initial FFT-based tool.

## 4.2. Data Sources
### 4.2.1. OpenPrescribing
The OpenPrescribing database imports openly accessible prescribing data from the large monthly files published by the NHSBSA, which contain data on cost and items prescribed for each month, for every typical GP in England since mid-2010. These data are sourced from community pharmacy claims data and, therefore, contain all items that were dispensed. This data is not linked to patient-level data so does not allow for identification of sub-populations of interest.

## 4.3. Study Population
We will extract all available prescribing data, limited to institutions with setting code 4 - general practices, according to the NHS Digital dataset of practice characteristics.5 This excludes all other organisations such as prisons and out-of-hours services as they are not represented fully or consistently in the OpenPrescribing dataset since many of these prescriptions would not be dispensed in community pharmacies.

## 4.4. Drug Definition
The group of drugs used in this study are grouped under the following codelists:
- Antidepressants:  https://www.opencodelists.org/codelist/bristol/antidepressants-bnf/7a3cf198/ 

## 4.5. Study Measures
We will use GP data from OpenPrescribing to extract monthly data for the following measures:
1. Total monthly quantity of the drugs under consideration
2.  

### 4.5.1. Covariates
The above described measures will be stratified by the following:
- NHS regions

### 4.5.2. Sensitivity Analyses

## 4.6. Statistical Analysis
The project starts with replicating the initial FFT-based Python pipeline in R and Quarto using the `tidyverts` package ecosystem and the `fftw` package. The pipeline will incorporate:
1. Time series plots: time plots, seasonal plots, and subseries plots
2. Frequency-domain plots to visualise the spectrum and detect seasonality and period.
3. Test the pipeline and compare it with the ARIMA model by:
    - Generate synthetic data with various seasonal periods from the fitted ARIMA model and use that to test the pipeline. 
    - Compare the model to the pipeline in two ways:
    - Testing the presence/absence of seasonality as a binary classification task using precision/recall/F1/FPR from the synthetic data.
    - Test the accuracy of seasonal period estimation using an error measure like MAE/RMSE
4. Run the pipeline and the fitted ARIMA model on the antidepressant dataset and examine the results.
5. Test both on a dataset with suspected seasonality (yet to be determined)

### Limitation

# Results
### Table Shells / Mockup Figures

# References