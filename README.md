# DeepUQ
Bayesian Uncertainty Quantification with Deep Generative Models

Notebooks and trained models to reproduce the posterior analysis of all examples shown in  
Vanessa Böhm, François Lanusse, Uroš Seljak: *Uncertainty Quantification with Generative Models*  
(accepted to Bayesian Deep Learning, NeurIPS 2019 Workshop).

### What is DeepUQ?
DeepUQ is a generative model based approach for reconstructing uncorrupted data from corrupted data. In addition to providing a best guess (maximum a posteriori estimate) of the uncorrupted data, DeepUQ provides an uncertainty quantification of the reconstruction.

### Examples

As an example we take an image from the test data set (left panel), corrupt it by adding noise and masking half of it (middle panel). We then run our reconstruction method to find the most likely uncorrupted image given the corrupted image and our generative model (right panel). 

![recon_example](/plots/4README/maskedNoise.png)

### How does is work?

We train a generative model on an uncorrupted data set (e.g. a Variational AutoEncoder). The latent space dimensionality of the generative model can generally be chosen to be much smaller than the dimensionality of the data space and we enforce the distribution of the latent space variables to be Gaussian. Once the generative model is trained, we can write down the posterior for corrupted images in latent space, find its maximum, fit the posterior distribution and draw samples from the fit. Points in the latent space can then be visualized by passing them through the generative model. A much more detailed description of the method can be found in the paper.

As an example we show samples from a bimodal posterior that we obtain from fitting a Gaussian mixture model to the posterior of a masked 4 (same 4 as above)

![masked_4](/plots/4README/masked_4.png)

Samples in latent space:
![posterior_example](/plots/4README/posterior_samples.png)

and collection of these samples forward modeled to data space:
![samples](/plots/4README/fwdmodeled_samples.png)

### How to use this repo?
The notebooks should be ready to plug and play (preferantially on a GPU). The module folder contains our pretrained generative model that the notebooks need to access. Each notebook contains essentially the same code but operates on a different data corruption example. We have added detailed comments to one of the notebooks. 

### Contributors
Vanessa Boehm  
Francois Lanusse  
Uros Seljak  

### References
Posterior Analysis:  
https://arxiv.org/abs/1901.04454   
Variational AutoEncoders (VAE):   
https://arxiv.org/abs/1401.4082  
https://arxiv.org/abs/1312.6114  
Dataset:  
http://yann.lecun.com/exdb/mnist/




