# Unsupervised Representation Learning by Sorting Sequences

**Problem**

Unsupervised representation learning using videos. Modeling this problem as a sequence sorting task by exploting temporal coherence. 

**Key Points**

1. Introduce sequence sorting as a self-supervised approach for representation learning by using unlabeled videos. 3-4 randomly shuffled frames are passed as input to a network that outputs the correct ordering by formulating it as a multi-class classification. (Number of classes = `n!/2`) 
2. Data sampling - 
    * Sample frames based on maximum motion among them. Use magnitude from optical flow for this selection.
    * Further select spatial patched with maximum motion using sliding-window approach.
    * Do spatial jittering by adding/subtracting 5 pixels from the patch.
    * Random channel splitting to emphasize semantic learning over low-level features.
3. Order Prediction Network - 
    * Siamese architecture for sharing weights among frames.
    * Pairwise concatenation of fc6/fc7 features, followed by another concatenation, followed by a softmax for `n!/2` class probabilities.
4. Use OPN as pre-training for action recognition tasks.

**Results**

1. Great results on UCF-101 and HMDB-51 datasets for video based pre-training. Imagenet initialization still better.
2. Generalizes well for classification and detection tasks.
3. Scalable as more data led to better accuracy.

**Notes**

1. Easy to understand paper with a novel approach.
2. Doesn't talk about patch size < 80 and its effect on performance.
3. No intuition about why different strategies for color splitting perform better or worse over the rest. Neat technique though to explicitly force the network.
4. Choice of number of frames (3-4) seems arbitrary. Performance effects with a more number of frames should have been measured. 
