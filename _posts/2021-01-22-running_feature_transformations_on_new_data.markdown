---
layout: post
title:      "Running Feature Transformations on New Data"
date:       2021-01-22 13:59:43 +0000
permalink:  running_feature_transformations_on_new_data
---


![](https://miro.medium.com/max/3840/1*sbmnCl9NzDPeyWP-Aw506w.jpeg)


One of the biggest skills a data scientist needs to harness is the ability to transform training data/make new features to make specific machine learning models work to the best of their ability. Most of the work in fitting a model to data comes in the form of preprocessing the data before new models are trained on it. An issue that some people may run into is needing to manually do everything they did to their training data on new unseen data that they need to make predictions on. To make matters more complicated, if you are making dummy variables and there is unfamiliar pieces of data in the test/training data, it will be impossible to fit your model on the new data. Thankfully, there are easy solutions to both of these problems. 


