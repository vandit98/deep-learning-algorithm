# Meta learning QNA

## Q1) What Is Meta-Learning?
Meta-learning is about learning how to learn. It is an ML algorithm that learns the learning of another ml algorithm.
Conventional ML (base learning) has a fixed inner learning algorithm (ie. SGD, with certain hyperparameters) that updates the network to solve the task. 
Meta-learning doesn’t have a fixed inner learning loop — instead, the inner loop is being updated by an outer algorithm.
We learn the outer algorithm throughout the episodes. These episodes could be samples from multiple tasks or a single task.
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/8486dd2b-930b-4c24-918b-a099cf1f2157)

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
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/15ba84f3-c23a-42ff-9563-aef6fa37fcde)



## Q3) Explain the below image, specifically how meta-learning is applied to a new task?
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/d2c04c80-2ca6-4c6f-b72f-a35baec38472)
we do not want to assume that every time training new tasks, we have the meta-training dataset. Then we need to compile our meta-training dataset down to a set of parameters θ. θ basically corresponds to what we need to know about the meta-training data in order to solve new tasks quickly. The likelihood of our parameters for our dataset given our past meta-training data can be re-written in a way that integrates over our meta-parameters θ. This rewriting assumes that our task-specific parameters and our meta-training data are independent conditioned on θ. We can then approximate the integral with a point estimate for our meta-parameters, where the right-hand side of the objective (logP(θ*|D_{meta-trin})) is going to correspond to meta-training, where we want to learn a set of meta-parameters given our meta-training data. And the left-hand side of the objective (logP(ϕ|D,θ*)) is going to correspond to adaptation where we want to be able to learn new parameters for a new task, given data from that task and our meta-parameters: θ*, where θ* is equal to basically argmax of log p θ given our meta-training data. So essentially this right-hand side(logP(θ*|D_{meta-trin})) is the meta-learning problem where we are optimizing over our meta-parameters such that when we use them for adaptation, we can effectively learn parameters for that task.

## Q4) Explain adaptation and how it works in detail for meta-learning.
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/daaa8247-2546-444d-af4e-cec9c467399e)

## Q5) What is the case when Hyperparameter optimization and auto-ML can also be cast as meta-learning?
It can be seen as a special case where ϕ = θ. Hyperparameter optimization and auto-ML can also be cast as meta-learning. Hyperparameter optimization 
is where θ corresponds to hyperparameters and ϕ corresponds to network weights. For architecture search, θ corresponds to architecture, and ϕ corresponds to network weights.

## Q6) What is black-box adaptation in meta-learning?
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/96c2d826-fb18-4e56-845a-fe9dba7480d2)
Black-box adaptation is an approach in meta-learning where the goal is to design a system that can quickly adapt to new tasks without explicitly modeling the underlying task distribution. The term "black box" refers to treating the task adaptation process as a black box, meaning we're not concerned with understanding the inner workings of the tasks themselves but rather focusing on finding a function that can adapt to them effectively.
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/7193379c-a9d9-431d-8814-9a34adc1d479)


## Q7) Advantages and disadvantages of black box adaptation.?
### Advantage
**Efficiency**: One of the key reasons for using black-box adaptation is efficiency. Traditional machine learning algorithms often require large amounts of labeled data for each new task in order to perform well. Black-box adaptation aims to minimize the amount of data needed for adaptation, making it more efficient and practical for real-world applications.

**Flexibility**: Black-box adaptation methods are flexible and can be applied to a wide range of tasks without needing to modify the underlying algorithm significantly. This flexibility makes them suitable for various domains and problem types.

**Expressiveness**: Black-box adaptation methods, particularly those based on neural networks, are highly expressive and can capture complex relationships between input data and task-specific parameters. This expressiveness allows them to adapt effectively to diverse tasks and datasets.

**Generalization**: By learning a general adaptation function rather than task-specific models, black-box adaptation methods can generalize well to new tasks that may differ from those seen during training. This ability to generalize is crucial for handling unseen tasks in real-world scenarios.


### Dis-advantage
The downside to this approach is in general, these neural networks are fairly complex because they need to be taking in datasets and making predictions about new data points. They essentially need to figure out how to learn from data, and they need to do this basically completely from scratch. As a result, they are often fairly data inefficient (not data inefficient at meta-test time), and they often require a large number of meta-training data and a large number of tasks in order to perform well.


## Q8) explain the working of black box adaptation?
![Screenshot from 2024-05-13 02-12-01](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/e5982de4-539c-45d4-afc4-e551b3f22b23)

If we want to do the optimization, we first sample a task or a mini-batch of tasks (step 1). Then we sample disjoint datasets from that task dataset( which are meta-training dataset of tasks instead of the training dataset), which we will refer to as D train and D test (step 2). So if we have Di, which is all of the data for the task i, then we are going to partition Di into a training dataset and a test set for task i. So particular we can basically randomly select half of them to be used for the training dataset and half of them to be used for the test set at this iteration of the algorithm. Then we will take the training dataset (Di^{tr}, which shows in the green box) to compute the task per-specific parameters ϕ i(step3). Then we will update our meta-parameters using the gradient of the objective with respect to the meta-parameters using the computed task-specific parameters (step 4). And then we will repeat this iteratively using an optimizer, such as Adam, SGD, etc.

Notably, we are not computing gradients using the training dataset. Instead, we are using the meta-training dataset of tasks. So the task-specific parameters are computed using D train, then we evaluate those parameters using the test dataset for that meta-training task.

## Q9) Why do the above nueral network approach does not seems scalable and discuss the soltution to it as well?
Notably, we are not computing gradients using the training dataset. Instead, we are using the meta-training dataset of tasks. So the task-specific parameters are computed using D train, then we evaluate those parameters using the test dataset for that meta-training task.

θ is meta parameters and ϕ are considered the task-specific parameters, which is essentially not considered part of the meta parameters. ϕ could be the parameters of an entire neural network, it could also be something that’s more compact. The challenge of black-box adaptation is that if ϕ is literally representing all the parameters of another neural network, it may not be that scalable to actually output all of those neural network parameters because neural networks can be very large.
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/61737f22-979f-488b-bbba-d272dc71d8a9)

**Solution**
You don’t need necessarily to output all of the parameters of a neural network. You could instead just output the sufficient statistics of that task such that you could effectively make predictions for that task.You could use low-dimensional vector hi for task i to represent contextual task information. Instead of having a neural network that outputs all of the parameters phi, it will output some set of sufficient statistics h. Then your new parameters Phi I corresponds to hi as well as part of theta that will parameterize g (ϕi={hi,θg})

![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/017a6afb-529c-48e9-a88f-36d49e9c5189)


## Q9) In muti-task learning we were also representing the task information via z (task descriptor) and we are using h for meta learning, how are they different ?
In multi-task learning where we were concatenating task information z into the network, you could view h (hidden state), essentially as a summarization of the task that is used to make predictions for that task. So h and z are very similar. In this case, unlike z, in the multi-task learning setting, we are actually learning the task representation h: we are learning how to produce that task representation h given a small dataset of that task.
So in summary there we are putting the task representation manually but here we are trying to learn how to represent task.

## Q10) What are permutation-invariant and permutation-variant model architecture?
In the context of machine learning, "permutation invariant" refers to the property of a model or algorithm where the order of the inputs does not affect the output. Conversely, "permutation variant" means that the output of the model or algorithm changes depending on the order of the inputs.

**Permutation Invariant:**

In the context of black-box adaptation approaches, architectures that aggregate information from inputs without considering their order are permutation invariant. For example, a neural network architecture that uses average pooling to aggregate features from different data points is permutation invariant. Regardless of the order in which the data points are presented, the resulting representation remains the same.
**Permutation Variant:**

Some neural network architectures used in black-box adaptation may be permutation variant. For instance, architectures that rely on sequential processing of data points, such as recurrent neural networks (RNNs) or models with attention mechanisms applied sequentially, can produce different outputs depending on the order of the inputs. This variation in output based on input order makes these architectures permutation variant.

## Q10) Describe meta networks and the difference between fast weight and slow weights in the meta networks.  
Source 
```
https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6519722/
```


![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/c44e49b1-c762-4325-902a-102b9ba85cf4)
MetaNet learns to fast parameterize underlying neural networks for rapid generalizations by processing a higher order meta information, resulting in a flexible AI model that can adapt to a sequence of tasks with possibly distinct input and output distributions. The model consists of two main learning modules. The meta learner is responsible for fast weight generation by operating across tasks while the base learner performs within each task by capturing the task objective. The generated fast weights are integrated into both base learner and meta learner to shift the inductive bias of the learners.The meta-learner learns from previous tasks and experiences, while the base-learner learns from the limited labeled data available for a specific task.
The meta-learner’s role is to capture the common patterns and knowledge across different tasks, enabling it to provide useful initializations or guidance to the base-learner. This initialization helps the base-learner to learn faster and more accurately with limited labeled data.
## Algorithm for MetaNet for one-shot supervised learning
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/80f07806-69fd-409d-8fd5-c10d8c265e98)
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/62af7198-bb60-46d9-bc84-2dd1848d127d)

### Training of MetaNet consists of three main procedures:
1) Acquisition of meta information
2) Generation of fast weights.
3) Optimisation of slow weights.

### Meta Learner

The meta learner consists of a dynamic representation learning function u and fast weight generation functions m and d. The function u has a representation learning objective and constructs embeddings of inputs in each task space by using task-level fast weights. The weight generation functions m and d are responsible for processing the meta information and generating the example and task-level fast weights.
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/03875595-42a2-4c9c-a22f-a7ab67c8dcc3)
The representation learning function u is a neural net parameterized by slow weights Q and task-level fast weights Q*. It uses the representation loss lossemb to capture a representation learning objective and to obtain the gradients as meta information. We generate the fast weights Q* on a per task basis as follows:
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/973c0e78-04d7-424c-b5b1-be5c5b02764c)

where d denotes a neural net parameterized by G, that accepts variable sized input. First, we sample T examples (T≤N){x′i,y′i}Ti=1![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/15264126-a667-407e-9a00-86db660855f7)
 from the support set and obtain the loss gradient as meta information. Then d observes the gradient corresponding to each sampled example and summarizes into the task specific parameters. We use LSTM for d although the order of inputs to d does not matter. Alternatively we can take summation or average of the gradients and use a MLP. However, in our preliminary experiment we observed that the latter results in a poor convergence.

![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/b1835c04-b695-4f41-84e2-994de1256f0a)
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/21baf434-3cd7-460d-a693-edb119dd16cd)

### Base Learner

The base learner, denoted as b, is a function or a neural net that estimates the main task objective via a task loss losstask. However, unlike standard neural nets, b is parameterized by slow weights W and example-level fast weights W*. The slow weights are updated via a learning algorithm during training whereas the fast weights are generated by the meta learner for every input.

The base learner uses a representation of meta information obtained by using a support set, to provide the meta learner with feedbacks about the new input task. The meta information is derived from the base learner in form of the loss gradient information:

![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/766e2b5e-66bf-4ceb-a0b9-8590cc09b908)

### Layer Augmentation

A slow weight layer in the base learner is extended with its corresponding fast weights for rapid generalization. An example of the layer augmentation approach applied to a MLP is shown in Figure 2. The input of an augmented layer is first transformed by both slow and fast weights and then passed through a non-linearity (i.e. ReLU) resulting in two separate activation vectors. Finally the activation vectors are aggregated by an element-wise vector addition. For the last softmax layer, we first aggregate two transformed inputs and then normalize for classification output.
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/c82ca29d-00ce-45dc-9753-09cbaaa4e2f7)

Intuitively, the fast and slow weights in the layer augmented neural net can be seen as feature detectors operating in two distinct numeric domains. The application of the non-linearity maps them into the same domain, which is [0,∞) in the case of ReLU so that the activations can be aggregated and processed further. Our aggregation function here is element-wise sum.

Although it is possible to define the base learner with only fast weights, in our preliminary experiment we found that the integration of both slow and fast weights with the layer augmentation approach is essential in convergence of MetaNet models. A MetaNet model relying on a base leaner with only fast weights were failed to converge and the best performance of this model was reported to be as equal as that of a constant classifier that assigns the same label to every input.

**Fast weights vs slow weights**

task-specific parameters as fast weights and the meta parameters as slow weights. Because one of them is updated much more quickly than the other one.


## Q11) What is Ml-MANN(Meta Learning with Memory Augmented Neural Networks) ?
source 
```
https://arxiv.org/pdf/1605.06065
```
Good Read 
```
https://medium.com/the-ai-team/memory-augmented-neural-network-for-meta-learning-case-study-56af9cc81ae2
```
Memory Augmented Neural Network is one of novel architectures to do meta learning which inspired the use of external memory from Neural Turing Machine.
### MANN contains three major parts.
1. Controller Network
2. External Memory Module
3. Read — Write Heads.

### Controller Network
The Controller Network is the either LSTM or feed forward network for prediction. Since the input for the Network is a sequence of data, it is preferable to use an RNN or LSTM. As a note, **remember that the External Memory module of MANN is not the memory cell in LSTM.**The controller interacts with an external memory module using read and write heads, which act to retrieve representations
from memory or place them into memory, respectively.

### External Memory Module and Read Write Heads
The External Memory Module is basically a matrix which retains the memory of important parameters from one task to the other. The communication between Memory Module and the Controller Network is done by the Read Write Heads where while reading, the representations from memory is retrieved and while writing, a new memory is encoded. The governing equations of the reading and writing processes are as follows:
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/4013b89e-a177-4cc4-9f51-81cb50ac7103)

For each input, the memory matrix is updated based on the usage weight and previously read vector (eqn 7). The retrieved memory is then concatenated with the input vector and fed through the Controller Network. The controller network parameters (weights and biases) is then updated by Gradient Descent carried out by the preferred optimization function minimizing the Categorical Cross Entropy.
![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/ec2521dc-3911-4fdf-83e4-b9a45d714416)

![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/bedaf3df-4766-4a1b-8499-ec89f127e214)
Task structure. (a) Omniglot images (or x-values for regression), xt, are presented with time-offset labels (or function values),
yt−1, to prevent the network from simply mapping the class labels to the output. From episode to episode, the classes to be presented
in the episode, their associated labels, and the specific samples are all shuffled. 

![image](https://github.com/vandit98/deep-learning-algorithm/assets/91458535/14e2ca7e-9040-4312-bd33-b8091b049797)

(b) A successful strategy would involve the use of an external memory to store bound sample representation-class label information, which can then be retrieved at a later point for successful classification when a sample from an already-seen class is presented. Specifically, sample data xt from a particular time step should be bound to the appropriate class label yt, which is presented in the subsequent time step. Later, when a sample from this same class is seen, it should retrieve this bound information from the external memory to make a prediction. Backpropagated error signals from this prediction step will then shape the weight updates from the earlier steps in order to promote this binding strategy.



