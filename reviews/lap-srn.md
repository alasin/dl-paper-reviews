# Deep Laplacian Pyramid Networks for Fast and Accurate Super-Resolution

**Problem**

Convolutional Neural Networks based single-image super-resolution.

**Key Points**

1. Authors propose a Laplacian Pyramid Super-Resolution Network (LapSRN) that takes a low-res (LR) image as input and progressively generates residuals at different scales for high-res (HR) images. It comprises of a feature extraction and a image reconstruction branch.

![Architecture](http://vllab1.ucmerced.edu/~wlai24/LapSRN/images/network.jpg)

2. The output of each *deconv* layer is connected to a conv layer for reconstructing HR image, and for further in feature extraction for higher layers.

3. The *deconv* layer is intialized with a bilinear kernel and is jointly optimized with all other layers. 

4. Use **Charbonnier loss** function as opposed to the usual **l2 loss** which is more robust and produces less blurry images. **Leaky ReLUs** used for activation.

5. Patches of size **128x128** for training. Augmentation done by scaling images from [0.5, 1], random rotation by 90, 180 or 270 degrees, and horizontal/vertical flipping. LR images generated from original images by bicubic downsampling. 

**Results**

1. Show that **Charbonnier loss** performs better than **l2 loss**, and residual network is better than non-residual network.

2. Achieves pretty good IFC values across datasets and best results for PSNR/SSIM/IFC for 8x network.

3. Not able to hallucinate finer details at higher resolutions.

**Notes**

1. Efficient and sufficiently accurate method for super-resolution. Single feed-forward pass could be used to generate 2x, 4x and 8x resolutions.

2. The performance for 2x and 4x zoom using 8x networks isn't as good as their specific 2x/4x counterpart networks.

3. Increasing depth of network doesn't help much in getting better results. Considering residual training, shouldn't it help to increase depth?

4. Should have compared qualitatively with SRGAN. Should perceptual loss be used for better qualitative results than other loss functions?  