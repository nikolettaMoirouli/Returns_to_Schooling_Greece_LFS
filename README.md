# Economic Analysis of Labor Market Outcomes & Wage Inequality (2003–2025)

This repository contains the Python-based data processing and econometric analysis pipeline for my thesis. The project replicates and modernizes a Stata workflow into Python, leveraging 23 years of pooled cross-sectional microdata from the Hellenic Statistical Authority's (ELSTAT) Labour Force Survey (LFS) to examine the heterogeneous relationship between educational attainment, academic field of study, and gender in the Greek labor market.

## Project Overview
* **Objective:** To investigate whether tertiary education universally correlates with economic stability, or whether returns to schooling are heterogeneous across specific academic disciplines and gender.
* **Data:** Pooled cross-sectional dataset combining quarterly (2003–2020) and annual (2021–2025) Greek LFS survey data (focusing on prime-age individuals after formal schooling and prior to retirement, aged 25–54). *Note: Raw microdata are excluded from this repository due to data confidentiality.*
* **Methodological Framework:** All wage and inequality metrics are strictly derived from **real monthly earnings** (deflated via CPI, base year 2020 = 100). To construct a consistent continuous wage series (`salary_cont`) across the full 2003-2025 period, categorical wage brackets reported in the 2003–2014 survey waves were mapped to their respective bracket midpoints, whereas for 2015–2025 the reported continuous earnings variable was used directly without transformation.

## Pipeline Structure (`Returns_to_Schooling_Analysis.ipynb`)
1. **Data Harmonization & Cleaning:** Sample selection, CPI deflation, and generation of labor market outcome variables (`inlf`, `empl`, `unem`, `hours`, `fulltime`, `wageearner`, `lwr`, `ineq20D`, `ineq80D`).
2. **Summary Statistics:** Weighted frequency tables by gender (covering educational fields, age, economic activity, working hours, and NUTS2 regions) alongside `tabstat` wage and labor market distributions.
3. **Automated Visualizations:** Time-series trend charts mapping population-weighted educational attainment and labor market trajectories by gender from 2003 to 2025.
4. **Econometric Modeling:** 24 survey-weighted Ordinary Least Squares (OLS) regressions with robust standard errors to estimate Mincerian wage equations, wage inequality models, and labor market outcome models across Pooled, Male, and Female samples.

## Key Empirical Findings & Stylized Facts
* **Educational Upgrading & Occupational Sorting:** Between 2003 and 2025, the Greek labor force experienced a substantial decline in low-skilled attainment alongside a rapid expansion in higher education, with women overtaking men in tertiary attainment. However, notable horizontal segregation persists: female graduates remain heavily concentrated in humanistic, education, and care fields, whereas male graduates predominate in engineering and technical disciplines.
* **Labor Market Attachment & Female Catch-Up:** Across the pooled sample, women face substantial baseline disadvantages in labor force participation, employment probability, and unconditional weekly hours worked, where non-workers are coded as `0`. However, tertiary education acts as a strong positive predictor of labor market attachment for women, correlating with large employment probability gains relative to upper secondary graduates.
* **Heterogeneous Wage Associations & Gender Penalties:** Mincerian log-wage regressions indicate that specialized, quantitative, and professional fields (such as Health, Engineering, Social Sciences/Law, Services, and Education) are associated with substantial real earnings premiums over upper secondary education. While women experience a persistent conditional wage penalty of approximately 16.5% (-0.180 log points) in the pooled specification, women achieve higher *relative* wage premiums from tertiary degrees than men across almost all fields of study.
* **Tail Inequality & Educational Mismatch (Bottom 20% vs. Top 20%):** 
   *Bottom 20% :* Holding a university degree generally correlates with a lower likelihood of falling into the bottom quintile of the real earnings distribution. A notable exception emerges for male Arts & Humanities graduates, who exhibit virtually no protection against low earnings relative to high school graduates—a pattern consistent with occupational mismatch.
   *Top 20% :* Technical, quantitative, and professional degrees are strongly associated with reaching the top quintile of earners, led by Health and Social Sciences/Law among men, and Engineering and Social Sciences/Law among women.
* **General Conclusion & Econometric Caveat:** Because the LFS dataset consists of repeated cross-sections rather than a longitudinal panel tracking unobserved individual ability or self-selection into majors, all estimated coefficients represent conditional associations rather than causal effects. Overall, the findings indicate that returns to schooling in Greece are not uniform: they are highly heterogeneous and depend strongly on both field of study and gender. While higher education serves as an important mechanism for women to overcome baseline participation barriers, educational expansion alone does not eliminate gender disparities in the labor market.

## Technologies Used
* `pandas`, `numpy`: Data cleaning, harmonization, survey-weighted aggregation, and variable transformation
* `matplotlib`: Automated time-series data visualization
* `statsmodels`: Econometric modeling and survey-weighted OLS estimation

