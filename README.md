## ConnectaTel Mobile Usage Analysis | TripleTen Bootcamp (2026)

This project simulates the role of a data analyst at ConnectaTel, a telecommunications company operating in Mexico and Colombia. The objective was to understand how customers actually use mobile services — calls and text messages — in order to identify usage patterns, detect anomalous behavior, and understand which customer segments show differentiated needs. By integrating and cleaning three datasets covering plans, customer demographics, and real usage records, the analysis sought to build a clear, reliable, and actionable view of customer behavior to support commercial offer optimization and improve customer experience.

**Technologies & Skills:**
Python, Jupyter Notebook, pandas, matplotlib, seaborn, NumPy.

**Key questions:**
* Which customer segments show higher or lower usage of calls and text messages?
* Which users present outlier values that could indicate unusual behavior, fraud, or registration errors?
* How does usage vary by age and plan type?
* What patterns can help design better plans, optimize the commercial offer, and improve customer satisfaction?

## Methodology

* **Data Loading & Exploration:** Loaded and explored the three datasets (`plans`, `users_latam`, `usage`) to establish a clear view of each dataset's structure and column types.
* **Data Quality Assessment:** Counted null values, detected sentinel values, and reviewed dates outside valid ranges to build a prioritized list of issues that could bias downstream decisions.
* **Data Cleaning:** Replaced sentinel values, converted date fields, and imputed or flagged missing values according to defined rules to produce consistent, analysis-ready data.
* **Summary Statistics:** Reviewed key measures (mean, median, percentiles) across categorical and numerical variables to characterize typical and extreme behavior.
* **Exploratory Data Analysis (EDA):** Leveraged statistical visualization techniques to assess distributions and detect anomalies:
   * **Histograms:** Used to visualize the distribution of usage variables.
   * **Boxplots:** Used to identify significant outliers in call duration and message length.
* **Segmentation:** Built rule-based customer segments by age and usage level, visualizing group proportions with countplots to surface actionable groupings.
* **Executive Insights:** Translated the analysis into conclusions and commercial recommendations addressing the core business questions.

## Conclusions and Recommendations

### Key Findings

**Data Quality**
* The `city` column in the `users` dataset had a meaningful (11%) null rate, prompting a review of whether to impute or leave these as missing. The `churn_date` column had a much higher null rate (88%), which on review reflected the normal nature of the data (most customers are still active) rather than a data quality issue.
* In the `usage` dataset, the `date` column had negligible nulls (<1%), while `duration` and `length` each had nulls in nearly half of their records — a more delicate case, since these columns are essential to answering the core business questions. Further investigation is recommended to determine whether these nulls stem from registration errors or another underlying cause.
* The `id` and `user_id` columns showed no sentinel values, and neither did `duration` or `length`, beyond the nulls noted above.
* The `city` column contained 7 unique cities, with Bogotá as the most frequent, but also revealed a sentinel value ("?").
* In the `users` dataset, the `age` and `city` columns contained sentinel values ("-999" and "?" respectively), affecting roughly 1% and 2% of records — small enough to consider replacing with nulls or the median after further review.
* One case of impossible dates (year 2026) was found in `users` (~1%), which can reasonably be imputed as null without losing other customer data. In `usage`, date conversion revealed 50 nulls (~0.01%) — a small share, but worth investigating given the dataset's overall high null rate elsewhere.
* The `plan` column showed the basic plan as the most commonly acquired, though it does not exceed 50% by a wide margin — premium plan customers remain a significant group.
* The `type` column showed that customers use text messages more frequently than calls.

**Segments by Age**
* Adults (30–60 years old) represent the largest concentration of customers, followed by older adults, confirming that customers over 30 are ConnectaTel's core audience.
* Younger customers (under 30) are the smallest group, though not dramatically smaller than the others — still a meaningful target audience for the company.
* No outliers were observed in this segment.

**Segments by Usage Level**
* Medium usage is the predominant group by a clear margin compared to the other two levels, showing that most customers neither churn nor use the service excessively — they sit in a stable, moderate range.
* Low-usage customers are relatively scarce, while high-usage customers, though fewer in number, show considerable outliers — a subset of them use the service far beyond typical levels.

➡️ Together, these findings point to a core target audience of adults over 30 with medium usage, alongside a smaller but notable high-usage segment with considerable outliers worth addressing separately.

### Strategic Recommendations

* **Tailored Plans for Low- and High-Usage Segments:** Introduce new plans for infrequent and heavy users, with reduced or increased pricing respectively and benefits suited to each group. Lower-cost, limited plans could attract prospective customers who currently avoid subscribing because they don't expect to use a full plan. For high-usage outliers, dedicated plans with loyalty benefits or additional features could better capture and retain this valuable segment.
* **Age-Targeted Engagement:** For younger customers, invest in targeted marketing and benefits to understand why they aren't choosing ConnectaTel's plans and to grow adoption in this segment. For adults, who already represent a solid base, focus on loyalty-building campaigns and long-term benefits to strengthen retention.
