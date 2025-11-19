# Project Title

## 1. Research Question

What are you investigating, and why does it matter?

Do days with high discounts (promotion days) result in significantly higher net sales? This matters because it provides a direct, data-driven answer to whether the store's promotion strategy is effectively increasing revenue or just cutting profit margins for no benefit.

## 2. Hypothesis

State your null and alternative hypotheses clearly and succinctly.

Null Hypothesis: The true mean net sales on Promo Days is the same as or less than the mean Net sales on Regular Days.

Alternative Hypothesis: The true mean Net sales on Promo Days is greater than the mean Net sales on Regular Days.


## 3. Data Description

Describe your data source(s):

* Where it comes from (URL, API, dataset name) : : This is private data from a single liquor store in Minnesota, provided by the business owner. The data was pulled from the Clover web browser, exporting daily sales totals from March 2024 to October 2025.

* What each observation represents (unit of analysis): Each row in the file represents a single day of sales.

* Number of observations and key variables: There are 610 observations (rows). The key variables for this analysis are Gross sales (float), Discounts (float), and Net sales (float).

* Any filtering, cleaning, or transformation steps: 

The data was in a column format from its raw export into various month files. I had created a new excel file called LiquorStoreDataCleaned.xlsx in which I had transposed the data into row format and calculated discount rate, made a weekday column, remove any commas, and then move that file into a csv.

A discount_rate column was made using the formula (Discounts / Gross sales).

A categorical is_promo_day column (True/False) was made based on a discount_rate threshold (any day with a discount_rate above the 75th percentile).


## 4. Methods

Summarize how you analyzed the data:

* The test statistic for your permutation test: 

The test statistic will be the difference in mean Net sales between the two groups (Promo Days vs Regular Days).

* How you simulated or resampled under the null hypothesis: 

I will perform a permutation test by combining the Net sales data from both groups, shuffling the combined list, re-dealing them back into two new groups of the original sizes, and calculating the new difference in means. This will be repeated 10,000+ times to build a distribution of test statistics under the null hypothesis.

* The metric(s) for which you created bootstrap confidence intervals:

I will create a 95% bootstrap confidence interval for the median Net sales on Promo Days.

* Why the CLT does not apply to at least one metric:

(CLT) applies to statistics like sums and means, but it does not apply to the median. Therefore, I cannot use a standard formula to find the confidence interval for the median. Bootstrapping is the correct method to generate this interval.

## 5. Results

Present your main findings:

* Key summary statistics and visualizations

The threshold for defining a Promo Day (top 25% discount rate) was 0.0109 (1.09%) (discount of total sales). 
The sample was split into 457 Regular Days and 153 Promo Days.
The initial boxplot visually suggested Promo Days had higher sales, but this was later proven to be due to the Day of Week confounding variable.
Final analysis showed a moderate negative correlation (r = -0.303) between the size of the discount and the daily Net Sales.


* Observed test statistic and p-value (if applicable)

Observed Difference (Promo Mean - Regular Mean): (- $838.34)
P-value (Stratified Permutation Test): (0.8398)
Conclusion: Since p > 0.05, we fail to reject the Null Hypothesis. The promotions did not cause a statistically significant increase in sales, even after controlling for the Day of Week.


* Bootstrap confidence intervals for relevant metrics

•  Original Median Net Sales (Promo Days): ($2,498.13)
•  95% Confidence Interval for Median: ($2,450.33, $2,551.67)



## 6. Uncertainty Estimation

Discuss your resampling results:

* How many resamples you used: 

We used 10,000 repetitions for both the Stratified Permutation Test and the Bootstrapping Confidence Interval.

* What the bootstrap or randomization distributions looked like:

The randomization distribution (for the permutation test) was centered near zero, showing that the observed difference of $ - 838.34 fell well within the range of outcomes that would be expected purely by random chance.

The bootstrap distribution (for the median CI) was tightly clustered around the observed median of $2,498.13, indicating low variance and high stability in the estimate.

* How you interpret the interval estimates: 

We are 95% confident that the true median Net Sales on a Promo Day lies between $2,450.33 and $2,551.67. This provides the business with a narrow, reliable range for forecasting sales and managing inventory on any day they run a promotion.



## 7. Limitations

Briefly note any limitations in data, assumptions, or methods, including sources of bias or missing data.

Confounding Variables: While I controlled for the Day of Week using a stratified test (as recommended), I did not account for other factors that strongly influence liquor sales, such as holidays, weather events, or seasonality.

Generalizability: The data is from a single store in Blaine, MN. The results cannot be generalized to other stores or regions, as pricing and local competition will differ.

Missing Data: The dataset was missing Cost of Goods Sold (COGS) which were not available. This prevents us from measuring the direct impact on Net Profit.



## 8. References
List all datasets, tools, libraries, or papers you cited.

Dataset: Private daily sales data from a single Minnesota liquor store (March 2024 - October 2025) using Clover POS.

Tools & Libraries: Python, Pandas, NumPy, Matplotlib (for visualization), and Jupyter Notebook.


---

**Reminder:** Your README should be clear enough that someone unfamiliar with your work could understand what you studied, how you analyzed it, and what you found.
