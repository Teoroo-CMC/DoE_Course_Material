# Generate a mesh using numpy...
The must be better ways, but this seem to work.

```
span = np.linspace(0, 10, 100)
x1,x2=np.meshgrid(span,span)
x=np.array( [x1.flatten(),x2.flatten()] )
```

With pandas

```
import pandas as pd
span = np.linspace(0, 10, 100)
x1,x2=np.meshgrid(span,span)
x1_flat = x1.flatten()
x2_flat = x2.flatten()

data=pd.DataFrame({"x1":x1_flat,"x2":x2_flat})
```





## Multivariate linear regression

Multivariate Linear Regression is a statistical modeling technique used to analyze the relationship between multiple independent variables (also called predictors or features) and a single dependent variable. It extends the concept of simple linear regression, which deals with only one independent variable.

In multivariate linear regression, the goal is to find the best-fitting linear equation that represents the relationship between the independent variables and the dependent variable. The equation can be expressed as:

$y = \beta_0 + \beta_1x_1 + \beta_2x_2 + \ldots + \beta_px_p + \epsilon$

where:
- $y$ is the dependent variable.
- $\beta_0$ is the y-intercept or the constant term.
- $x_1, x_2, \ldots, x_p$ are the independent variables.
- $\beta_1, \beta_2, \ldots, \beta_p$ are the coefficients (regression weights) representing the effect of each independent variable on the dependent variable.
- $\epsilon$ is the error term or residual, which represents the unexplained variation in the dependent variable.

The coefficients $\beta_0, \beta_1, \ldots, \beta_p$ are estimated using a method called Ordinary Least Squares (OLS). The goal of OLS is to minimize the sum of squared residuals, which is the difference between the actual dependent variable values and the predicted values based on the linear equation.

The estimation of the coefficients involves solving a set of equations that minimize the sum of squared residuals. This can be done using matrix algebra techniques, such as the normal equation or matrix inversion.

To assess the overall fit of the multivariate linear regression model, various statistical measures can be used, including the coefficient of determination (R-squared), adjusted R-squared, F-statistic, and p-values associated with the coefficients. These measures help determine the proportion of the dependent variable's variability explained by the model and the statistical significance of the independent variables.

### Normal equations and the Ordinary Least Squares (OLS)
Linear regression can be related to the normal equations, which provide a closed-form solution for finding the optimal values of the regression coefficients. The normal equations are derived from the principle of minimizing the sum of squared residuals (also known as the Ordinary Least Squares method).

Let's consider the case of simple linear regression with one predictor variable. The relationship between the predictor variable ($x$) and the response variable ($y$) can be represented by the equation:
$
 y = \beta_0 + \beta_1x + \epsilon
$

where $\beta_0$ is the intercept, $\beta_1$ is the slope coefficient, and $\epsilon$ is the error term.

The goal of linear regression is to estimate the values of $\beta_0$ and $\beta_1$ that minimize the sum of squared residuals:

$ \text{minimize} \sum_{i=1}^{n} (y_i - (\beta_0 + \beta_1x_i))^2 $

To find the optimal values of $\beta_0$ and $\beta_1$, we differentiate the sum of squared residuals with respect to each coefficient and set the derivatives equal to zero. This leads to the normal equations:

$ \sum_{i=1}^{n} y_i = n\beta_0 + \beta_1\sum_{i=1}^{n} x_i $

$ \sum_{i=1}^{n} x_iy_i = \beta_0\sum_{i=1}^{n} x_i + \beta_1\sum_{i=1}^{n} x_i^2 $

These equations represent a system of linear equations that can be solved to obtain the estimates of $\beta_0$ and $\beta_1$.

For multiple linear regression with $K$ predictor variables, the normal equations can be extended to a matrix form:

$ \mathbf{X}^T\mathbf{X}\mathbf{b} = \mathbf{X}^T\mathbf{y} $

where $\mathbf{X}$ is the design matrix containing the predictor variables, $\mathbf{y}$ is the response variable vector, and $\mathbf{b}$ is the coefficient vector to be estimated.

By solving the normal equations, we can obtain the estimates of the regression coefficients, which represent the best-fitting line or hyperplane that minimizes the sum of squared residuals.

The normal equations provide a closed-form solution for linear regression, but in practice, other methods such as gradient descent or matrix factorization techniques may be used for computational efficiency or when dealing with large datasets.


### Goodness-of-fit: R-squared
R-squared, also known as the coefficient of determination, is a statistical measure that represents the proportion of the variance in the dependent variable (response variable) that can be explained by the independent variables (predictor variables) in a regression model.

The key formula for calculating R-squared is as follows:

$ R^2 = 1 - \frac{{\sum_{i=1}^{n}(y_i - \hat{y_i})^2}}{{\sum_{i=1}^{n}(y_i - \bar{y})^2}} $

where:
- $ y_i $ represents the observed values of the dependent variable.
- $ \hat{y_i} $ represents the predicted values of the dependent variable obtained from the regression model.
- $ \bar{y} $ represents the mean of the observed values of the dependent variable.
- $ n $ represents the number of data points or observations.

In simpler terms, R-squared measures the proportion of the total variation in the dependent variable that can be accounted for by the regression model. It ranges from 0 to 1, where:
- An R-squared value of 0 indicates that the model does not explain any of the variability in the dependent variable.
- An R-squared value of 1 indicates that the model explains all of the variability in the dependent variable.

However, it is important to note that R-squared alone does not provide a complete assessment of the model's performance. It does not indicate whether the model is a good fit or whether the coefficients are statistically significant. Therefore, it should be interpreted alongside other diagnostic measures and statistical tests.


### Goodness-of-fit: Adjusted R-squared

Adjusted R-squared is a modified version of R-squared that takes into account the number of predictor variables in the regression model. It provides a more reliable measure of the model's goodness-of-fit, especially when comparing models with different numbers of predictors.

The key formula for calculating adjusted R-squared is as follows:

$ \text{Adjusted } R^2 = 1 - \left(\frac{{n - 1}}{{n - k - 1}}\right)\left(1 - R^2\right) $

where:
- $ n $ represents the number of data points or observations.
- $ k $ represents the number of predictor variables (independent variables) in the regression model.
- $ R^2 $ represents the unadjusted R-squared value.

Adjusted R-squared penalizes the inclusion of unnecessary predictor variables in the model. It adjusts the R-squared value by subtracting a penalty term that increases with the number of predictors relative to the number of observations. This penalty accounts for the possibility of overfitting, where a model with more predictors may artificially inflate the R-squared value.

By considering the degrees of freedom in the calculation, adjusted R-squared provides a more accurate measure of the model's goodness-of-fit and helps in comparing models with different numbers of predictors. A higher adjusted R-squared value indicates a better fit of the model to the data, while accounting for model complexity.

### Goodness-of-fit: F-test
In multivariate linear regression, the F-statistic is commonly used to assess the overall significance of the regression model. It tests the hypothesis that all of the regression coefficients (except the intercept) are equal to zero, indicating that there is no significant relationship between the independent variables and the dependent variable.

The F-statistic is calculated by comparing the variation explained by the regression model to the unexplained variation or residual variation. The general formula for calculating the F-statistic in multivariate linear regression is as follows:

$F = \frac{{(SSR / df_{\text{Regression}})}}{{(SSE / df_{\text{Residual}})}}$

where:
- SSR is the sum of squares regression, which represents the explained variation by the regression model.
- SSE is the sum of squares error or sum of squared residuals, which represents the unexplained variation or residual variation.
- $df_{\text{Regression}}$ is the degrees of freedom for the regression model, which is equal to the number of independent variables.
- $df_{\text{Residual}}$ is the degrees of freedom for the residuals, which is equal to the number of observations minus the number of independent variables minus one.

The F-statistic follows an F-distribution with $df_{\text{Regression}}$ and $df_{\text{Residual}}$ degrees of freedom.

To interpret the F-statistic, you compare it to the critical value from the F-distribution for a given significance level (e.g., 0.05 or 0.01). If the calculated F-statistic is greater than the critical value, you reject the null hypothesis and conclude that there is a significant relationship between the independent variables and the dependent variable. Conversely, if the calculated F-statistic is smaller than the critical value, you fail to reject the null hypothesis, suggesting that there is no significant relationship.

It's important to note that the F-statistic tests the joint significance of all the independent variables in the model. It does not provide information about the significance of individual variables. To assess the significance of individual variables, you can examine their corresponding t-statistics and p-values.

### Goodness-of-fit: F-test (example)
Suppose we collected data from a study involving 50 participants. We measured their height (independent variable 1), weight (independent variable 2), and blood pressure (dependent variable). Here's a sample of the data:

| Participant | Height (cm) | Weight (kg) | Blood Pressure (mmHg) |
|-------------|-------------|-------------|-----------------------|
| 1           | 165         | 68          | 120                   |
| 2           | 172         | 74          | 130                   |
| 3           | 158         | 60          | 115                   |
| ...         | ...         | ...         | ...                   |
| 50          | 170         | 72          | 125                   |

We want to determine if there is a significant relationship between height, weight, and blood pressure.

Performing a multivariate linear regression analysis on this data, we obtain the following results:

- Sum of Squares Regression (SSR): 2400
- Degrees of Freedom for Regression ($df_{\text{Regression}}$): 2 (since we have 2 independent variables)
- Sum of Squares Error (SSE): 1800
- Degrees of Freedom for Residual ($df_{\text{Residual}}$): 47 (50 observations minus 2 independent variables minus 1)

Using these values, we can calculate the F-statistic:

$F = \frac{{SSR / df_{\text{Regression}}}}{{SSE / df_{\text{Residual}}}} = \frac{{2400 / 2}}{{1800 / 47}} \approx 6.18$

Now, let's assume that the critical F-value at a significance level of 0.05 for our degrees of freedom (2, 47) is 3.15.

Comparing the calculated F-statistic (6.18) to the critical F-value (3.15), we find that the calculated F-statistic is greater. Therefore, we reject the null hypothesis and conclude that there is a significant relationship between height, weight, and blood pressure in this example.

This result suggests that the combination of height and weight has a significant impact on blood pressure, as indicated by the F-statistic.


### t-test and the standard error in the regression coefficients

$
SE(\hat{\beta}_1) = \sqrt{\frac{{\sum_{i=1}^n (y_i - \hat{y}_i)^2}}{{(n - 2) \sum_{i=1}^n (x_i - \bar{x})^2}}}
$

In this formula, $SE(\hat{\beta}_1)$ represents the standard error of the regression slope ($\hat{\beta}_1$). The terms $y_i$ and $\hat{y}_i$ refer to the observed and predicted values of the dependent variable for the $i$th observation, respectively. The term $n$ represents the total number of observations, while $x_i$ represents the value of the independent variable for the $i$th observation. The symbol $\bar{x}$ denotes the mean of the independent variable.

The standard error of the regression slope is a measure of the precision or uncertainty associated with the estimated slope coefficient in a linear regression model. It quantifies the average amount by which the estimated slope coefficient would vary if the same regression analysis were repeated on different samples from the same population.


To test the significance of regression coefficients using the t-test, you can follow these steps:

1. Perform linear regression and obtain the estimated coefficients for each predictor variable.

2. Calculate the standard error of each coefficient estimate. This can be done using the formula:

   $ SE(\beta_i) = \frac{{\hat{\sigma}}}{{\sqrt{{\sum (x_i - \bar{x})^2}}}} $

   where $ \hat{\sigma} $ is the residual standard deviation, $ x_i $ represents the predictor variable, and $ \bar{x} $ is the mean of the predictor variable.

3. Compute the t-statistic for each coefficient using the formula:

   $ t = \frac{{\hat{\beta_i}}}{{SE(\beta_i)}} $

   where $ \hat{\beta_i} $ is the estimated coefficient.

4. Determine the degrees of freedom for the t-test. For simple linear regression with one predictor variable, the degrees of freedom will be $ n - 2 $, where $ n $ is the number of observations.

5. With the t-statistic and degrees of freedom, calculate the p-value associated with each coefficient using the t-distribution. This can be done using statistical software or t-tables.

6. Compare the p-values to a chosen significance level (e.g., 0.05) to determine the significance of each coefficient. If the p-value is less than the significance level, the coefficient is considered statistically significant.

By performing the t-test on the regression coefficients, you can assess whether each predictor variable has a statistically significant impact on the dependent variable in the regression model.

Please note that the above steps assume the use of simple linear regression with one predictor variable. For multiple regression with multiple predictor variables, the process is similar, but the degrees of freedom and calculations may differ slightly.


### Ridge regression

Ridge regression is a regularization technique used in linear regression to address multicollinearity and improve the stability of the regression model. It adds a penalty term to the ordinary least squares (OLS) objective function, resulting in the following modified objective function:
$$
\text{Minimize:} \quad \sum_{i=1}^{n} (y_i - \beta_0 - \sum_{j=1}^{p} \beta_j x_{ij})^2 + \lambda \sum_{j=1}^{p} \beta_j^2
$$

where:
- $n$ is the number of observations.
- $y_i$ is the observed value of the dependent variable for the $i$th observation.
- $\beta_0$ is the intercept.
- $x_{ij}$ is the value of the $j$th independent variable for the $i$th observation.
- $\beta_j$ is the coefficient associated with the $j$th independent variable.
- $p$ is the number of independent variables.
- $\lambda$ (lambda) is the regularization parameter, controlling the amount of shrinkage applied to the coefficients.

The modified objective function includes a penalty term, $\lambda \sum_{j=1}^{p} \beta_j^2$, which encourages smaller coefficient values. The parameter $\lambda$ determines the strength of the regularization, with higher values leading to greater shrinkage.

To estimate the ridge regression coefficients, we minimize the modified objective function using techniques such as gradient descent or closed-form solutions.

Once the ridge regression coefficients are estimated, they can be used to make predictions on new data in the same way as ordinary linear regression.

Ridge regression offers a trade-off between model complexity and model fit. By introducing the penalty term, it reduces the impact of multicollinearity and can help prevent overfitting. The optimal value of $\lambda$ can be determined using techniques like cross-validation or by minimizing a criterion such as the mean squared error.


### Kernel ridge regression (KRR)

Kernel ridge regression is an extension of ridge regression that allows for nonlinear relationships between the independent variables and the dependent variable. It achieves this by employing the kernel trick, which maps the original features into a higher-dimensional feature space, where linear relationships can be effectively captured.

In kernel ridge regression, the objective function is modified to incorporate a kernel function that operates on the transformed feature space. The modified objective function can be written as:

$\text{Minimize:} \quad \sum_{i=1}^{n} (y_i - \beta_0 - \sum_{j=1}^{n} \alpha_j K(x_i, x_j))^2 + \lambda \sum_{j=1}^{n} \alpha_j^2$

where:
- $n$ is the number of observations.
- $y_i$ is the observed value of the dependent variable for the $i$th observation.
- $\beta_0$ is the intercept.
- $x_i$ and $x_j$ represent the feature vectors for the $i$th and $j$th observations, respectively.
- $K(x_i, x_j)$ is the kernel function that computes the similarity between the transformed feature vectors.
- $\alpha_j$ represents the coefficients associated with the kernel function.

The kernel function allows us to implicitly work in the higher-dimensional feature space without explicitly calculating the transformed feature vectors. It captures the similarity or distance between observations in the transformed space, enabling nonlinear relationships to be modeled.

The choice of the kernel function depends on the specific problem and data characteristics. Popular kernel functions include the linear kernel, polynomial kernel, Gaussian (RBF) kernel, and sigmoid kernel, among others.

Similar to ridge regression, kernel ridge regression also includes a regularization parameter, $\lambda$, that controls the trade-off between model complexity and model fit. Higher values of $\lambda$ increase the amount of regularization, leading to smoother and more generalized models.

To estimate the coefficients in kernel ridge regression, one typically uses techniques such as gradient descent or matrix factorization methods.

Once the coefficients are estimated, predictions can be made for new data points using the kernel function and the learned coefficients.

Kernel ridge regression is particularly useful when dealing with nonlinear relationships between variables and can offer improved predictive performance compared to linear models when appropriate kernel functions are chosen.


### Simple example of Kernel Ridge Regression:

Suppose we have a dataset with $N$ samples and $D$ features, denoted as $X = \{x_1, x_2, \ldots, x_N\}$, and corresponding target values $y = \{y_1, y_2, \ldots, y_N\}$.

1. Compute the Kernel Matrix:
First, we need to compute the kernel matrix $K$ using a kernel function $k(x, x')$, which measures the similarity between two data points. In this example, we'll use the radial basis function (RBF) kernel:
$
K_{ij} = k(x_i, x_j) = \exp\left(-\frac{\|x_i - x_j\|^2}{2\sigma^2}\right)
$

2. Estimate Ridge Regression Coefficients:
Next, we estimate the ridge regression coefficients $\alpha$ by solving the following equation:
$
\alpha = (K + \lambda I)^{-1} y
$
where $\lambda$ is the regularization parameter and $I$ is the identity matrix.

3. Make Predictions:
To make predictions for a new data point $x_{\text{new}}$, we use the following formula:
$$
\hat{y}_{\text{new}} = \sum_{i=1}^{N} \alpha_i k(x_{\text{new}}, x_i)
$$
where $\hat{y}_{\text{new}}$ is the predicted value for $x_{\text{new}}$, $\alpha_i$ are the ridge regression coefficients, and $k(x_{\text{new}}, x_i)$ is the kernel function evaluated between $x_{\text{new}}$ and $x_i$.

4. Kernel Function (RBF):
The RBF kernel is defined as:
$
k(x, x') = \exp\left(-\frac{\|x - x'\|^2}{2\sigma^2}\right)
$
where $x$ and $x'$ are input vectors, and $\sigma$ is the kernel bandwidth parameter.


# Further reading:
https://en.wikipedia.org/wiki/Regression_analysis
https://en.wikipedia.org/wiki/Linear_regression
