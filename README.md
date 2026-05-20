# Analysis on Ontario Top Earners

## 🔗 Quick Links
* [Read the Full PDF Report](./ontario-compensation-report.pdf)
* [Explore the R-Markdown Code](./code/ontario-compensation-analysis.Rmd)
* [Access the Dataset](./dataset/README.md)

## Background and Overview
In a predominantly corporate-driven landscape, Ontario's public sector accounted for a substantial 19.4% of total provincial employment in 2020. Comprising critical infrastructure such as healthcare, education, and various governmental bodies, these workers serve as vital components of Ontario's urban centers and form the fundamental structural backbone of the province.

This project utilizes the 2020 public salary disclosure compendium (commonly known as the "Sunshine List") mandated under the Public Sector Salary Disclosure Act, 1996. The data covers historical compensation profiles for top-earning employees making $100,000 or more per annum.

## Project Objective
From an analytics and organizational management perspective, this project evaluates the baseline compensation design structures of public institutions by seeking to answer one specific question: "Can we accurately predict the job sector of a public employee given only their taxable employee benefits and base salary?"

## Data Structure Overview
The analysis was performed on a dataset consisting of $N = 171,365$ clean public sector observations. To ensure an optimized predictive performance with minimal distributional bias, the scope was narrowed down to the five largest employment sectors in the dataset:
| Sector Code | Public Department Industry |
| :--- | :--- |
| Mun | Municipalities and Services |
| Sch | School Boards |
| Hosp | Hospitals & Boards of Public Health |
| Uni | Universities |
| Minst | Government of Ontario Ministries |

### Core Variables
* Sector: The target categorical response classification variable.
* Salary: Continuous financial metric measuring the baseline annual earnings of each top earner.
* Benefits: Continuous financial metric tracking the taxable bonus additions provided by respective employers.

## Executive Summary
An initial comprehensive overview confirms that while base compensation packages across public sectors generally follow normal distributions, the real differentiation lies in the allocation behavior of non-salary perks and taxable benefits.

By training a tuned machine learning classification model on purely financial paycheck entries, the algorithm achieved a mean cross-validated accuracy rate of 64.88% across five distinct sectors, with a Cohen's Kappa statistic of 0.5331. This predictive capability significantly outstrips the baseline 20% random-chance threshold, mathematically demonstrating that distinct public industries maintain stark, systematic variances in how they reward upper-tier personnel.

## Insights Deep Dive
### 1. *4x Dominance of Benefits over Salary*
Variable importance tracking yielded an extraordinary structural finding: Taxable employee benefits account for 79.78% of the classification model’s predictive power, while base salary accounts for just 20.22%. This reveals that benefit-based perks are nearly four times more predictive of a public sector worker's exact industry than the baseline amount on their check.

### 2. *Divergent Allocation Profiles (Universities vs. Municipalities)*
Bootstrapped 95% confidence interval testing on 1,000 resamples isolated completely separate corporate compensation philosophies:
* Base-Pay Heavy (Universities): Holding the highest median salary spectrum in the province ($148,293; 95% CI: $147,467–$149,146), Universities heavily skew their compensation towards guaranteed base salary rather than floating additions.
* Benefit-Heavy (Municipalities): Conversely, Municipalities maintain mid-tier base salaries ($117,452) but hold the undisputed highest average employee benefit yields ($989; 95% CI: $976–$1,001).

### 3. *Statistical Validation of Pairwise Discrepancies*
Simultaneous evaluation using a One-Way ANOVA definitively rejected the null hypothesis that sector benefit averages are globally equal ($F(4,171365) = 2669$, $p < 2 \cdot 10^{-16}$). Post-hoc Tukey HSD testing confirmed that all 10 possible pairwise industry combinations are entirely statistically significant.

Even the minor historical difference between School Boards and Ministries (~$71 variance) represents a true structural market variance rather than a random noise signature.

## Libraries Used
* **Data Wrangling:** tidyverse, dplyr, stringr, readr, tidyr
* **Statistical Modeling & Machine Learning:** broom, boot, rpart, caret
* **Data Visualization & Formatting:** ggplot2, rpart.plot, rattle, knitr, kableExtra

## Project Context & Data Attribution
* **Development History:** This analysis originated as a final project for STAA57 course. The repository hosted here represents an expanded portfolio version featuring updated structural regression visualizations, optimized code refactoring, and enhanced documentation.
* **Data Source:** All primary analysis relies on the official 2020 public compendium collected and published by the Treasury Board Secretariat of Ontario under the Public Sector Salary Disclosure Act, 1996.
