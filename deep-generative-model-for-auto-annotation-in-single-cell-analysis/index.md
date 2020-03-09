---
title: deep_generative_model_for_auto-annotation_in_single-cell_analysis
date: 2019-12-16 22:23:28
---

# Dimension Reduction

With the raw data of single-cell RNA sequencing, the next step is reducing the dimension to get the latent variances. There are four kinds of information have to be included: cell type information, batch information, library information and the gene expression information. 

In this project, we will adopt the generative model proposed in scvi to get the latent variances.  The model has included the batch information, library information and gene expression information. By including the cell type information, we define the generating process as follow:

![1576508656237](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\1576508656237.png)

As commonly defined in autoencoders, z follows the standard multivariate normal prior  so that it can be reparameterized  into any arbitrary multivariate Gaussian random variable, which can simplify the calculation. 

B denotes the number of batched and ![1576509905452](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\1576509905452.png)

![1576509933899](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\1576509933899.png)

are the  μσ , are set to be the empirical mean and variance of the log-library size per batch. 

The parameter R θ∈ + G denotes a gene-specific inverse dispersion, estimated via variational Bayesian inference. 



The mainly different is we will also encode the cell type information into the generative model.

![1576508886166](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\1576508886166.png)

![1576508897859](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\1576508897859.png)

![1576508908811](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\1576508908811.png)

![1576508919679](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\1576508919679.png)

![1576508938012](C:\Users\admin\AppData\Roaming\Typora\typora-user-images\1576508938012.png)

# Classifier