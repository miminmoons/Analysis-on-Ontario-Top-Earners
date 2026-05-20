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
### **The 4x Dominance of Benefits over Salary**
Variable importance tracking yielded an extraordinary structural finding: Taxable employee benefits account for 79.78% of the classification model’s predictive power, while base salary accounts for just 20.22%. This reveals that benefit-based perks are nearly four times more predictive of a public sector worker's exact industry than the baseline amount on their check.
