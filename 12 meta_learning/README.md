# Meta learning QNA

## Q1) What Is Meta-Learning?
Meta-learning is about learning how to learn. It is an ML algorithm that learns the learning of another ml algorithm.
Conventional ML (base learning) has a fixed inner learning algorithm (ie. SGD, with certain hyperparameters) that updates the network to solve the task. 
Meta-learning doesn’t have a fixed inner learning loop — instead, the inner loop is being updated by an outer algorithm.
We learn the outer algorithm throughout the episodes. These episodes could be samples from multiple tasks or a single task.

### good source
```
https://medium.com/geekculture/an-introduction-to-meta-learning-b328ada3b27f
```
### These are the different parts of a meta-learning algorithm.
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/bfe93b05-eada-46cb-9f7b-a1c3de833687)
