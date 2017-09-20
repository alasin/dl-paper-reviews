# Deep Residual Learning for Image Recognition

**Problem**

*Degradation* or saturation of accuracy after a certain point while training very deep neural networks. 

**Key points**

1. Introduction of a *residual block* that tries to learn a residual function `F(x) = H(x) - x` . Intuition is that it's easier to converge this function to zero as we go deeper rather than to learn an identity mapping with increasing number of non-linearities.

2. Use of *shortcut connections* that perform 'identity' mapping where the output of certain stacked layers (a residual block) is added to the input to that block.

3. No extra parameters and computations for this 'identity' mapping.

4. Two approaches for handling dimension change - 
    * Identity mapping with extra zero entries added for padding.
    * A projection parameter `w` multiplied with input (used as `wx`) to match the output dimensions. Perform slightly better.

5. Use of batch normalization before activation layers to avoid vanishing gradients.

6. Similar data augmentation techniques as *ImageNet*.

7. Demonstrate that plain deeper networks by default have higher training error as well compared to sufficiently deep networks. *ResNets* have lower training error as we go deeper. Analyse deeper *ResNets* on smaller datasets for experiments.

8. Use *bottleneck design* by using **1x1** convolutions in a residual block to further reduce the dimensionality.

**Results**

1. Excellent results in ILSVRC detection and classification tasks. 3.57% top-5 error in classsification using ensemble of two nets, significantky outperforming previous models, with fewer parameters.

2. Generalized well to other datasets. Won MSCOCO, ILSVRC localization and other tasks as well. 

**Notes**

1. Neat idea of transforming the problem of learning identity mapping to learning a residual function instead, with no extra parameters.

2. Number of layers between the skip connections seem arbitrary. Should have performed experiments to show the effect of changing the freqeuency of this skip connections. 