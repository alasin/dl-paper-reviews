# Region-based Convolutional Networks for Accurate Object Detection and Segmentation

**Problem**

Detecting multiple objects in an image.

**Key points**

1. Authors propose a CNN-based object detection system consisiting of 3 modules. First generates category-independent region proposals which are the candidate bounding boxes. Second is a CNN that extracts features. Third is a set of class-specific linear SVMs. 
2. Use selective search for region proposals which output around 2000 bounding box proposals.
3. At test time, every extracted feature vector is scored using each SVM. A greedy non-maximum suppression is appled for each class that rejects a region if it has an IoU overlap with a higher scoring selected region larger than a learned threshold.
4. Fine-tune networks trained for ILSVRC on region proposals, with regions having a >= 0.5 IoU overlap with ground truth being a positive example. 

**Results**

1. Achieve state-of-the-art results in PASCAL VOC.
2. Show that transfer learning works.

**Notes**

1. Very slow.
2. Very dependent on the region proposals.
3. Using SVMs at the end seems redundant. Even though auhors have tried to explain why they chose it, it doesn't seem elegant.