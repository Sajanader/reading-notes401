# read_13
## Linear regression
You know that linear regression is a popular technique and you might as well seen the mathematical equation of linear regression. But do you know how to implement a linear regression in Python?? If so don’t read this post because this post is all about implementing linear regression in Python. There are several ways in which you can do that, you can do linear regression using numpy, scipy, stats model and sckit learn. But in this post I am going to use scikit learn to perform linear regression.

## Scikit-learn
 is a powerful Python module for machine learning. It contains function for regression, classification, clustering, model selection and dimensionality reduction. Today, I will explore the sklearn.linear_model module which contains “methods intended for regression in which the target value is expected to be a linear combination of the input variables”.

* Exploring Boston Housing Data Set
The first step is to import the required Python libraries into Ipython Notebook.

![image](https://bigdata-madesimple.com/wp-content/uploads/2016/04/Explore-1.png)

* This data set is available in sklearn Python module, so I will access it using scikitlearn. I am going to import Boston data set into Ipython notebook and store it in a variable called boston.
![image](https://bigdata-madesimple.com/wp-content/uploads/2016/04/sklearn.png)

* The object boston is a dictionary, so you can explore the keys of this dictionary.

![image](https://bigdata-madesimple.com/wp-content/uploads/2016/04/boston-keys.png)

* I am going to print the feature names of boston data set.
![image](https://bigdata-madesimple.com/wp-content/uploads/2016/04/boston-features.png)

* I will see the description of this data set to know more about it. In this data set I have 506 instances(rows) and 13 attributes or parameters(columns). The goal of this exercise is to predict the housing prices in boston region using the features given.

![image](https://bigdata-madesimple.com/wp-content/uploads/2016/04/boston-description.png)

* I am going to convert boston.data into a pandas data frame.
![imag](https://bigdata-madesimple.com/wp-content/uploads/2016/04/Pandas-DataFrame.png)

* boston.target contains the housing prices.

![umage](https://bigdata-madesimple.com/wp-content/uploads/2016/04/Boston-target.png)

* I am going to add these target prices to the bos data frame.
![image](https://bigdata-madesimple.com/wp-content/uploads/2016/04/RAD.png)
