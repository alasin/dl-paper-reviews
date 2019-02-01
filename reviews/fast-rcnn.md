# Fast R-CNN

**Problem**

Detecting multiple objects in an image.

**Key points**

1. Builds upon RNN and SPP by using object proposals while doing one forward pass through the CNN for the image.
2. Propose a differentiable ROI pooling layer which max pools the feature maps of the ROIs into a fixed window size that depends on the choice of network used.
3. At the end, it branches into two sibling output layers. One does a (K+1) way softmax classification and the other regresses bounding boxes (refined) for each of the classes. The bounding boxes regressed are normalized and are with respect to the ROI. 
4. Use a constrained batching such that only 2 images are used for a minibatch with 64 region proposals each. This saves time as features for all ROIs are computed only once. This allows back propagation through all the layers.
5. Use a multi-task loss that is a combination of softmax loss and and a soft L1 loss for the bounding boxes.
6. For faster detection with a lot of ROIs, SVD is used to truncate the weights of the fully connected layers. This compression gives a lot of speedup.

**Results**

1. Achieve state-of-the-art results in PASCAL VOC.
2. Show that multi-task loss works and helps both tasks.
2. 213x speed-up at test time over RCNN. 

**Notes**

1. Still dependent on initial region proposals. An end-to-end solution would be much more elegant.
2. Final multi-task loss is pretty intuitive and makes sense.
3. Paper is very clearly written. 