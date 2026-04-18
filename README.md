# A/B Testing Notebooks

This repository contains two notebook-based analyses:

- `AB_Testing_Website_Conversion_Simulation.ipynb`: an A/B test of website background color and conversion.
- `Medicaid_DinD_testing.ipynb`: a Difference-in-Differences analysis of Medicaid expansion and insurance coverage.

Both notebooks use simulated or synthetic data and are intended for statistical analysis practice, not production decision-making.

## Repository Contents

| File | Description |
| --- | --- |
| `AB_Testing_Website_Conversion_Simulation.ipynb` | A/B testing workflow for website conversion analysis |
| `ab_testing.csv` | User-level A/B testing dataset |
| `NJ-PA_DinD_testing.ipynb` | Difference-in-Differences workflow for Medicaid expansion analysis |
| `synthetic_medicaid_did_micro_v1.csv` | Individual-level synthetic Medicaid expansion dataset used by the DiD notebook |
| `synthetic_medicaid_did_dataset_v2.csv` | Additional synthetic Medicaid expansion dataset included in the repo |

## Notebook 1: Website A/B Testing

### Objective

Evaluate whether website background color affects user conversion rates between a control variant and a treatment variant.

### Dataset

The notebook uses `ab_testing.csv`, with user-level experiment data:

- `User ID`: unique user identifier
- `Group`: control or treatment assignment
- `Page Views`: pages viewed during the session
- `Time Spent`: session duration in seconds
- `Conversion`: whether the user converted
- `Device`: access device type
- `Location`: user location

### Methods

- Data loading and basic cleaning
- Null checks and unique user assignment checks
- Sample Ratio Mismatch check using chi-square goodness-of-fit
- Device and location balance checks
- Two-proportion z-test for conversion rate difference
- Absolute lift, relative lift, and confidence interval calculation
- Guardrail metric review for time spent and page views

### Main Takeaway

The notebook finds a statistically significant conversion difference between variants, with the treatment group outperforming the control group while guardrail engagement metrics remain stable.

## Notebook 2: Medicaid Expansion DiD Analysis

### Objective

Estimate whether Medicaid expansion increased insurance coverage in expansion states relative to non-expansion states.

### Dataset

The notebook uses `synthetic_medicaid_did_micro_v1.csv`, with individual-level state-year observations:

- `state`: U.S. state identifier
- `year`: observation year
- `expanded_state`: indicator for states that eventually expanded Medicaid
- `expansion_year`: expansion year, or `Never` for non-expansion states
- `post`: indicator for observations at or after expansion
- `age`: individual age
- `female`: gender indicator
- `low_income`: low-income indicator
- `insured`: insurance coverage indicator

### Methods

- Data quality checks for expansion-year assignment and treatment coding
- Exploratory summaries of adoption timing and coverage rates
- Difference-in-Differences interaction term creation
- Baseline DiD regression
- State and year fixed effects regression
- Adjusted fixed effects regression with individual covariates
- Coverage trend visualization
- Low-income subgroup analysis

### Main Takeaway

The fixed-effects DiD estimate is positive, suggesting Medicaid expansion is associated with higher insurance coverage in this synthetic dataset. The low-income subgroup estimate is larger but less precisely estimated.

## Requirements

The notebooks use Python 3 and the following packages:

- pandas
- numpy
- matplotlib
- seaborn
- scipy
- statsmodels

Install dependencies with:

```bash
pip install pandas numpy matplotlib seaborn scipy statsmodels
```

If you want to run the notebooks interactively, also install Jupyter:

```bash
pip install notebook ipykernel
```

## How to Run

1. Open the repository folder.
2. Confirm the CSV files are in the same directory as the notebooks.
3. Start Jupyter:

```bash
jupyter notebook
```

4. Open either notebook and run cells from top to bottom.

## Notes

- The datasets appear to be simulated or synthetic, so results should be interpreted as examples of analytical workflows.
- The A/B testing notebook focuses on experiment validation and conversion lift.
- The Medicaid notebook focuses on causal inference using a Difference-in-Differences design.
- Outputs may differ if the notebooks are rerun after package upgrades or local display settings change.
