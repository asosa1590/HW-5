# HW-5
HW 5
````


Authors: Antonio Sosa, Mirajul Fahim, Ahmed Aslam 

````

For our Homework Assignment we decided to have the poverty vlaue as our dependent variable (Y).
According to the PUMS data, poverty in our data set was defined as the household income divided by the previous year’s poverty threshold as determined by the Social Security Administration. As an example a participant making 40,000 a year in income, would have a poverty level of 2 if the poverty threshold were set at 20,000 dollars. Meaning the participant’s poverty ratio is above twice the poverty line.

Please note that our corresponding regression graphs are attached and labled as Ouput 2 ,3 ,4 and 5
 
 
`````

> attach(acs2017_ny)
> AGE2 <- acs2017_ny$AGE^2
> AGE3 <- acs2017_ny$AGE^3
> college <- educ_college==1
> college2 <- educ_advdeg==1
> output <- lm(POVERTY~ AGE + AGE2 + AGE3 + college + college2)
> summary(output)

> summary(output)

Call:
lm(formula = POVERTY ~ AGE + AGE2 + AGE3 + college + college2)

Residuals:
   Min     1Q Median     3Q    Max 
-458.6 -139.0   37.8  131.3  358.6 

Coefficients:
               Estimate Std. Error t value Pr(>|t|)
(Intercept)   3.138e+02  1.493e+00  210.21   <2e-16
AGE          -6.434e+00  1.416e-01  -45.43   <2e-16
AGE2          2.093e-01  3.594e-03   58.24   <2e-16
AGE3         -1.691e-03  2.639e-05  -64.06   <2e-16
collegeTRUE   1.103e+02  1.075e+00  102.59   <2e-16
college2TRUE  1.420e+02  1.202e+00  118.10   <2e-16
                
(Intercept)  ***
AGE          ***
AGE2         ***
AGE3         ***
collegeTRUE  ***
college2TRUE ***
---
Signif. codes:  
0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 165.4 on 196579 degrees of freedom
Multiple R-squared:  0.1303,	Adjusted R-squared:  0.1302 
F-statistic:  5888 on 5 and 196579 DF,  p-value: < 2.2e-16
````
`````


Output 1: In our Regression Model for Output 1 we wanted to interpret poverty in the PUMS data set by considering age, age value squared, age value cubed, college education and advanced college education. Based on the regression model we determined that all variables tested in the model were statistically significant. However, College Degree and Advanced Degree had the highest t-values in our model and therefore we concluded that these estimates created a positive correlation  between education and poverty. In other words higher education implied that a participant would not be in the impoverished threshold and would have a higher poverty threshold ratio. At the 95 significance level, AGE^2 and AGE^3 both had negative t values and lowered our intercept values for the regression. It;s important to note that the negative t values from the AGE based values did not greatly affect the  positive correlation between education and the poverty ratio value. Within this regression an increase of 1 percent of our poverty ratio led to a 110 increase in college degree and 142 increase in advanced degree.


````
> output2 <- lm(POVERTY ~ log1p(AGE), data=acs2017_ny)
> summary(output2)
Call:
lm(formula = POVERTY ~ log1p(AGE), data = acs2017_ny)

Residuals:
   Min     1Q Median     3Q    Max 
-342.8 -157.0   32.7  169.2  261.3 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)
(Intercept) 239.6969     1.6737  143.21   <2e-16
log1p(AGE)   22.5844     0.4646   48.62   <2e-16
               
(Intercept) ***
log1p(AGE)  ***
---
Signif. codes:  
0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 176.3 on 196583 degrees of freedom
Multiple R-squared:  0.01188,	Adjusted R-squared:  0.01187 
F-statistic:  2363 on 1 and 196583 DF,  p-value: < 2.2e-16

> output3 <-lm(POVERTY ~ AGE +AGE2 + AGE3, data=acs2017_ny )
> summary(output3)

Call:
lm(formula = POVERTY ~ AGE + AGE2 + AGE3, data = acs2017_ny)

Residuals:
    Min      1Q  Median      3Q     Max 
-361.52 -153.59   32.81  149.81  339.72 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)
(Intercept)  2.912e+02  1.559e+00  186.85   <2e-16
AGE         -2.878e+00  1.461e-01  -19.70   <2e-16
AGE2         1.559e-01  3.747e-03   41.61   <2e-16
AGE3        -1.474e-03  2.764e-05  -53.34   <2e-16
               
(Intercept) ***
AGE         ***
AGE2        ***
AGE3        ***
---
Signif. codes:  
0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 173.7 on 196581 degrees of freedom
Multiple R-squared:  0.04019,	Adjusted R-squared:  0.04018 
F-statistic:  2744 on 3 and 196581 DF,  p-value: < 2.2e-16
````

Output 2: In this regression model, we have a log-linear model. The t-statistic is statistically significant  with 99.9% confidence. A 1% increase in age increases poverty by 22.5844. The SER is 176.3. We did a log of (X) because polynomials have turning points, and log functions do not.  Both log functions and polynomials are used for  diminishing marginal returns, while log functions do not give turning points. Percentage chances are useful for judging economic significance of estimates.


````

> output3 <-lm(POVERTY ~ AGE +AGE2 + AGE3, data=acs2017_ny )
> summary(output3)

Call:
lm(formula = POVERTY ~ AGE + AGE2 + AGE3, data = acs2017_ny)

Residuals:
    Min      1Q  Median      3Q     Max 
-361.52 -153.59   32.81  149.81  339.72 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)
(Intercept)  2.912e+02  1.559e+00  186.85   <2e-16
AGE         -2.878e+00  1.461e-01  -19.70   <2e-16
AGE2         1.559e-01  3.747e-03   41.61   <2e-16
AGE3        -1.474e-03  2.764e-05  -53.34   <2e-16
               
(Intercept) ***
AGE         ***
AGE2        ***
AGE3        ***
---
Signif. codes:  
0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 173.7 on 196581 degrees of freedom
Multiple R-squared:  0.04019,	Adjusted R-squared:  0.04018 
F-statistic:  2744 on 3 and 196581 DF,  p-value: < 2.2e-16
```
````

Output 3: In this regression model, we have a cubic function. All the values were statistically significant, and the SER is 176.3 The turning point is  -1.559e-01/ (2*-1.474e-03), which is 53 years.  After 53 years, there is a diminishing rate of marginal returns. 


````

> output4 <- lm(log1p(POVERTY) ~ log1p(AGE), data=acs2017_ny)
> summary(output4)

Call:
lm(formula = log1p(POVERTY) ~ log1p(AGE), data = acs2017_ny)

Residuals:
    Min      1Q  Median      3Q     Max 
-5.4549 -0.2194  0.5562  0.8433  1.4161 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)
(Intercept) 4.802477   0.014042  342.00   <2e-16
log1p(AGE)  0.142946   0.003897   36.68   <2e-16
               
(Intercept) ***
log1p(AGE)  ***
---
Signif. codes:  
0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 1.479 on 196583 degrees of freedom
Multiple R-squared:  0.006796,	Adjusted R-squared:  0.006791 
F-statistic:  1345 on 1 and 196583 DF,  p-value: < 2.2e-16

````


Output 4: We created a regression comparing the log of poverty and age. Percentage chances are useful for judging economic significance of estimates. This regression model is a log-log function, so we are finding the elasticity. We determined that a 1 percent increase in AGE leads to a 14.3  percent increase in our poverty ratio.  The standard residual error became 1.479, the model significantly improved because outliers were removed through the use of log function. The higher SER means a smaller distance between the residual values and the  fitted values, thus resulting in more variation of (X)  in Y. 

````


> Output5 <- lm(POVERTY~ AGE + VETSTAT + I(AGE*VETSTAT) )
> summary(Output5)

Call:
lm(formula = POVERTY ~ AGE + VETSTAT + I(AGE * VETSTAT))

Residuals:
    Min      1Q  Median      3Q     Max 
-364.02 -157.76   32.64  170.13  215.60 

Coefficients:
                  Estimate Std. Error t value Pr(>|t|)    
(Intercept)      285.39798    1.09029 261.764  < 2e-16 ***
AGE                0.67415    0.04064  16.587  < 2e-16 ***
VETSTAT            4.92216    1.51753   3.244  0.00118 ** 
I(AGE * VETSTAT)   0.02490    0.03732   0.667  0.50461    
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 176.4 on 196581 degrees of freedom
Multiple R-squared:  0.01046,	Adjusted R-squared:  0.01044 
F-statistic: 692.6 on 3 and 196581 DF,  p-value: < 2.2e-16

`````




