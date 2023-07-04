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

By looking at graph we users can easily tell where a minima is and can define its coordinates. But we won't be searching for the minima in the graphs and providing it to the algorithm, instead, we will find a so that the algorithm itself finds the minima and assign the values to w and b, so that our model will be fully prepared for making predictions.

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