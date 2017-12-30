# Decomposing Motion and Content for Natural Video Sequence Prediction

**Problem**

Future frame prediction in natural video sequences.

**Key points**

1. Authors introduce an end-to-end trainable encoder-decoder architecture (MCnet) which decouples motion and content streams into different pathways. Future frame is predicted by transforming the last frame into the next by the observed motion.

2. Use a two-stream encoder architecture for motion and content streams:
    * Motion encoder is modeled as a convolutional LSTM which operates on
        * Element-wise consecutive frame difference.
        * Motion encoding feature tensor of last frame.
        * Memory cell observed through time till last frame.
    and outputs
        * Motion encoding feature tensor of current frame.
        * Memory cell observed through time till current frame.
    * Content encoder is modeled as a simple CNN which outputs content encoding feature tensor of current frame.

3. Use residual connections between encoders and decoders at every scale to preserve content after every pooling operation. The residual function encodes a concatenation of motion feature tensor and content fetaure tensor at every scale.

4. A common decoder first combines the two encoded representations through a CNN and then deconvolves to predict the final output by operating on the above computed representation and residual skip connections.

![Architecture](https://sites.google.com/a/umich.edu/rubenevillegas/_/rsrc/1478353328880/iclr2017/Screen%20Shot%202016-11-05%20at%209.39.05%20AM.png)

5. Use a weighted sum of GAN loss (Generator loss during GAN training) and Image loss (L1/L2 loss plus gradient difference loss) for training the network.

6. For predictiong multiple frames, the predicted frame is passed as an input for the next step.  

**Results**

1. Achieve best SSIM and PSNR metrics on KTH and Weizmann action datasets.

2. Perform better than the chosen baseline - a ConvLSTM.

3. Show that models generalize well to unseen videos, unlike ConvLSTM. Infer that the decoupling is responsible for this generalization. 

**Notes**

1. Easy to understand with simple explanations.

2. Network architecture could have been described in a better way.

3. Would have liked to see the performance on more frames/longer videos.