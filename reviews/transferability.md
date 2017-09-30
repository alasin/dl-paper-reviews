# How transferable are features in deep neural networks?

**Problem**

Quantifying the *generality* and *specificity* of features learned at different layers of a convolutional neural network. 

**Key Points**

1. Show that the first 1-2 layers are usually general as they resemble color blobs or Gabor filters and the higher layers are usually specific to the type of dataset.
2. Split ImageNet into two datasets A and B, and perform experiments on new networks:
    * Base - A base 8 layer CNN trained on A and B
    * Selffer - First *n* layers copied from the base network and rest is randomly initialized and retrained. 
    * Transfer - First *n* layers copied from the base network and rest is trained on a different task.

    Each of these *copied* layers can be fine-tuned or kept frozen. 

**Results**

1. As the *n* increases from 2 to 6, **selffer** networks with frozen layers perform worse, showing the presence of *fragile co-adapted features* on successive layers and showing dependency on previous layers. Performance is similar to base network when *n* reaches 6, showing that co-adaptation is more prominent in middle layers than at higher layers. Also, there are less features to retrain now.
2. **Selffer** networks with fine-tuning are able to show similar performance as base networks.
3. **Transfer** networks with frozen layers exhibit the problem of *fragile co-adapted features* as well as *specificity* of higher layers.
4. **Transfer** networks with fine-tuning show better results than the base networks, showing that fine tuning after transferring features improve generalization.
5.  Features are more transferable on similar datasets than distinct datasets. Example - Natural and man-made objects in ImageNet (Distinct)

**Notes**

1. The paper is insightful and demonstrates the intuition behind transfer learning.
2. Studies were only done on classification task. Should have performed similar experiments on different vision tasks.