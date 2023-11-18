## Main limitation of rnn?


__Vanishing Gradient Problem:__

The vanishing gradient problem occurs during backpropagation through time in RNNs, where gradients diminish exponentially as they are propagated backward through the network(BPTT __backpropogation_through_time__). This makes it challenging for the model to effectively learn and capture dependencies that span a large number of time steps.

__Difficulty in Capturing Long-Term Dependencies:__

Basic RNNs struggle to capture long-term dependencies in sequences. The information from early time steps may not effectively propagate to later time steps, limiting the model's ability to learn relationships that extend over a significant period.



## Summarise the working of rnn?

### Forward pass
In it the first initialised weights (input weights,hidden_satate weights,output_state weights)  and biases(output_bias,previous hidden state bias) keep same and we calculate the output

### Keep the loss calulated

for each output in the forward pass we keep the hold of the output and then finally calulate the loss i.e summ of each individual loss.

### Backward propogation through time

#### Calculate the derivativea and gradients
Then we update the weights through way back from time=t to time=1


### Repeat above until loss is reducing i.e model is learning


