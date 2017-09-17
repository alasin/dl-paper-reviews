# Going deeper with convolutions

**Problem**

Better and computationally cheaper architecture for ILSVRC (ImageNet Large Scale Visual Recognition Challenge) - Image classification for over a million images into 1000 object classes.

**Key points**

1. Introduction of a novel *Inception* module, which is based on the idea of modeling sparse structure of a convolutional vision network using available dense compute operations.
    - Uses **1x1** convolutions for feature-space dimensionality reduction before larger **3x3** and **5x5** convolutions.
    - Performs **1x1**, **3x3** and **5x5** convolutions in a parallel fashion, to capture sparsely correlated features. Concatenates all of them along with a max-pooled version (followed by **1x1** convolution) of input.
    - Ratio of **3x3** and **5x5** to **1x1** filters increases as we go deeper in the netowrk, to capture high-level abstractions. 
    - ReLU activations in every layer, making them learn faster.
    - Based on practical intuition that visual information should be processed at various scales and then aggregated so that the next stage can abstract features from the different scales simultaneously.
2. Use of auxiliary classifiers after some *Inception* modules to tackle the vanishing gradient problem. This extra loss gets added in a weighted manner to the loss flowing through the main network. Discarded at test time.
3. Data augmentation by resizing the image to 4 *scales* of shorter dimension, taking left/top, center and right/bottom squares, taking 4 224x224 corners, center crop, 224x224 resized version and their mirror flips, making it 4 * 3 * 6 * 2 = 144 crops per image.
4. Ensures a max. limit of 1.5 billion multiply-add operations at inference.

**Results**

1. Best performance in ILSVRC 2014 classification and detection tasks.
2. *GoogLeNet* architecture uses 12x less parameters than *AlexNet*.
3. Demonstrated that sparser architectures can perform better and are in general, more useful than the conventional ones.

**Notes**

1. Excellent paper with relevant intuitions for most of the choices made in the architecture design.
2. Clearly the best choice for practical deployment.
