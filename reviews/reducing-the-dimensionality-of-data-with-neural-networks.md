# Reducing the dimensionality of data with neural networks

<br>

**Problem**

Converting high-dimensional data to low-dimensional vectors/codes effectively that can be used to reconstruct the original data.

**Contributions**

1. The authors introduce a neural net based approach for dimensionality reduction.
2. The concept of 'Autoencoders' is introduced, where an encoder-decoder architecture is used to first reduce the dimensionality of input data and then used to reconstruct the original high-dimension data with the encoded representation.
3. A pre-training technique is used to initialize the weights properly, bringing them close to the actual weights. The obtained weights are then fine-tuned on the actual training dataset.

**Results**

1. Better quantitative and qualitative results than Pricipal Component Analysis (PCA) in image and document reconstruction. 
2. The pre-training technique is also shown to improve the performace in classification and regression tasks, as it helps in generalization by ensuring that most of the information in the weights comes from modeling the images.
3. Without pretraining, the very deep auto-
encoder always reconstructs the average of the
training data.
