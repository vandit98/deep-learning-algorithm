# Meta learning QNA

## Q1) What Is Meta-Learning?
Meta-learning is about learning how to learn. It is an ML algorithm that learns the learning of another ml algorithm.
Conventional ML (base learning) has a fixed inner learning algorithm (ie. SGD, with certain hyperparameters) that updates the network to solve the task. 
Meta-learning doesn’t have a fixed inner learning loop — instead, the inner loop is being updated by an outer algorithm.
We learn the outer algorithm throughout the episodes. These episodes could be samples from multiple tasks or a single task.

### good source
```
https://medium.com/@rachel_95942/multi-task-meta-learning-basics-259abe7a868
```
### These are the different parts of a meta-learning algorithm.
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/bfe93b05-eada-46cb-9f7b-a1c3de833687)

## q2) Explain the mechanistic view and probabilistic view for meta-learning.

### Mechanistic View 
A deep neural network model can read an entire dataset and make predictions for new data points. Training this network uses a meta-data set, which itself consists of many datasets, each for a different task. This view makes it easier to implement meta-learning algorithms.
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/b1c6787e-b007-4820-aa3d-e5af6d7466a6)

### Probabilistic View
With regard to the probabilistic view, extracting prior information from a set of (meta-training) tasks allows efficient learning of new tasks. Leaning a new task uses this prior and (small) training set to infer the most likely posterior parameters. This view makes it easier to understand meta-learning algorithms.
![Uploading image.png…]()

## Q3) Explain the below image, specifically how meta-learning is applied to a new task?
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/d2c04c80-2ca6-4c6f-b72f-a35baec38472)
we do not want to assume that every time training new tasks, we have the meta-training dataset. Then we need to compile our meta-training dataset down to a set of parameters θ. θ basically corresponds to what we need to know about the meta-training data in order to solve new tasks quickly. The likelihood of our parameters for our dataset given our past meta-training data can be re-written in a way that integrates over our meta-parameters θ. This rewriting assumes that our task-specific parameters and our meta-training data are independent conditioned on θ. We can then approximate the integral with a point estimate for our meta-parameters, where the right-hand side of the objective (logP(θ*|D_{meta-trin})) is going to correspond to meta-training, where we want to learn a set of meta-parameters given our meta-training data. And the left-hand side of the objective (logP(ϕ|D,θ*)) is going to correspond to adaptation where we want to be able to learn new parameters for a new task, given data from that task and our meta-parameters: θ*, where θ* is equal to basically argmax of log p θ given our meta-training data. So essentially this right-hand side(logP(θ*|D_{meta-trin})) is the meta-learning problem where we are optimizing over our meta-parameters such that when we use them for adaptation, we can effectively learn parameters for that task.

## Q4) Explain adaptation and how it works in detail for meta-learning.
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/daaa8247-2546-444d-af4e-cec9c467399e)

## Q5) What is the case when Hyperparameter optimization and auto-ML can also be cast as meta-learning ?
It can be seen as a special case where ϕ = θ. Hyperparameter optimization and auto-ML can also be cast as meta-learning. Hyperparameter optimization is where θ corresponds to hyperparameters and ϕ corresponds to network weights. For architecture search, θ corresponds to architecture, and ϕ corresponds to network weights.



