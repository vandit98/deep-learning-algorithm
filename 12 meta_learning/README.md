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

### Probabilistic View
With regard to the probabilistic view, extracting prior information from a set of (meta-training) tasks allows efficient learning of new tasks. Leaning a new task uses this prior and (small) training set to infer the most likely posterior parameters. This view makes it easier to understand meta-learning algorithms.
