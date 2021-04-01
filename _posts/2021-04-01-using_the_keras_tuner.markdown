---
layout: post
title:      "Using the Keras Tuner"
date:       2021-04-01 19:09:29 +0000
permalink:  using_the_keras_tuner
---


![](https://repository-images.githubusercontent.com/231190401/931fd800-8c88-11ea-8bbd-fcfcb6dac20f)

When starting any machine learning project, it is essential to try and understand which models make the most sense to use given the context of the problem. After the first model is fit to a particular dataset, the next step will always be to start changing hyperparameters, and seeing if any of these changes results in a noticeable difference in accuracy. A popular method when utilizing models such as Decision Trees or Random Forests is to use GridSearchCV, which will examine the hyperparameter options you give it, make models for every combination of every hyperparameter, and then return the model with the best accuracy. However, this process is a little different when it comes to using neural networks with Keras. 
