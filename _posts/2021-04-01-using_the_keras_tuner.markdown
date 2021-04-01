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

 `for i in range(hp.Int("first layer", min_value = 0, max_value = 3)):
    model.add(layers.Dense(hp.Choice(f"layer {i} features", [32, 64, 128, 256, 512]), activation='relu'))`
		
		
We are giving the keras option to either 0 or 3 of the above lines of code. Each line of code is going to be adding a Dense Layer to our neural network, with possible "node" values of 32, 64, 128, 256, or 512. What is unique about this method is that if there are other layers already below this line of code, the algorithm might actually decide that the model is better off without any of these layers, with a best value of 0 for i.  It should also be note that as well a changing the number of nodes in each feature, we can also provide different options for the activation function or the learning rate. 

![](https://cdn.corporatefinanceinstitute.com/assets/combination.jpeg)

As with any algorithm that runs an exhaustive search through every possible combination of hyperparameters, it is extremely important that you are aware of the time it may take to execute. What I would strongly advise anyone looking to utilize the Keras Tuner in their next machine learning project to do would be to run the tuner in a Google Collab notebook. Not only can you utilize Googles powerful gpu, but it can also take a lot of stress off of your local machine. Not to mention, you can models in Google Collab overnight, and even days for a time if you purchase Google Collab Pro. 

As with any machine learning model, you need to be sure that your parameters are the best they can be. Utilizing the Keras Tuner can not only help you determine the ideal amount of nodes in each layer, but also tell you if there are some layers that shouldn't even be included! I hope this helped highlight some of the major advantages of using the Keras Tuner, and how it can directly help you increase the performance of your next machine learning model. 
	
	
	
	
	
	
	
	
