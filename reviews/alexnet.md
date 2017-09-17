# ImageNet Classification with Deep Convolutional Neural Networks

**Problem**

ILSVRC (ImageNet Large Scale Visual Recognition Challenge) - Image classification for over a million images into 1000 object classes.

**Key points**

1. Authors introduce a deep convolutional neural network for the task of image classification, achieving best results on ILSVRC and popularizing ConvNets for various computer vision problems.
2. They propose an 8-layer architecture comprising of 5 convolutional and 3 fully connected layers, excluding the non-weighted layers.
3. Use of **Re**ctified **L**inear **U**nits as the non-linearilty activation function after convolutional and pooling layers, that doesn't suffer with the gradient saturation suffered by tanh and sigmoid functions and makes training six times faster.
4. Data augmentation using geometric transformations like translation and horizontal reflections, and adding PCA-ed images to the dataset, to prevent overfitting and generalizing it for changes in intensity and illumination.
5. Use of Dropout technique to make the model more robust and essentially, make it work like an ensemble without actually training multiple networks.
6. Give a [GPU implementation](https://github.com/dnouri/cuda-convnet) of their model.
7. Use an overlapping pooling layer instead of the conventional local pooling in CNNs.

**Results**

1. Achieve state-of-the-art results in ILSVRC, beating the second best by a significant margin.
2. Show that ReLUs are superior to tanh and other activation functions.
3. Show that their approach is scalable as GPUs become better and faster.

**Notes**

1. A lot of choices driven by experiments and lack intuition. 
2. Initial cropping of all images to 256*256 could crop out the target object partially.
3. Zero padding not mentioned as kernels of size 11 with stride 4 not compatible with 224x224 images.
4. Overall, a great paper to understand a non-trivial CNN architecture which could be used effectively for multiple problems.