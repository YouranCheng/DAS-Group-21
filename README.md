# DAS-Group-21

This repository contains Group 21's analysis of the spam email dataset for Data Analysis Skills Group Project 2.

## Project Overview

The report studies which email text features are associated with spam classification. The analysis uses binomial logistic regression to examine how variables such as capital-letter runs, dollar signs, exclamation marks, and selected word frequencies relate to the probability that an email is spam.

## Repository Structure

- `Group-21.qmd`: Quarto source file for the analysis report.
- `Group-21.pdf`: rendered pdf output of the report.
- `dataset21.csv`: dataset used in the analysis.
- `README.md`: project summary and reproduction guide.

## Main Methods

- Data cleaning and validation in R
- Exploratory data analysis with `ggplot2`
- Logistic regression with `glm(..., family = binomial)`
- Model assessment with confusion matrices and ROC/AUC

## How to Reproduce

1. Clone the repository.
2. Open the project folder in RStudio or a terminal.
3. Make sure the required R packages are installed:
   - `tidyverse`
   - `broom`
   - `caret`
   - `pROC`
   - `knitr`
4. Render the report from the repository root:

```bash
quarto render Group-21.qmd
```

If you do not have Quarto installed, you can still run the code chunks in `Group-21.qmd` inside RStudio after setting the working directory to the repository folder.

## Current Output

The current report fits a full logistic regression model and a reduced model, compares their performance, and concludes that `log_crl_tot`, `dollar`, `bang`, `money`, and `n000` are useful indicators of spam, while `make` is not statistically significant in the full model.

## Notes

- The report now reads `dataset21.csv` more robustly when rendered from the project directory.
- Deprecated `ggplot2::aes_string()` usage has been removed to avoid rendering issues in newer package versions.
