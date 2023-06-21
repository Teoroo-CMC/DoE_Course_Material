# t-test and ANOVA

## t-test

The t-test is a statistical method used to determine if there is a significant difference between the means of two populations, or to test whether the mean of a single distribution is larger, smaller or equal to a claimed value. It is based on the t-distribution, which is similar to the normal distribution but with heavier tails.

The t-test is commonly used when you have a small sample size (typically less than 30) and want to compare the means of two independent groups. The test calculates a t-value, which measures the difference between the means relative to the variability within the groups.

### one-sample t-test

The one-sample t-test is a statistical method used to determine if the mean of a single sample significantly differs from a hypothesized population mean. It is commonly used when you have a sample and want to test if it is representative of the entire population.

The formula for the one-sample t-test is as follows:

$$
t = \frac{{\bar{X} - \mu}}{{\frac{{s}}{{\sqrt{n}}}}}
$$

Where:
- $\bar{X}\$ is the sample mean.
- $\mu$ is the hypothesized population mean.
- $s$ is the sample standard deviation.
- $n$ is the sample size.

To perform a one-sample t-test, you calculate the t-value using this formula and compare it to the critical value from the t-distribution with $n-1$ degrees of freedom. The critical value is determined based on the desired significance level $\alpha$ and the direction of the test (one-tailed or two-tailed).

If the calculated t-value is greater than the critical value (for a one-tailed test) or falls outside the critical region (for a two-tailed test), then there is evidence to suggest that the sample mean significantly differs from the hypothesized population mean.

Here's an example to illustrate the one-sample t-test:

Suppose we have a sample of 30 students, and we want to test if their average score significantly differs from a population mean of 75. We calculate the sample mean $\\bar{X}\$ and the sample standard deviation $s$ as follows:


$\bar{X}$ (sample mean) = 78.5
$s$ (sample standard deviation) = 4.2


Assuming a significance level of 0.05, we can calculate the t-value using the formula:

$$
t = \frac{{78.5 - 75}}{{\frac{{4.2}}{{\sqrt{30}}}}}
$$

Once we have the t-value, we can compare it to the critical value from the t-distribution with $n-1$ degrees of freedom. If the calculated t-value exceeds the critical value, we can conclude that the sample mean significantly differs from the hypothesized population mean.



### Independent two-sample t-test
The independent two-sample t-test is used when we like to determine if there is a significant difference between the means of two populations.

The formula for the independent two-sample t-test:

$$
t = \frac{{\bar{X}_1 - \bar{X}_2}}{{\sqrt{\frac{{s_1^2}}{{n_1}} + \frac{{s_2^2}}{{n_2}}}}}
$$

Where:
- $\bar{X}_1$ and $\bar{X}_2$ are the sample means of the two groups.
- $s_1$ and $s_2$ are the sample standard deviations of the two groups.
- $n_1$ and $n_2$ are the sample sizes of the two groups.

Once you have calculated the t-value, you can compare it to the critical value from the t-distribution with $n_1 + n_2 - 2$ degrees of freedom. The critical value helps you determine whether the difference between the means is statistically significant.

If the calculated t-value is greater than the critical value (usually at a chosen significance level, such as 0.05), then there is evidence to suggest that the means of the two groups are significantly different.

Example:

Suppose we want to investigate whether there is a significant difference in the average test scores between two groups of students: Group A and Group B. We have collected a sample of 20 students from each group and recorded their test scores.

Let's say we obtained the following data:

Group A: 75, 80, 85, 90, 92, 78, 81, 79, 88, 86, 83, 82, 87, 84, 91, 80, 83, 85, 89, 81
Group B: 70, 72, 76, 68, 74, 73, 78, 75, 77, 80, 72, 76, 79, 73, 75, 71, 77, 76, 74, 78

To determine if there is a significant difference between the means of the two groups, we can perform an independent t-test. 
The proceedure is as follows:

Step 1: Calculate the sample means and sample standard deviations for each group.

$\bar{X}_1$ (Group A mean) = 84.25

$\bar{X}_2$ (Group B mean) = 74.45

$s_1$ (Group A standard deviation)$ = 4.876

$s_2$ (Group B standard deviation)$ = 3.142

Step 2: Calculate the t-value using the formula:

$$
t = \frac{{\bar{X}_1 - \bar{X}_2}}{{\sqrt{\frac{{s_1^2}}{{n_1}} + \frac{{s_2^2}}{{n_2}}}}}
$$

$$
t = \frac{{84.25 - 74.45}}{{\sqrt{\frac{{4.876^2}}{{20}} + \frac{{3.142^2}}{{20}}}}}
$$

$$
t \approx 3.168
$$

Step 3: Determine the degrees of freedom. For an independent t-test, the degrees of freedom are $n_1 + n_2 - 2$, where $n_1$ and $n_2$ are the sample sizes of the two groups. In our example, the degrees of freedom would be $20 + 20 - 2 = 38$.

Step 4: Compare the calculated t-value with the critical value from the t-distribution. The critical value depends on the chosen significance level (often denoted as $\alpha$). Let's assume we chose a significance level of 0.05.

Using statistical software or a t-table, we can find that the critical t-value for a two-tailed test with 38 degrees of freedom at a 0.05 significance level is approximately 2.024.

Since our calculated t-value (3.168) is greater than the critical t-value (2.024), we can conclude that there is a significant difference between the average test scores of Group A and Group B.


### Dependent two-sample t-test
The dependent two-sample t-test, also known as the paired t-test, is a statistical method used to determine if there is a significant difference between the means of two related or dependent groups. It is commonly used when the same subjects are measured or tested under different conditions or at different time points.

The formula for the dependent two-sample t-test is as follows:

$$
t = \frac{{\bar{D} - \mu}}{{\frac{{s_D}}{{\sqrt{n}}}}}
$$

Where:
- $\bar{D}$ is the mean of the differences between paired observations.
- $\mu$ is the hypothesized population mean difference (usually 0 if there is no expected difference).
- $s_D$ is the standard deviation of the differences.
- $n$ is the number of pairs or observations.

To perform a dependent two-sample t-test, you calculate the t-value using this formula and compare it to the critical value from the t-distribution with $n-1$ degrees of freedom. The critical value is determined based on the desired significance level ($\alpha$) and the direction of the test (one-tailed or two-tailed).

If the calculated t-value is greater than the critical value (for a one-tailed test) or falls outside the critical region (for a two-tailed test), then there is evidence to suggest that there is a significant difference between the means of the dependent groups.

Here's an example to illustrate the dependent two-sample t-test:

Suppose we want to investigate if a new teaching method improves student scores. We have a sample of 20 students who were tested before and after the teaching method was implemented. The scores of each student are as follows:

Before: 75, 80, 85, 90, 92, 78, 81, 79, 88, 86, 83, 82, 87, 84, 91, 80, 83, 85, 89, 81
After: 80, 82, 86, 88, 90, 75, 79, 81, 82, 85, 84, 86, 87, 83, 90, 82, 84, 83, 88, 85

To perform the dependent two-sample t-test, we calculate the differences between the before and after scores for each student:

Difference (D): 5, 2, 1, -2, -2, -3, -2, 2, -6, -1, 1, 4, 0, -1, -1, 2, 1, -2, -1, 4

We then calculate the mean of the differences ($\bar{D}$) and the standard deviation of the differences ($s_D$):

$\bar{D}$ (mean of differences) = 0.2
$s_D$ (standard deviation of differences) = 2.7

Assuming a significance level of 0.05, we can calculate the t-value using the formula:

$$
t = \frac{{0.2 - 0}}{{\frac{{2.7}}{{\sqrt{20}}}}}
$$

Once we have the t-value, we can compare it to the critical value from the t-distribution with $n-1$ degrees of freedom. If the calculated t-value exceeds the critical value, we can conclude that there is a significant difference between the means of the dependent groups.

It's important to note that assumptions about the normality of the differences and the dependence of the paired observations should be met for accurate results when conducting a dependent two-sample t-test

### A note on the depenedent two-sample t-test
When the data of the two groups in a dependent t-test differ by a single constant, it means that there is a systematic shift or offset between the measurements of the two groups. In this case, the mean of the differences between the paired observations will be equal to that constant.

Let's denote the constant offset as $c$. If the data of Group A is denoted by $X$ and the data of Group B is denoted by $Y$, then the differences between the paired observations can be calculated as $D = X - Y$. In this scenario, $D$ will have a constant value for each pair, which is equal to $c$.

The mean of the differences ($\bar{D}$) will also be equal to $c$ because each difference is a constant. The standard deviation of the differences ($s_D$) will be 0 since there is no variability in the differences.

As a result, when performing the dependent t-test, the t-value can be calculated as:

$$
t = \frac{{\bar{D} - \mu}}{{\frac{{s_D}}{{\sqrt{n}}}}}
$$

Since $s_D$ is 0, the denominator becomes 0, resulting in an undefined t-value. This means that the t-test cannot be applied in this scenario.

In summary, when the data of the two groups differ by a single constant in a dependent t-test, the standard deviation of the differences becomes 0, making it impossible to calculate a valid t-value.

## ANalysis Of VAriance (ANOVA)

Certainly! ANOVA, or Analysis of Variance, is a statistical method used to analyze the differences between the means of three or more groups. It allows us to determine if there are significant differences among the group means, beyond what might be expected due to random variation.

The main idea behind ANOVA is to partition the total variability in the data into two components: the variability between the groups and the variability within the groups. If the between-group variability is significantly larger than the within-group variability, it suggests that there are differences in the means of the groups.

To assess the significance of the differences, ANOVA utilizes the F-test statistic. The F-test compares the ratio of the between-group variability to the within-group variability. If the ratio is large enough to exceed a critical value, it indicates that the group means are likely different.

Here's a step-by-step explanation of how ANOVA and the F-test work:

Step 1: Formulate hypotheses:
- Null hypothesis (H0): There are no significant differences among the group means.
- Alternative hypothesis (Ha): At least one group mean is significantly different from the others.

Step 2: Calculate the F-test statistic:
The F-test statistic is computed as the ratio of the mean square between-groups (MSB) to the mean square within-groups (MSW):

$$
F = \frac{{MSB}}{{MSW}}
$$

Step 3: Determine the degrees of freedom:
- Degrees of freedom between-groups (DFB): Number of groups minus 1.
- Degrees of freedom within-groups (DFW): Total number of observations minus the number of groups.

Step 4: Calculate the mean square between-groups (MSB):
MSB is obtained by dividing the sum of squares between-groups (SSB) by the degrees of freedom between-groups (DFB):

$$
MSB = \frac{{SSB}}{{DFB}}
$$

Step 5: Calculate the mean square within-groups (MSW):
MSW is obtained by dividing the sum of squares within-groups (SSW) by the degrees of freedom within-groups (DFW):

$$
MSW = \frac{{SSW}}{{DFW}}
$$

Step 6: Determine the critical value:
The critical value for the F-test depends on the chosen significance level ($\alpha$) and the degrees of freedom for the between-groups and within-groups.

Step 7: Compare the calculated F-test statistic with the critical value:
If the calculated F-test statistic is greater than the critical value, we reject the null hypothesis and conclude that there are significant differences among the group means. Otherwise, we fail to reject the null hypothesis.

### Pair-wise t-tests

A Pair-wise t-tests tests, are often conducted after performing an Analysis of Variance (ANOVA) to determine which specific group means are significantly different from each other. ANOVA can indicate the presence of significant differences among the groups, but it does not identify which specific group pairs are responsible for the differences. Pair-wise t-tests help address this issue by comparing the means of individual group pairs.

Here's how pair-wise t-tests are typically conducted after ANOVA:

Step 1: Perform ANOVA:
First, you conduct an ANOVA to determine if there are significant differences among the group means.

Step 2: Identify significant differences:
If the ANOVA results indicate a significant difference among the group means, you proceed to perform pair-wise t-tests to identify which specific group pairs are significantly different from each other. The pair-wise t-tests compare the means of each pair of groups to determine if their differences are statistically significant.

Step 3: Adjusting for multiple comparisons:
When conducting multiple pair-wise t-tests, there is an increased risk of making Type I errors (incorrectly concluding significant differences). To account for this, it is common to apply a correction method, such as the Bonferroni correction, to adjust the significance level for each individual t-test. This correction helps control the overall family-wise error rate.

Step 4: Conduct pair-wise t-tests:
For each pair of groups, you perform a separate t-test to compare their means. The t-test calculates the t-value by considering the means, standard deviations, and sample sizes of the two groups. The t-value is then compared to the critical value from the t-distribution with appropriate degrees of freedom.

Step 5: Interpret the results:
Based on the results of the pair-wise t-tests, you can identify which specific group pairs have statistically significant differences in means. The significance level used for the pair-wise t-tests will be adjusted based on the chosen correction method in Step 3.

Thus, by conducting pair-wise t-tests, you can gain a more detailed understanding of the specific group differences that contribute to the significant findings from the ANOVA. This helps to further elucidate the patterns and relationships within the data.

It's important to note that the choice of post hoc test may vary depending on the specific research question, study design, and assumptions underlying the data. There are several post hoc tests available, such as the Tukey's Honestly Significant Difference (HSD) test, Bonferroni test, Scheffé's test, and others. 

### Pair-wise t-tests with Bonferroni correction

The Bonferroni correction is a widely used method for adjusting the significance level in multiple hypothesis testing scenarios. It is particularly useful when conducting multiple pairwise comparisons or conducting multiple statistical tests simultaneously. The purpose of the Bonferroni correction is to control the family-wise error rate, which is the probability of making at least one Type I error among all the tests.

Pair-wise t-tests with Bonferroni correction:

Step 1: Determine the desired overall significance level:
Before conducting multiple tests, you need to determine the desired overall significance level, denoted as $\alpha$. This is typically set at 0.05 or 0.01, indicating a 5% or 1% chance of making a Type I error, respectively.

Step 2: Divide the significance level by the number of tests:
To adjust the significance level for each individual test, divide the desired overall significance level ($\alpha$) by the number of tests being performed. Let's say you are conducting $k$ tests, so the adjusted significance level $(\alpha'$) for each test is calculated as $\frac{\alpha}{k}$.

Step 3: Conduct individual tests:
Perform each of the individual tests or pairwise comparisons, comparing the test statistic (e.g., t-value, p-value) with the adjusted significance level ($\alpha'$) obtained in Step 2.

Step 4: Interpret the results:
If the p-value (or any other test statistic) is less than or equal to the adjusted significance level ($\alpha'$), you reject the null hypothesis for that particular test. Otherwise, you fail to reject the null hypothesis.

The Bonferroni correction is quite conservative since it divides the desired overall significance level by the number of tests. This adjustment helps maintain a more stringent threshold for declaring statistical significance, reducing the likelihood of Type I errors.

For example, if you are conducting 10 pairwise comparisons and want to maintain an overall significance level of 0.05, each individual comparison would be tested at a significance level of $\frac{0.05}{10} = 0.005$.

The Bonferroni correction is simple and widely applicable, but it assumes that the tests being conducted are independent or weakly dependent. It does not take into account any potential correlations or relationships between the tests.

### Tukey's test

Tukey's Honestly Significant Difference (HSD) test is a commonly used post hoc test following an Analysis of Variance (ANOVA). It helps identify which specific group pairs have statistically significant differences in their means. Tukey's test is particularly useful when comparing all possible pairs of group means and controlling for the family-wise error rate.

The algortihm:

Step 1: Perform ANOVA:
First, you conduct an ANOVA to determine if there are significant differences among the group means. 

Step 2: Calculate the Tukey's HSD value:
Tukey's HSD value is calculated using the formula:

$$
HSD = q \times \sqrt{\frac{{MSW}}{{n}}}
$$

where:
- $q$ is the critical value obtained from the studentized range distribution table or calculated using mathematical functions.
- $MSW$ is the mean square within-groups obtained from the ANOVA.
- $n$ is the number of observations in each group (assuming equal sample sizes).

Step 3: Calculate the mean differences:
For each pair of groups, calculate the difference between their means.

Step 4: Conduct pairwise comparisons:
Compare the absolute differences between the means of each pair of groups with the HSD value obtained in Step 2. If the absolute difference exceeds the HSD value, then the means of that pair of groups are considered significantly different.

Step 5: Interpret the results:
Based on the pairwise comparisons, identify which specific group pairs have statistically significant differences in means. These pairs are the ones that have absolute differences greater than the HSD value.

Tukey's test is advantageous because it simultaneously considers multiple pairwise comparisons while controlling the overall family-wise error rate. By using the HSD value, it helps determine the minimum detectable difference needed to declare a significant mean difference between any pair of groups.





