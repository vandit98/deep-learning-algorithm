# Possible Questions

## 1) What are the differences in terms of the number of updates to model parameters during 10 epochs when using stochastic gradient descent (SGD), mini-batch gradient descent, and batch gradient descent, and how does the choice of algorithm impact the training process over these 10 epochs?


<!--  make it bold -->
 #### Batch Gradient Descent:( vanilla gradient descent )

-> In batch gradient descent, the entire training dataset is used to compute the gradient of the cost function with respect to the model parameters. 

-> The model parameters are updated once per epoch (a full pass through the entire training dataset). 

-> 10 epochs -10 times parameter update 

#### Stochastic Gradient Descent (SGD):

-> In stochastic gradient descent, the model parameters are updated after each individual training example.
it's called "stochastic" because the updates are noisy and can fluctuate based on the randomness inherent in using individual data points.    

-> 10 epoch- X.size()*(10)

#### Mini-Batch Gradient Descent:

-> Mini-batch gradient descent strikes a balance between batch and stochastic gradient descent. It divides the training dataset into small batches (typically of size 32, 64, 128, etc.), and the model parameters are updated after processing each mini-batch.  

-> 10 epochs - (x.size()/batch_size)*10


![Alt text](image.png)



## 2) why does stochastic gradient has high variance?

#### Noisy Updates:

SGD computes the gradient and updates the model parameters for each individual training example. Since each example is a small, random sample from the entire dataset, the updates can be noisy and fluctuate significantly. This noise introduces variance in the optimization process.

#### Randomness in Data Ordering:

The order in which training examples are presented to the algorithm is typically randomized in each epoch. This random ordering introduces additional variability in the updates, as the model parameters are adjusted based on different subsets of the data in each epoch.

#### Impact of Outliers:

Individual training examples, especially outliers, can have a more pronounced effect on the updates in SGD. If a particular example has an unusually large gradient, it can lead to a substantial update in the model parameters, introducing variance in the optimization process.

#### Convergence Path Fluctuations:

The path taken by the optimization algorithm to reach the minimum of the cost function can vary between different runs due to the random selection of individual examples. This variability in the convergence path contributes to the overall high variance.


