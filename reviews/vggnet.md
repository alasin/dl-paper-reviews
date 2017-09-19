# Very Deep Convolutional Networks for Large-Scale Image Recognition

**Problem**

ILSVRC (ImageNet Large Scale Visual Recognition Challenge) - Image classification for over a million images into 1000 object classes.

**Key points**

1. Authors demonstrate the importance of depth in CNNs for effective classification and other image recognition tasks.
2. No use of normalization layers as compared to AlexNet, because of smaller filter size.
3. Preference of depth with smaller filters over shallower networks with larger filters. 3 layers with **3x3** filters have an effective receptive field of **7*7** with 81% less parameters than one filter with size **7x7**.
4. Incorporate **1x1** convoloutional layers just to increase non-linearilty. Peforms better than nets with no such layer but worse than nets using **3x3** filters instead.
5. Pre-initialization of weights using shallower nets.
6. Two approaches for training: 
    * Single scale - Rescaling images so that shorter side (*S*) is 256 or 384, and then cropping 224x224 patches from it. During test time, 
    * Multi scale - Rescaling images so that shorter side (*S*) lies in [256, 512], to better capture the multi-scale nature of objects. 
7. Two approaches for testing:
   * Single scale - Scale shorter side of test image(*Q*) = *S* if *S* is fixed, and *Q* = 0.5 * (*S*min + *S*max) when multi-scale training is used.
   * Multi scale - *Q* = {*S* - 32, *S*, *S* + 32} if *S* is fixed, else *Q* = {*S*min, 0.5 * (*S*min + *S*max), *S*max}. Gives best results.
8. Dense and multi-crop evaluation:
    * Dense - FCN layers are converted to CNNs and uncropped image is passed. Scores are then averaged for this image and its flip.
    * Multi-crop - Multiple crops of test image are taken and their scores averaged.
    * Works best when both are combined. 

**Results**

1. 2nd in ILSVRC 2014 classification task behind GoogLeNet in net performance.
2. Best performance if using only 1 network as opposed to ensemble.
3. 1st in ILSVRC 2015 localization task.
4. Learned VGG representations generalize well on other datasets and tasks as well.

**Notes**

1. Simple to understand network architecture, with pre-trained models being able to generalize well on other datasets.
2. Very heavy model with around 138M parameters, not suitable for actual deployment. 