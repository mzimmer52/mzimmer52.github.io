---
layout: post
title:      "Using the Keras Tuner"
date:       2021-04-01 15:09:30 -0400
permalink:  using_the_keras_tuner
---


![](https://repository-images.githubusercontent.com/231190401/931fd800-8c88-11ea-8bbd-fcfcb6dac20f)

When starting any machine learning project, it is essential to try and understand which models make the most sense to use given the context of the problem. After the first model is fit to a particular dataset, the next step will always be to start changing hyperparameters, and seeing if any of these changes results in a noticeable difference in accuracy. A popular method when utilizing models such as Decision Trees or Random Forests is to use GridSearchCV, which will examine the hyperparameter options you give it, make models for every combination of every hyperparameter, and then return the model with the best accuracy. However, this process is a little different when it comes to using neural networks with Keras. Due to the natural complexity of neural networks, it makes sense to utilize an algorithm than can run through many possible models just like GridSearchCV.

![](https://thumbor.forbes.com/thumbor/960x0/https%3A%2F%2Fspecials-images.forbesimg.com%2Fdam%2Fimageserve%2F966248982%2F960x0.jpg%3Ffit%3Dscale)

When the Keras Tuner is used, you can essentially put in as many hyperparameter options as you think necessary, and the algortithm will run through all possible combinations until it finished/the best model has been found. For example, we can take a look at the following code:

'def build_model(hp):
  model = Sequential()
  for i in range(hp.Int("first layer", min_value = 0, max_value = 3)):
    model.add(layers.Dense(hp.Choice(f"layer {i} features", [32, 64, 128, 256, 512]), activation='relu'))'
