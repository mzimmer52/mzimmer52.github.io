---
layout: post
title:      "Deep Learning Visualization"
date:       2021-02-06 09:20:14 -0500
permalink:  deep_learning_visualization
---


![](https://miro.medium.com/max/453/1*51D0MqtqHu3h2vTE5oJ-7g.png)



In module 4, one of the most important things introduced is neural networks. While neural networks are certainly impressive in their ability to make accurate predictions, the neural network is only as good as the design the programmer desides to give it. Using the Keras library in python, it is fairly simple to add more layers to your neural network, change your optimizer, and make other changes that may either increase or decrease your model's accuracy. Like other machine learning models, there is always the risk of overfitting your training data to your neural network if you are not careful. A common practice when fitting your neural network is to set aside a portion of your training data (also known as your validation data) to get an early estimate of the skill of the model. Once your model has been fully fit, using matplotlib, you can create a graph that can show how the accuracy/loss for your training data and validation data change after each epoch. 

When the validation data and training data are diverging from eachother in one way or another, this is a clear sign that your data might be overfitting on the training data. The ultimate goal when plotting the results of your neural network is to make the graphs for your validation data and training data are as similar as possible. A visualization that can accurately represent this phenomenon can be seen below. 

![](https://i.stack.imgur.com/v4sP2.png)


The closer the two graphs are, the more confident we can be that the model will not show signs of overfitting when the accuracy is calculated on the testing data. The more the two graphs diverge, the more evidence there is to suggest that the data on the training data will be way higher than that of the testing data. If a neural network is showing signs of overfitting, there are a couple ways to deal with this problem. The first is to utilize a feature of keras where you can add "Dense" neurons to your neural network with a single line of code. For instance:

“`”  model_2.add(Dropout(.2))



