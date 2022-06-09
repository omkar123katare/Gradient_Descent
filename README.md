# Gradient_Descent

There are three types of Gradient descent ( these diferences are based on the slope term in the gradient descent formula )
1. Batch Gradient Descent
2. Stochastic Gradient descent
3. mini bath gradient descent

a. The idea of gradient descent is to take repeated steps in the opposite direction of gradient of the function at the current point. ( notice the negative sign given to the slope value of the function in the formula ) 

b. Gradient descent is an optimization function. 

c. If we give a differetntiable function as an input to this function, the function returns minimum value of the function.


Actual working of gradient descent:
1. for z axis, start with any random value z1
2. find slope at z1
3. this slope value and its sign will guide us towards the next point     [ Z ₙₑₓₜ = Z ᶜᵘʳʳᵉⁿᵗ - λ * slope of function @ current point Zᶜᵘʳʳᵉⁿᵗ ] 

### Question: Why do we need to multiply the slope by λ?
### Answer:To avoid overshooting of values and delay in reaching the minimum point on the fucntion, we multiply the slope value by a factor λ. It is also called as learning rate.

Important term in the gradient descent's formula to find the minimum value of the function step by step is the slope of the function term. To find this term, we need to differentiate this term and substitute the current value of the function in order to get the next value.
So, to get best values of β for all the features, in order to obtain best fit hyperplane using gradient descent we use the gradient descent formula for all feature columns  βₙₑₓₜ =  βᶜᵘʳʳᵉⁿᵗ - λ * slope of function @ current point βᶜᵘʳʳᵉⁿᵗ .

## Deciding on learning rate and epochs:
1. If learning rate is very less, we need to have large number of epochs so as to reach the minimum point on the function.
2. If the learning rate is too high, we still need large number of epochs, because the βₙₑₓₜ value will overshoot the minimum value of the β slope value for that feature      many times before attaining the minimum value.

## 3 issues with Gradient Descent:
1. Learning Rate
2. Loss Function a) non convex function. b) saddle point.
3. Issue of data

Batch Gradient Descent vs Stochastic gradient descent vs Mini batch gradient descent
for Z ₙₑₓₜ = Z ᶜᵘʳʳᵉⁿᵗ - λ * slope of function @ current point Zᶜᵘʳʳᵉⁿᵗ :
1. In batch gradient descent, the slope term includes summation of errors for all the rows in one epoch. As we use all the rows in dataset, this makes this type of gradient descent has slowest epoch speed. So, for every epoch Z ₙₑₓₜ is updated once and the rows in the dataset are used for this.
2. In stochastic gradient descent, for each epoch, the Z ₙₑₓₜ is updated n (number of rows in the dataset) times. Unlike batch gradinet descent, in stochastic gradinet descent we dont take summation for all the rows in the dataset. We randomly choose a row in dataset and update the Z ₙₑₓₜ value n times.
3. In mini batch gradient descent, if we create 'b' batches out of total rows of dataset, there will be 'b' updates in the Z ₙₑₓₜ value in one epoch.

### Even though stochastic gradient descent takes more time for one epoch, than batch gradient descent, effectively stochastic gradient descent gives the minimum value for the function faster. So, in stochastic gradient descent solution converges in less number of epochs. Because stochastic gradient descent requires less number of epochs than batch gradient descent. Also, we dont need to load the whole dataset in the algorithm in stochastic gradient descent during vectorization beacuse in stochastic gradinet descent we randomly choose the rows instead of calculating summation term inside the slope formula for the whole dataset. 

### What are the problems with batch gradient descent?
1. Hardware requiremets:Vectorization step requires us load the whole X_train matrix at once. While updating each slope value corresponding to each feature, we need to perform above vectorizaion steps. If our dataset has millions of rows, it will be computationally very heavy. In stochastic gradinet descent, ot once only one Y_hat value and error value is calculated this solves our harware limations problem and we dont get *memory overload error*.
2. Huge amounts of calculations: For each epoch, we update each feature value only once, But while updating, we substitute the slope value for each feature. This slope value requires us to huge amounts of calculations. But by using batch gradient descent, we perform the above mathematical operations one by onr for each selected random row. Also epochs i.e the amount of calculations required to be done are lesser in stochastic gradient descent than in batch gradient descent.

### When to use stochastic gradinet descent?
1. when we have big data.
When we have large number of rows in the training data, in batch gradient descent, the slope term for each feature has sumaation term for errors of all the data points. This requires us to load the whole dataset at once. This step of vectorization is computationally very heavy. Solution to this problem is to use stochastic gradient descent. In stoachastic gradient descent, we only load one random error value out of whole dataset in each step. This makes stochastic gradient descent suitable for big data. 
2. When we have a non convex function.
If our function has multiple minima, and during gradient descent our new values enter the slope of a local minima, it not possible to come out of it and traverse towards the global minima. In such case, if we use stochastic gradient descent, in each epoch, number of updates made are equal to nuber of rows in the dataset. As the rows are chosen randomly, there is chance that the new value of variable lies away from local minima, thereby increasing chances of ultimately reaching to global minima of loss function with enough epochs.

### Learning schedule
Learning rate value is changed after every epoch if we want to reduce the random behaviour of the new values obtained after reaching near the optimal point i.e the minimum value of loss function for each feature. In order to do achieve this, we use a Learning schedule function which returns damped values for learning rate at each consequent epoch. This reduces random fluctuations in the  βₙₑₓₜ value as we reach closer to the optimal  βₙₑₓₜ value.
