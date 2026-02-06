# A/B Testing Analysis: Website Background Color Experiment

## Objective

Evaluate whether website background color (Control vs Treatment) affects user conversion rates using an A/B testing framework. Secondary checks include engagement guardrail metrics such as time spent and page views.

## Dataset Overview

The dataset contains simulated user-level experiment data with the following fields:

- User ID – Unique identifier for each user
- Group – Control (A) or Treatment (B)
- Page Views – Number of pages viewed during session
- Time Spent – Total session time (seconds)
- Conversion – Whether user converted (Yes/No)
- Device – Access device type
- Location – UK region of the user

Unit of randomization: User ID

## Methodology
- Experiment Validation

  - Sample Ratio Mismatch (SRM) check using chi-square goodness-of-fit
  - Device and location balance checks using chi-square independence tests
  - Verification of unique user assignment

- Primary Analysis
  - Conversion rate comparison between control and treatment
  - Two-proportion z-test (two-sided hypothesis)
  - Absolute and relative lift calculations
  - 95% confidence interval for difference in proportions

- Guardrail Metrics
  - Mean and median time spent
  - Average page views per user

These ensure improvements in conversion do not negatively impact engagement.

## Key Findings

- Conversion rates differ significantly between groups.

- Confidence interval excludes zero, indicating a statistically significant effect.

- Treatment group shows higher conversion performance.

- Engagement guardrails (time spent and page views per user) show no material degradation.

## Limitations

- Dataset appears simulated and may not reflect production noise.

- Short-term behavioral metrics only; no retention or long-term outcomes.

- No accessibility or usability subgroup analysis included.

## Requirements

Python packages used:

- panda
- numpy
- matplotlib
- seaborn
- scipy
- statsmodels


## Install via:
```
pip install pandas numpy matplotlib seaborn scipy statsmodels
```

## How to Run

- Place ab_testing.csv in the project directory.
- Run the notebook/script sequentially.
- Outputs include statistical tests, visualizations, and summary metrics.

## Conclusion

The experiment provides statistical evidence that background color influences conversion behavior in this dataset, with treatment outperforming control while maintaining stable engagement metrics.
