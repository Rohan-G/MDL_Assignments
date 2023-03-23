# Report

## Q1 

### LinearRegression().fit()

LinearRegression fits a linear model with coefficients w = ($w_1$, …, $w_n$) to minimize the cost function (sum of predicted values of y on our training set to the actual observed values of y). The fit method fits the Linear Regression model onto our training set using plain Ordinary Least Squares or Non Negative Least Squares, rather than the gradient descent method.

### Ordinary Least Squares

This method uses plain pseudo-inverse to find the solution to $$AX=B$$
Pseudo inverse:
$$(B^TB)^{-1}$$

## Q2

### Gradient Descent
Gradient descent aims to find the coefficients that locally minimize the cost function ( the sum of squares of difference between our current predicted value and the training set's provided value ). It does this in the following way: <br>
Consider the following equation:
$$
y = mx + b
$$
$$
C = \sum_{i=1}^{n} (mx_i + b - y_i)^2
$$
where $y$ is our dependent variable, $x$ is our independent variable, $(x_i,y_i)$ is the $i^{th}$ point in the training set, $C$ is the cost function, and $n$ is the size of the training set. <br>
We change the values of $m$ and $b$ with the following equation, taking a random initial value for each:
$$
\Delta w = -\alpha \frac{dC}{dw}
$$
where $\alpha$ is the learning rate and $w$ is the coefficient we want to change (m and b).<br>
Hence,
$$
\Delta m = -2 \alpha (m_{old}x_i + b_{old} - y_i) x_i
$$
$$
\Delta b = -2 \alpha (m_{old}x_i + b_{old} - y_i)
$$
We keep taking small steps, the size of which is defined by the learning rate (usually $10^-3$ to $10^-4$, but depends on our particular needs), till we reach the nearest minima. <br>
We know that this method gets us to the nearest minima as we keep taking small steps till $\frac{dC}{dw}$ becomes 0 (we set $\alpha$ which should evidently not be 0 or else we have 0 step size and aren't trying to find anything) and moving over the negative value ($-\alpha \frac{dC}{dw}$) of the slope (Hence, if slope is positive (function is increasing), we move backwards towards the smaller value and if the slope is negative (function is decreasing), we move forwards towards the smaller value ).

## Q3
### Bias-Variance Tradeoff
| Degree | Bias | Variance |
| ------ | ---- | -------- |
| 1 | 0.2698749874328136 | 0.005384121178583774 |
| 2 | 0.08690825549169226 | 0.0014132705271420532 |
| 3 | 0.03332808779760927 | 0.00046531619264977066 |
| 4 | 0.026704905407178306 | 0.0006320960607956194 |
| 5 | 0.025982322485939437 | 0.0009098984831737561 |
| 6 | 0.025653007373353177 | 0.0009843175261205232 |
| 7 | 0.026031948029229396 | 0.001210456345942013 |
| 8 | 0.026036556807045974 | 0.0013306253704325655 |
| 9 | 0.03204138621983644 | 0.008505698388728455 |
| 10 | 0.036641611957433574 | 0.022126447446899712 |
| 11 | 0.052001857556003096 | 0.24357527764628578 |
| 12 | 0.11717001647755972 | 2.1537000863771794 |
| 13 | 0.12305792542018035 | 14.593767892910064 |
| 14 | 0.39194286382632443 | 79.7833242083478 |
| 15 | 1.0266326303889224 | 339.6575811101034 |

Bias is how much our models vary from the actual value, and variance depicts how far off different variations of a model are from each other in their predicted values. As we increase our degree, our bias reduces. This happens because our model is able to better fit the training data due to the huge number of features (which is essentially 1 feature, $x$), which means it can capture more complex relations between $x$ and $y$. However, if the degree increases too much, this leads to overfitting and the model loses its ability to generalize and captures irrelevant relationships present due to noise in our data, thus increasing variance (different models were trained on different data which have different noise). Lower degrees, on the other hand, have very few features and hence have to highly generalize and capture highly relevant information. Since this highly relevant information is very unlikely to differ over different training sets, it is more likely to have lower variance in lower degrees. However, since they are not able to fully capture all relevant information, it will not perform as well as higher degree polynomials and will thus have higher biases.

## Q4
### Irreducible Error
| Degree | Irreducible Error |
| ------ | ----------------- |
| 1 | 1.3372549595436212e-17 |
| 2 | -7.708677446371937e-19 |
| 3 | 4.4951022071249015e-18 |
| 4 | 2.0572736222912446e-19 |
| 5 | 1.646089948376117e-18 |
| 6 | 7.766140161513668e-18 |
| 7 | 5.387807170895154e-19 |
| 8 | 3.1245351358316632e-18 |
| 9 | -4.621411760219463e-19 |
| 10 | 1.145188544687814e-18 |
| 11 | 2.718013531258223e-17 |
| 12 | 5.114344277939997e-16 |
| 13 | -3.4054833605856595e-15 |
| 14 | -4.9400257105466916e-15 |
| 15 | -4.534747550339821e-14 |

As we see, irreducible error does not vary much over different degrees. This is because these are errors which will always be present in our training data due to unknown variables, hence it is not dependent on the model and thus it will not differ much over different models.

## Q5
### $Bias^2 - Variance - MSE$ $Graph$
![Graph](graph.png)
As we can see from the figure and as was explained before (Q3), low degree polynomials are underfitted and hence have lower variance but higher bias. Higher degrees, on the other hand, are overfitted and have lower bias but higher variance. The mid range of degrees from ~ 3 to 8 seem to have a good Bias-Variance tradeoff and hence have low values of MSE, making them the ideal degrees (in our case) to find models from for actual use.

## Bonus
### Reducing the equation
#### Assuming the first value is time and the second value is charge in the given dataset
$$
Q = CV_0e^{\frac{-t}{RC}}
$$
$$
ln(Q) = ln(CV_0) - \frac{t}{RC}
$$
Hence, the intercept = $ln(5C)$ (Since $V_0$ = $5V$),<br>and $w$ (the only coefficient returned) = $\frac{-1}{RC}$
<br>Substituting in our equations, we get:
$$
C = 5 * 10e^{-5}
$$
$$
R = 100000.00000001 \approx 10^5
$$