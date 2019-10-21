# DeepUQ
## Bayesian Uncertainty Quantification with Deep Generative Models

Notebooks and trained models to reproduce the posterior analysis of all examples shown in the publication
*Uncertainty Quantification with Generative Models*
(accepted to Bayesian Deep Learning, NeurIPS 2019 Workshop).

### What is DeepUQ?
DeepUQ is a generative model based approach for reconstructing uncorrupted data from corrupted data. In addition to providing a best guess (maximum a posteriori estimate) of the uncorrupted data, DeepUQ provides an uncertainty quantification of the reconstruction.

### A reconstruction example:

As an example we take an image from the test data set (left panel), corrupt it by adding noise and masking half of it (middle panel). We then run our reconstruction method to find the most likely uncorrupted image given the corrupted image and our generative model (right panel). 

![recon_example](/plots/4README/maskedNoise.png)

### How does is work?

We train a generative model on an uncorrupted data set (e.g. a Variational AutoEncoder). The latent space dimensionality of the generative model can generally be chosen to be much smaller than the dimensionality of the data space and we enforce the distribution of the latent space variables to be Gaussian. Once the generative model is trained, we can write down the posterior for corrupted images in latent space, find its maximum, fit the posterior distribution and draw samples from the fit. Points in the latent space can then be visualized by passing them through the generative model. A much more detailed description of the method can be found in the paper.

As an example, let's consider corrupted data in the form of a masked 4 (same 4 as in the example above):

![masked_4](/plots/4README/masked4.png)

The posterior in latent space is bimodal corresponding to 4s and 9s which are both compatible with the input data. We fit it with a mixture of Gaussians and draw samples from them:     
![posterior_example](/plots/4README/posterior_samples.png)

We can then visualize these samples by forward modeling them to data space:    
![samples](/plots/4README/fwdmodeled_samples.png)

This gives us an estimate of the uncertainty of our reconstruction.

### How to use this repo?
The notebooks should be ready to plug and play (preferantially on a GPU). The module folder contains our pretrained generative model that the notebooks need to access. Each notebook contains essentially the same code but operates on a different data corruption example. We have added detailed comments to one of the notebooks ([here](https://github.com/bccp/DeepUQ/blob/master/notebooks/ImageCorruptionMNIST_masknoise05_SVI.ipynb)).

### Contributors
Vanessa Böhm, François Lanusse, Uroš Seljak

### References
Posterior Analysis:  
https://arxiv.org/abs/1901.04454   
Variational AutoEncoders (VAE):   
https://arxiv.org/abs/1401.4082  
https://arxiv.org/abs/1312.6114  
Dataset:  
http://yann.lecun.com/exdb/mnist/

### Requirements
tensorflow 1.15.0  
tensorflow-probability 0.7.0  
tensorflow-hub 0.6.0
