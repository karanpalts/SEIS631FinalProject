# Project Title

## 1. Research Question

What are you investigating, and why does it matter?

Do days with high discounts (i.e., "promotion days") result in significantly higher net sales? This matters because it provides a direct, data-driven answer to whether the store's promotion strategy is effectively increasing revenue or just cutting profit margins for no benefit.

## 2. Hypothesis

State your null and alternative hypotheses clearly and succinctly.

Null Hypothesis: The true mean net sales on "Promo Days" is the same as or less than the mean Net sales on "Regular Days."

Alternative Hypothesis: The true mean Net sales on "Promo Days" is greater than the mean Net sales on "Regular Days."


## 3. Data Description

Describe your data source(s):

* Where it comes from (URL, API, dataset name) : : This is private data from a single liquor store in Minnesota, provided by the business owner. The data was pulled from the Clover web browser, exporting daily sales totals from March 2024 to October 2025.

* What each observation represents (unit of analysis): Each row in the file represents a single day of sales.

* Number of observations and key variables: There are 610 observations (rows). The key variables for this analysis are Gross sales (float), Discounts (float), and Net sales (float).

* Any filtering, cleaning, or transformation steps: 

The data was in a column format from its raw export into various month files. I had created a new excel file called LiquorStoreDataCleaned.xlsx in which I had transposed the data into row format and calculated discount rate, made a weekday column, remove any commas, and other misc tasks. 

A discount_rate column was made using the formula (Discounts / Gross sales).

A categorical is_promo_day column (True/False) will be engineered based on a discount_rate threshold (e.g., any day with a discount_rate above the 75th percentile).


## 4. Methods

Summarize how you analyzed the data:

* The test statistic for your permutation test: 

The test statistic will be the difference in mean Net sales between the two groups ("Promo Days" and "Regular Days").

* How you simulated or resampled under the null hypothesis: 

I will perform a permutation test by combining the Net sales data from both groups, shuffling the combined list, re-dealing them back into two new groups of the original sizes, and calculating the new difference in means. This will be repeated 10,000+ times to build a distribution of test statistics under the null hypothesis.

* The metric(s) for which you created bootstrap confidence intervals:

I will create a 95% bootstrap confidence interval for the median Net sales on "Promo Days."

* Why the CLT does not apply to at least one metric:

(CLT) applies to statistics like sums and means, but it does not apply to the median. Therefore, I cannot use a standard formula to find the confidence interval for the median. Bootstrapping is the correct method to generate this interval.

## 5. Results

Present your main findings:

* Key summary statistics and visualizations
* Observed test statistic and p-value (if applicable)
* Bootstrap confidence intervals for relevant metrics

## 6. Uncertainty Estimation

Discuss your resampling results:

* How many resamples you used
* What the bootstrap or randomization distributions looked like
* How you interpret the interval estimates

## 7. Limitations

Briefly note any limitations in data, assumptions, or methods, including sources of bias or missing data.

## 8. References




List all datasets, tools, libraries, or papers you cited.

---

**Reminder:** Your README should be clear enough that someone unfamiliar with your work could understand what you studied, how you analyzed it, and what you found.
