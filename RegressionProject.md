---
title: "Regression Project"
output: html_document
---

#Executive Summary

Overall my analysis tells me the transmission type doesn't really have a significant impact on the fuel economy of a car once you account for other factors, such as weight and number of cyllinders.







#Results


```r
mtcars$am <- factor(mtcars$am, levels=c(0, 1), labels=c('Auto', 'Man'))
mtcars$vs <- factor(mtcars$vs, levels=c(0, 1), labels=c('V', 'S'))
lm1 <- lm(mpg ~ am + wt, mtcars)
```

```
## Error in `contrasts<-`(`*tmp*`, value = contr.funs[1 + isOF[nn]]): contrasts can be applied only to factors with 2 or more levels
```

```r
summary(lm1)
```

```
## 
## Call:
## lm(formula = mpg ~ am + wt, data = mtcars)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -4.5295 -2.3619 -0.1317  1.4025  6.8782 
## 
## Coefficients:
##             Estimate Std. Error t value          Pr(>|t|)    
## (Intercept) 37.32155    3.05464  12.218 0.000000000000584 ***
## amManual    -0.02362    1.54565  -0.015             0.988    
## wt          -5.35281    0.78824  -6.791 0.000000186741504 ***
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 3.098 on 29 degrees of freedom
## Multiple R-squared:  0.7528,	Adjusted R-squared:  0.7358 
## F-statistic: 44.17 on 2 and 29 DF,  p-value: 0.000000001579
```

```r
lm2 <- lm(mpg ~ vs + wt + cyl, mtcars)
```

```
## Error in `contrasts<-`(`*tmp*`, value = contr.funs[1 + isOF[nn]]): contrasts can be applied only to factors with 2 or more levels
```

```r
summary(lm2)
```

```
## 
## Call:
## lm(formula = mpg ~ vs + wt + cyl, data = mtcars)
## 
## Residuals:
##     Min      1Q  Median      3Q     Max 
## -4.3115 -1.7450 -0.3759  1.5174  6.0433 
## 
## Coefficients:
##             Estimate Std. Error t value         Pr(>|t|)    
## (Intercept)  38.7461     3.3989  11.399 0.00000000000495 ***
## vsS           0.5242     1.6271   0.322         0.749734    
## wt           -3.2464     0.7879  -4.120         0.000304 ***
## cyl          -1.3641     0.6135  -2.223         0.034433 *  
## ---
## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
## 
## Residual standard error: 2.608 on 28 degrees of freedom
## Multiple R-squared:  0.8309,	Adjusted R-squared:  0.8127 
## F-statistic: 45.85 on 3 and 28 DF,  p-value: 0.0000000000624
```

The model above shows that weight has a clear negative effect on the miles per gallon. There is a drop of 5.35 miles per gallon for every additional 1000 pounds of weight. However no significant changed is incurred due to the type of transmission.

In the second model, the transmission type doesn't have much impact once you account for weight and number of cyllinders, as the coefficients suggest.


```r
library(car)
scatterplot(mpg ~ wt | am, data=mtcars, 
  	xlab="Weight", ylab="Miles Per Gallon", 
   main="Scatter Plot", 
   labels=row.names(mtcars))
```

```
## Warning in min(x): no non-missing arguments to min; returning Inf
```

```
## Warning in max(x): no non-missing arguments to max; returning -Inf
```

```
## Warning in min(x): no non-missing arguments to min; returning Inf
```

```
## Warning in max(x): no non-missing arguments to max; returning -Inf
```

```
## Error in plot.window(...): need finite 'xlim' values
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2-1.png) 

