# What is Machine Learning?

According to Arthur Samuel, machine learning is a field of study that gives computers the ability to learn without being explicitly programmed.

## Types of Machine Learning Algorithms:-
    
- Supervised Learning
- Unsupervised Learning
- Recommender Systems
- Reinforcement Learning

## 1) Supervised Learning :- 

It is the most used learning alogrithm in real-world applications. In this learning, the algorithms learn x -> y or input to output mappings. It learns from data labelled with the "Right Answers". 

Two major types of Machine learning are as follows,

- Regression, Mapping a function y = f(x) such that maximum points of data are covered and an output can be predicted from the given curve. It predicts a number from infinitely many possible output numbers. 

- Classification, Predicts Categories from a small number of possible outputs. They don't have to be numbers, they can be non-numeric.

## 2) Unsupervised Learning :- 

Data only comes with inputs x, but not with output labels y. Algorithm has to find structure in the data. It finds something interesting in the unlabelled data.

Types of Unsupervised learning,

- Clustering, it processes the unlabelled data into different clusters. Groups similar data points.

- Anomaly detection, Find unusual data points.

- Dimensionality reduction, Compress data using fewer numbers.

#
## Linear Regression :- 

It is a regression algorithm in which the function turns out be a line function and the output is calculated on the line.

Training set contains features as well as targets, features as inputs and targets as required outputs.
This training set is then given to a learning algorithm that gives out a function (f), Note: this function is called hypothesis in machine learning terms.
This hypothesis or function is given a test input x which then producess an estimate output y^ (y-hat or y-bar). Note: y^ (y-hat or y-bar) is an estimate of y.

### How to represent f?

In linear regression f is a line function so,

fw,b(x) = wx + b

can also be written as,

f(x) = wx + b

![Alt text](<md_images/Screenshot from 2023-06-27 16-14-41.png>)
    
Linear regression works with one variable only.

To find the line which gives us the best values for w and b which in turn helps generating the closest output estimate towards target output, we need to define a cost function.
To compute this equation we find the average of squared error for all the given training examples.

![Alt text](<md_images/Screenshot from 2023-06-28 11-33-05.png>)

where, 
- J(w,b)  -> is the cost function, also called Squared error cost function
- w       -> slope of the line
- b       -> y-intercept of the line
- m       -> no. of training examples
- i       -> index
- y^      -> estimate output from model at a given pair of w and b.
- y       -> target output for the model

It is observed that the value of parameters w and b at which the cost function is at the minimum, best fits the line with the training data. So it is recommended to find such values by finding the minimum value of J or cost function.

To find the minimum value of cost function, we need to plot a graph with cost function , w and b values and find the minimum of the plot.

To do so, we learnt about contour plot which was able to plot the minimum of the cost function but with cost function and w or b only. Since it is a 2D graph.

So, we move on to plotting a 3D plot using cost function values, w and b altogether which is known as surface plot. Using this we were easily able to spot the local minima's. Note: Since our cost function is squared erros cost function, it will result in shape of bowl when plotted and thus there will only be one minima which will be the global minima.

### Gradient Descent...

By looking at graph we users can easily tell where a minima is and can define its coordinates. But we won't be searching for the minima in the graphs and providing it to the algorithm, instead, we will find a way so that the algorithm itself finds the minima and assign the values to w and b, so that our model will be fully prepared for making predictions.

To do so, we will use a concept called Gradient Descent. Gradient Descent helps our algorithm by moving some steps from a starting point on the surface plot to the local minima. It does so by first checking 360 degrees for the next step which will lead to values of w and b where the cost reduces and it will take a step in that direction and repeat the same process untill it finds the minima.

To compute it, we have a formula that will allow algorithm to find such values of w and b.

![Alt text](<md_images/Screenshot from 2023-07-04 14-14-49.png>)

where, 

- alpha is the learning rate
- multiple part of alpha is partial derivative of the cost function, basically slope of the function.

Note: these values must be updated in the algorithm simultaneously so that the cost function updates only when both w and b are updated. So the correct method to do so is, 

![Alt text](<md_images/Screenshot from 2023-07-04 14-22-58.png>)

This method of storing values of w and b will make sure that the same cost function with previous values is being passed in the second line of code where temp_b is calculated and the value of b is unhampered by passing the cost function with only the updated value of w, which might give but results but is an incorrect way of doing so.

This method will update the values of w and b so in such a way that the new value of w and b will result in a lower cost. To help you visulaize how this function helps the algorithm to do so, recall that in these steps of updation we are taking partial derivative of cost function with respect to only one parameter at a time. Which is nothing but the slope of the curve between cost function and a single parameter. Below is the curve shown, 

![Alt text](<md_images/Screenshot from 2023-07-04 14-34-11.png>)

According to this curve when we take the slope at a point, it will either be positive or negative. Now replacing the slope in the equations above we find that the value of the parameter (here, in diagram w) changes according to the slope and the new value is closer to the minima. See in the diagram, 

![Alt text](<md_images/Screenshot from 2023-07-04 14-38-51.png>)

Similarly equation of updation for b results in similar graph with b as the parameter and it also changes according to the slope and results in the value where the minima of cost is.

The result of the derivative will look like this,

![Alt text](<md_images/Screenshot from 2023-07-04 16-24-25.png>)

Note: 
- alpha ranges between 0 and 1. Keeping alpha too large will end up in loosing the minima and diverge instead of converging at the minima. 
- Keeping alpha too small will make our updations very minimal and thus our model will take much higher time to find the correct values of parameters. 
- And also note that since alpha is multiplied with the slope, as the function moves towards the minima, the slope will reduce resulting in smaller and smaller values of updation after multiplying with alpha. 

So decide a value of alpha keeping these three points in mind.

### Wrapping Up...

So finally, this ensures that the algorithm when given a starting point (i.e. with coordinates of w and b) will automatically find the values of w and b where the cost is the minimum and since, as mentioned earlier, we are using Squared error cost function our minima will only be at a single point.
Thus making our model ready to predict outputs for any input, seems like its ready to face the world ;)

#
## Multiple Linear Regression :-

In Linear Regression, we studied about model which can predict output bsaed on only single parameter i.e size of the flat. Multiple Linear Regression focusses on more details than just only a single parameter to predict more accurate results. For example, let's take into consideration the number of bedrooms, the number of floors and how old the property is also with the size of the property. So in this case, we'll be having 4 features to work on instead of one.

![Alt text](<md_images/Screenshot from 2023-07-07 17-49-22.png>)

So, now the definition of the function changes a little as now we have vector form for w i.e. parameters and x i.e. features.

![Alt text](<md_images/Screenshot from 2023-07-12 17-03-45.png>)

Since it is of the form of linear regression itself, but with multiple variables, Thus it is called multiple linear regression.

### Vectorization

Now that we have vecotrs to deal with in our code and since our data, parameters and features can be extremely large, to handle it, we have a convenient way using NumPy, a famous python library to deal with vectorization.

![Alt text](<md_images/Screenshot from 2023-07-12 17-23-02.png>)

NumPy is able to use parallel hardware in a normal computer and thus achieves faster calculations.

### Feature Scaling 

For a gradient descent aproach it is necessary to have more normalised plots so that the changing of the values to find the local minima occurs efficiently and does not converge. To do that we use the technique of Feature Scaling.

The following image shows the relation between the feature and the parameter sizes.

![Alt text](<md_images/Screenshot from 2023-08-01 13-02-52.png>)

You might see a contour plot where the horizontal axis has a much narrower range, say between zero and one, whereas the vertical axis takes on much larger values, say between 10 and 100. So the contours form ovals or ellipses and they're short on one side and longer on the other. And this is because a very small change to w1 can have a very large impact on the estimated price and that's a very large impact on the cost J. Because w1 tends to be multiplied by a very large number, the size and square feet. In contrast, it takes a much larger change in w2 in order to change the predictions much. And thus small changes to w2, don't change the cost function nearly as much. So where does this leave us? This is what might end up happening if you were to run gradient descent, if you were to use your training data as is. Because the contours are so tall and skinny gradient descent may end up bouncing back and forth for a long time before it can finally find its way to the global minimum. 

So, in situations like this, a useful thing to do is to scale the features. This means performing some transformation of your training data so that x1 say might now range from 0 to 1 and x2 might also range from 0 to 1. So the data points now look more like this and you might notice that the scale of the plot on the bottom is now quite different than the one on top.

![Alt text](<md_images/Screenshot from 2023-08-01 13-10-16.png>)

Now, after the re scale, x1 and x2 are both now taking comparable ranges of values to each other. And if you run gradient descent on a cost function to find on this, re scaled x1 and x2 using this transformed data, then the contours will look more like this more like circles and less tall and skinny. And gradient descent can find a much more direct path to the global minimum.

Now, How to perform feature scaling?

1. Feature scaling by dividing

Well it means, if x_1 ranges from 3-2,000, one way to get a scale version of x_1 is to take each original x1_ value and divide by 2,000, the maximum of the range. The scale x_1 will range from 0.15 up to one. Similarly, since x_2 ranges from 0-5, you can calculate a scale version of x_2 by taking each original x_2 and dividing by five, which is again the maximum. So the scale is x_2 will now range from 0-1. If you plot the scale to x_1 and x_2 on a graph, it might look like this. 

![Alt text](<md_images/Screenshot from 2023-08-01 13-14-25.png>)

2. Mean Normalization

What this looks like is, you start with the original features and then you re-scale them so that both of them are centered around zero. To calculate the mean normalization of x_1, first find the average, also called the mean of x_1 on your training set, and let's call this mean Mu_1. For example, you may find that the average of feature 1, Mu_1 is 600 square feet. Let's take each x_1, subtract the mean Mu_1, and then let's divide by the difference 2,000 minus 300, where 2,000 is the maximum and 300 the minimum, and if you do this, you get the normalized x_1 to range from negative 0.18-0.82. Similarly, to mean normalized x_2, you can calculate the average of feature 2. For instance, Mu_2 may be 2.3. Then you can take each x_2, subtract Mu_2 and divide by 5 minus 0. Again, the max 5 minus the mean, which is 0. The mean normalized x_2 now ranges from negative 0.46-0 54. If you plot the training data using the mean normalized x_1 and x_2, it might look like this. 

![Alt text](<md_images/Screenshot from 2023-08-01 13-21-39.png>)

3. Z-Score Normalization

To implement a Z-score normalization, you first calculate the mean Mu, as well as the standard deviation, which is often denoted by the lowercase Greek alphabet Sigma of each feature. For instance, maybe feature 1 has a standard deviation of 450 and mean 600, then to Z-score normalize x_1, take each x_1, subtract Mu_1, and then divide by the standard deviation, which I'm going to denote as Sigma 1. What you may find is that the Z-score normalized x_1 now ranges from negative 0.67-3.1. Similarly, if you calculate the second features standard deviation to be 1.4 and mean to be 2.3, then you can compute x_2 minus Mu_2 divided by Sigma_2, and in this case, the Z-score normalized by x_2 might now range from negative 1.6-1.9. If you plot the training data on the normalized x_1 and x_2 on a graph, it might look like this. 

![Alt text](<md_images/Screenshot from 2023-08-01 13-29-46.png>)

### Feature Engineering 

Using intuition and knowledge to design new features, by transforming or combining original features is nothing but feature engineering.