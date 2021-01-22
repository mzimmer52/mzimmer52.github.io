---
layout: post
title:      "Running Feature Transformations on New Data"
date:       2021-01-22 08:59:44 -0500
permalink:  running_feature_transformations_on_new_data
---


![](https://miro.medium.com/max/3840/1*sbmnCl9NzDPeyWP-Aw506w.jpeg)


One of the biggest skills a data scientist needs to harness is the ability to transform training data/make new features to make specific machine learning models work to the best of their ability. Most of the work in fitting a model to data comes in the form of preprocessing the data before new models are trained on it. An issue that some people may run into is needing to manually do everything they did to their training data on new unseen data that they need to make predictions on. To make matters more complicated, if you are making dummy variables and there is unfamiliar pieces of data in the test/training data, it will be impossible to fit your model on the new data. Thankfully, there are easy solutions to both of these problems. 


Concerning running feature transformations on new unfamilar data, I decided to fix this problem using the "pipe" function in pandas. This function is able to run specific functions on new datasets without the need to do everything manually. For instance, for one column in the Tanzania Waterpump Dataset, there was a specific column where assigned the value 0 to every value that was 0, and assigned the value for 1 for everything else that wasn't zero. I then created a function of this simple transformation, making sure to return the new dataset at the end of the function. Once all my functions had been made concerning my feauture transformations, I used pipe to transform my entire dataset with one line of code. This line of code looked something like this:

X_final = X.pipe(add_tsh).pipe(gov_funding).pipe(installer).pipe(public_fill).pipe(permit_fill).pipe(filt, feature_list = features).pipe(dummies)

For each new function used, another pipe function would be added. Once this function is established, any new dataset that is needed to make predictions on can be replaced with "X" in the very beginning of the code, and the your data will be transformed instantly. 

Lets say you had a training dataset with the values "panda", "dog", and "cat" in one dataset, however, the testing set only had the values "dog" and "cat". If you chose to make dummy variables from both of your datasets, you would be unable to use your model trained on your training dataset on your new test data because there would be a different number of columns. Recall that pd.get_dummies will make new columns for each unique variable depending on whether or not you are using the drop_first parameter. If you use the pipe function but then run into this issue when running your model on the new data, there is a simple way to solve this. In the example above, assuming you kept all the columns, you would have three columns and only two columns in the testing dataset. In order to give the testing data and extra column, you could use the pandas "align" function to perfectly align these two datasets. While you may input different parameters for different situations, my code using the "align" function looked something like this:


X_train2, X_test2 = X_final.align(X_test2, join = "left", fill_value = 0, axis = 1)


After this line of code is run, X_train2 and X_test2 end up having the same number of columns, making it now possible to run the same model trained on the training data on the testing data to determine how well the model really works on unfamiliar, unseen data. 


With the amount of work done in the preprocessing stage before fitting models to your data, it would be a shame to need to do all of the work again on unseen data that hasn't been through the data transformation stage yet. This is why it is smart to make functions along the way for every data transformation, and then use the pipe function to instantly apply these transformations to data that hasn't been cleaned up yet. Using the align function is also a great complement to this technique, as there might be categorical variables that weren't accounted for in either the testing or training data. I hope this can serve to help anyone set out to embark on their journey to learn machine learning/data science. 








