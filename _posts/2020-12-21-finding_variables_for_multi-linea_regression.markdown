---
layout: post
title:      "Finding Variables For Multi-Linea Regression"
date:       2020-12-21 11:44:07 -0500
permalink:  finding_variables_for_multi-linea_regression
---


For the second project of the data science/machine learning program, we were tasked with creating a linear regression model to predict the price of houses in Kings County using either the variables given, or engineered variables of our own. While Linear Regression is known as one of the simplest machine learning algorithms, finding the correct variables took a lot of trial and error, along with deciding to use them as continuous or categorical variables. 


## Variables vs. Dependent Variable:

When choosing your variables, you first need to make sure that each variable has a relationship with the dependant variable you are trying to predict. For instance, in this project we were instructed to use our model to predict the housing prices in Kings County. Each variable I ended up choosing had a relationship with price, making it easier to tell how one additional unit in each variable would directly affect the price of a given house in the model. 


## Avoiding Multicollinearity:

One your variables have been chosen, you need to make sure that each variable is not strongly correlated with one another. The reason for this is that is can add redundancy, and possibly affect the accuracy of your model. For example, if two of the variables in the model for predicting height are year born and age, you should get rid of one of them because they are essentially saying the same thing. In other words, year born and age will have an almost perfect correlation with one another, resulting in multicollinearity in the model. 

## P-Values

![](https://www.statisticshowto.com/wp-content/uploads/2014/01/p-value1.jpg)

The P-values for each of your chosen variables also need to be less than .05 to show that they are indeed significant to the model. In this project I had to change around my variables many times simply because my p-values would be too high for one or more variables. 

## Meaningful Coefficients 

One the model is run, you lastly need to make sure that each coefficient for you variables makes sense in the context of the model. For example, lets say that your model is trying to predict the height of a person, and age is one of your variables. If your constant is zero and age has a negative coefficient, this wouldn't make much sense.  We would expect age to have a positive coefficient since each additional year (up to a certain point) should be correlated with an increase in height. 

![](https://miro.medium.com/max/2872/1*_TqRJ9SmwFzRigJhMiN2uw.png)


# Conclusion

Finding meaningful variables for performing a multi-linear regression can be an exhausting process given all the requirements that must be fulfilled. If your model includes multicollinearity, you may need to get rid of one or more of your variables. If your p-values are too high, some variables should either be dropped or added. If you can't make sense of your coefficients, you may need to change your variables as well. However, it is a very exciting when you eventually find out that your model works with an above average R^2 value, meaningful coefficients, and p-values all below .05. While linear regression is not known to be the most accurate form of machine learning, I'm looking forward to learning about all the other methods in the modules to come!








