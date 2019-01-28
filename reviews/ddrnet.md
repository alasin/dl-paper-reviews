# DDRNet: Depth Map Denoising and Refinement for Consumer Depth Cameras Using Cascaded CNNs

**Problem**

Denoising and refining depth maps using the corresponding RGB images.

**Key points**

1. Authors introduce a cascaded CNN comprised of denoising and refinement networks for depth maps. Raw maps are first passed through denoising net and then the output is passed through the refinement net along with the intensity image for the final prediction.
2. They create their own dataset comprising of humans by using structured light and time-of-flight cameras and create ground truth by fusing different depth maps to create a 3D scene and then rasterizing for a particular view.
3. Propose a differentiable depth-to-normal layer which is used extensively.
4. Denoising network is trained supervisedly using L1/L2 losses and a normal consistency loss that ensures normal smoothness in the neighborhood. This network primarily removes low frequency noise.
5. A shallow refinement network that incorporates skip connections is used for fusing RGB local features with depth features. A shading loss is proposed that is essentially a reconstruction loss based on shape from shading along with L2 loss between the predicted depth and reference depth. A local smoothness regularization term is also used. 

**Notes**

1. Code and dataset is publicly available.
2. Dataset is limited to human bodies. Yet to be seen if it generalizes to outdoor/general scenes.
3. Lot of hyperparameters for loss terms.