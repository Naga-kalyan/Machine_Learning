# Linear Regression
In statistics, **linear regression** is a **linear** approach to modeling the relationship between a scalar response (or **dependent variable**) and one or more explanatory variables (or **independent variables**). The case of one explanatory variable is called **simple linear regression**.
#### Examples :-
1. stock price prediction.
2. Rain fall prediction.
3. predict number of users who will click on an internet advertisement.

### Assumptions of  Linear Regression :-
1. **Linearity**: The relationship between X and the mean of Y is linear.
2. **Homoscedasticity**: The variance of residual is the same for any value of X.
3. **Independence**: Observations are independent of each other.
4. **Normality**: For any fixed value of X, Y is normally distributed. 

### Formula for simple Linear Regression :-
* Let 'x' be the independent varaiable, and y is a dependent variable.
* For **example**:
    - 'x' is temperature today, 'y' is amount of rainfall
    - 'x' is advertising budget, 'y' is sales
* Regression model is the function f, such that `y=f(x)`
* The equation can be given as `y=mx+c`
<br> Where <img src="https://render.githubusercontent.com/render/math?math={m}={\frac{n\sum xy - (\sum x \sum y)}{n\sum x^2 - (\sum x)^2}}">
<br>&emsp;&emsp;&nbsp;&nbsp;&nbsp; <img src="https://render.githubusercontent.com/render/math?math=c = \bar {y} - {m \bar{x}}">

### How to find coefficient that best fits the data :-
* Find the line which minimizes the error
* That is, find the difference between the **actual value** of y and **predict value** of y
* **Sum of Squared Differences** should be **minimum**
* Sum of Squared error :- 
<br><img src="https://render.githubusercontent.com/render/math?math={s} = {\sum_{i=1}^n(y_{i}-(mx%2Bc))^2}">
<br>Where <img src="https://render.githubusercontent.com/render/math?math=y_{i}"> is **Actual Value of y**
<br>&emsp;&emsp;&nbsp;&nbsp;&nbsp; <img src="https://render.githubusercontent.com/render/math?math={mx%2Bc}"> is **predicted value of y**

### Residual :-
* A **residual** is the vertical distance between a data point and the regression line. Each data point has one residual. They are positive if they are above the regression line and negative if they are below the regression line. If the regression line actually passes through the point, the residual at that point is zero.
* The residual(e) can also be expressed with an equation.
<br>`Residual e = Observed value - Predicted value`
* As residuals are the difference between any data point and the regression line, they are sometimes called **“errors”**.
* The sum of the residuals always equals **zero** (assuming that your line is actually the line of **“best fit**”.

### Coefficient of Determination, <img src="https://render.githubusercontent.com/render/math?math={R^2}"> :-
* R-squared is a **goodness-of-fit** measure for linear regression models.
* This statistic indicates the percentage of the variance in the dependent variable that the independent variables explain collectively.
* R-squared measures the strength of the relationship between your model and the dependent variable on a convenient 0 – 100% scale.
* R-squared evaluates the scatter of the data points around the fitted regression line. It is also called the **coefficient of determination**, or the coefficient of multiple determination for multiple regression. For the same data set, higher R-squared values represent smaller differences between the observed data and the fitted values.
* R-squared is the percentage of the dependent variable variation that a linear model explains.
<br><img src="https://render.githubusercontent.com/render/math?math={R^2}=1-{\frac{Sum of Squared Regression Error}{Sum Squared Error}}=1-{\frac{SSR}{SST}}={\frac{\sum(\hat y - y)^2}{\sum(y - \bar y)^2}}">
* <img src="https://render.githubusercontent.com/render/math?math={R^2}"> is always between 0 and 100%
    - 0% represents a model that does not explain any of the variation in the response variable around its mean. The mean of the dependent variable predicts the dependent variable as well as the regression model.
    - 100% represents a model that explains all of the variation in the response variable around its mean.
* Usually, the **larger** the <img src="https://render.githubusercontent.com/render/math?math={R^2}">, the better the regression model fits your observations.

#### <img src="https://render.githubusercontent.com/render/math?math={R^2}"> has limitations :-
* You cannot use R-squared to determine whether the coefficient estimates and predictions are biased, which is why you must assess the residual plots.
* R-squared does not indicate if a regression model provides an adequate fit to your data. A good model can have a low R2 value. On the other hand, a biased model can have a high <img src="https://render.githubusercontent.com/render/math?math={R^2}"> value!

### Adjusted <img src="https://render.githubusercontent.com/render/math?math={R^2}"> :-
* Use adjusted R-squared to compare the goodness-of-fit for regression models that contain differing numbers of independent variables.
* Let’s say you are comparing a model with five independent variables to a model with one variable and the five variable model has a higher R-squared. Is the model with five variables actually a better model, or does it just have more variables? To determine this, just compare the adjusted R-squared values!
* It measures the proportion of variation explained by only those independent variables that really help in explaining the dependent variable. It penalizes you for adding independent variable that do not help in predicting the dependent variable.
* Adjusted R-Squared can be calculated mathematically in terms of sum of squares. The only difference between R-square and Adjusted R-square equation is **degree of freedom**.
<br><img src="https://render.githubusercontent.com/render/math?math={Adj {R^2}}={\frac{(1-{R^2})(n-1)}{n-p-1}}">
<br>Where n = Total sample size
<br>&emsp;&emsp;&nbsp;&nbsp;&nbsp; p = number of independent variables

### Difference between <img src="https://render.githubusercontent.com/render/math?math={R^2}"> and Adjusted <img src="https://render.githubusercontent.com/render/math?math={R^2}"> :-
* Every time you add a independent variable to a model, the **R-squared** increases, even if the independent variable is insignificant. It never declines. Whereas **Adjusted R-squared** increases only when independent variable is significant and affects dependent variable.
* suppose, if adjusted r-squared is maximum when we included two variables. It declines when third variable is added. Whereas r-squared increases when we included third variable. It means third variable is insignificant to the model.
* Adjusted r-squared can be negative when r-squared is close to zero.
* Adjusted r-squared value always be less than or equal to r-squared value.

### Predicted <img src="https://render.githubusercontent.com/render/math?math={R^2}"> :-
* predicted R-squared to determine how well a regression model makes predictions.
* This statistic helps you identify cases where the model provides a good fit for the existing data but isn’t as good at making predictions. However, even if you aren’t using your model to make predictions, predicted R-squared still offers valuable insights about your model.
* Statistical software calculates predicted R-squared using the following procedure:
    - It removes a data point from the dataset.
    - Calculates the regression equation.
    - Evaluates how well the model predicts the missing observation.
    - And, repeats this for all data points in the dataset.
* If the **predicted R-squared** is **small** compared to **R-squared**, you might be **over-fitting** the model even if the independent variables are statistically significant.

### Over Fitting & Under Fitting :-
1. **Over Fitting** :
    * If the curve fits the given data perfectly, then the model may not be able to predict the future data properly. This is known as Over Fitting.
    * Good performance on the training data, poor generliazation to other data.
2. **Under Fitting** :
    * If the error(residuals) is high then it is known as Underfitting.
    * Poor performance on the training data and poor generalization to other
    
### Bias & Variance :-
1. **Bias** :
    * Bias are the simplifying assumptions made by a model to make the target function easier to learn.
    * Generally, linear algorithms have a high bias making them fast to learn and easier to understand but generally less flexible. In turn, they have lower predictive performance on complex problems that fail to meet the simplifying assumptions of the algorithms bias.
        * **Low Bias** : Suggests less assumptions about the form of the target function.
        * **High-Bias** : Suggests more assumptions about the form of the target function.
2. **Variance** :
    * Variance is the amount that the estimate of the target function will change if different training data was used.
    * The target function is estimated from the training data by a machine learning algorithm, so we should expect the algorithm to have some variance.
    * The error due to variance is taken as the variability of a model prediction for a given data point.
    * Variance shows how subject the model is to outliers, meaning those values are far away from mean.
        * **Low Variance** : Suggests small changes to the estimate of the target function with changes to the training dataset.
        * **High Variance** : Suggests large changes to the estimate of the target function with changes to the training dataset.
3. The goal of any supervised machine learning algorithm is to achieve **low bias** and **low variance**. In turn the algorithm should achieve good prediction performance.
    * **Linear** machine learning algorithms often have a **high bias** but a **low variance**.
    * **Nonlinear** machine learning algorithms often have a **low bias** but a **high variance**.
    
4. The parameterization of machine learning algorithms is often a battle to balance out bias and variance.
5. There is no escaping the relationship between bias and variance in machine learning.
    * **Increasing** the **bias** will decrease the **variance**.
    * **Increasing** the **variance** will decrease the **bias**.
    
###  Advantages and Disadvantages of Linear Regression :-
<table width="100%">
<thead>
<tr>
<th align='center'>Advantages</th>
<th>Disadvantages</th>
</tr>
</thead>
<tbody>
<tr>
<td>Linear Regression is simple to implement and easier to interpret the output coefficients.</td>
<td>On the other hand in linear regression technique outliers can have huge effects on the regression and boundaries are linear in this technique.</td>
</tr>
<tr>
<td>When you know the relationship between the independent and dependent variable have a linear relationship, this algorithm is the best to use because of it’s less complexity to compared to other algorithms.</td>
<td>Diversely, linear regression assumes a linear relationship between dependent and independent variables. That means it assumes that there is a straight-line relationship between them. It assumes independence between attributes.</td>
</tr>
<tr>
<td>Linear Regression is susceptible to over-fitting but it can be avoided using some dimensionality reduction techniques, regularization (L1 and L2) techniques and cross-validation.</td>
<td>But then linear regression also looks at a relationship between the mean of the dependent variables and the independent variables. Just as the mean is not a complete description of a single variable, linear regression is not a complete description of relationships among variables.</td>
</tr>
</tbody>
</table>
