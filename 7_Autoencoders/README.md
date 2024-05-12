## Q1) Are autoencoders supervised,unsupervised or semi-supervised?
Autoencoders are considered an unsupervised learning technique since they don’t need explicit labels to train on. But to be more precise they are __self-supervised__ because they generate their own labels from the training data.

## Q2) Define denoising of the auto encoders?

Keeping the code layer small forced our autoencoder to learn an intelligent representation of the data. There is another way to force the autoencoder to learn useful features, which is adding random noise to its inputs and making it recover the original noise-free data. This way the autoencoder can’t simply copy the input to its output because the input also contains random noise. We are asking it to subtract the noise and produce the underlying meaningful data. This is called a denoising autoencoder.

 We add random Gaussian noise to them and the noisy data becomes the input to the autoencoder. The autoencoder doesn’t see the original image at all. But then we expect the autoencoder to regenerate the noise-free original image.


 ## Q3) Whata are sparse autoencoders?

 We introduced two ways to force the autoencoder to learn useful features: keeping the code size small and denoising autoencoders. The third method is using regularization. We can regularize the autoencoder by using a sparsity constraint such that only a fraction of the nodes would have nonzero values, called active nodes.

In particular, we add a penalty term to the loss function such that only a fraction of the nodes become active. This forces the autoencoder to represent each input as a combination of small number of nodes, and demands it to discover interesting structure in the data. This method works even if the code size is large, since only a small subset of the nodes will be active at any time.


## Q4)  what are the use case of autoencoders?

__Data denoising__

__Dimentionality Reduction__
: visualizing high-dimensional data is challenging. t-SNE is the most commonly used method but struggles with large number of dimensions (typically above 32). So autoencoders are used as a preprocessing step to reduce the dimensionality, and this compressed representation is used by t-SNE to visualize the data in 2D space. 


## Q5) What are the cases when Autoencoder fails to learn anythin useful ?
1) Capacity of encoder.decoder f/g is too high. Capacity conrolled by depth.
2) hidden code _h_ has dimension equal to input x.
3) Overcomplete case: where hidden code h has dimension greater than input x
Even a linear encoder/decoder can learn to copy input to output without learning anything useful about data distribution.

## Q6) What are VAE (Variational Autoencoder) ?
In a nutshell, a VAE is an autoencoder whose encodings distribution is regularised during the training in order to ensure that its latent space has good properties allowing us to generate some new data. Moreover, the term “variational” comes from the close relation there is between the regularisation and the variational inference method in statistics.
A variational autoencoder can be defined as being an autoencoder whose training is regularised to avoid overfitting and ensure that the latent space has good properties that enable generative process.

Good Source
```
https://towardsdatascience.com/understanding-variational-autoencoders-vaes-f70510919f73
```
