
## what are the limitations of sigmoid and its advantage?
### Advantages

#### Output Range:

The sigmoid function outputs values in the range (0, 1). This is particularly useful in binary classification problems where the output needs to represent probabilities. The output can be interpreted as the probability of belonging to the positive class.

#### Smooth Gradient:

The sigmoid function has a smooth gradient, which is crucial for optimization algorithms (like gradient descent) to converge efficiently. This smoothness makes it well-suited for use in gradient-based optimization algorithms.
### Limiitations

#### Vanishing Gradient Problem:

The sigmoid function tends to squash input values to extreme outputs (close to 0 or 1). During backpropagation, when calculating gradients for weight updates, the gradients in the early layers can become extremely small. This can lead to the "vanishing gradient problem," where the network has difficulty learning in the early layers.

#### Output Not Centered Around Zero:


Being zero centric  helps optimization algorithms converge faster because it reduces the risk of weights being updated in one direction significantly more than in another.

#### Saturation and Kill Neurons:  

Neurons that always output the same value (near 0 or 1) are referred to as "dead neurons" as they no longer contribute to the learning.

#### Not Well-suited for Deep Networks:
same if in between we have dead nueron in hidden layer it can hnder with the training.



### RElu vs sigmoid vs tanh?
#### Sigmoid:

Range: Outputs values in the range (0, 1).

Zero-Centered: No, not zero-centered.

Advantages:

Suitable for binary classification problems where the output needs to represent probabilities.

Smooth gradient, which is beneficial for optimization algorithms.

Disadvantages:

Prone to vanishing gradient problem, especially in deep networks.

Not zero-centered, which can affect optimization dynamics.
#### Tanh (Hyperbolic Tangent):

Range: Outputs values in the range (-1, 1).

Zero-Centered: Yes, zero-centered around the origin.

Advantages:

Zero-centeredness helps mitigate vanishing gradient problems.

Smooth gradient for efficient optimization.

Broader output range compared to sigmoid.

Disadvantages:

Still susceptible to vanishing gradient, although less severe than sigmoid.

### ReLU (Rectified Linear Unit):

Range: Outputs the input for positive values, and zero for negative values.

Zero-Centered: No, not zero-centered.

Advantages:
Fast and computationally efficient due to simplicity.

Mitigates vanishing gradient problem for positive inputs.

Promotes sparsity, leading to more efficient representations.

Disadvantages:

Not zero-centered, which may lead to issues in optimization, especially for certain types of networks.

Can suffer from the "dying ReLU" problem, where neurons may become inactive during training and stop learning.