# Session 3 | Convolution Foundations

## What is Convolution?
The process of extracting features from input data using kernels/filters. Filter moves discretely on top of data-plane/channel, scales the input data equal to the size of it's receptive field, sums this results and creates a new feature map.
  
## 4-3 Convolution
To be Updated.
  
## 5-3 Convolution  
To be Updated.  
  
## Pointwise Convolution
To be Updated.
#### 1x1 Convolution
To be Updated.
#### Behind the scenes
To be Updated.
  
## Concept of Channels
To be updated.  
#### Receptive Field
To be Updated.
#### Checkerboard Issue
To be Updated.
##### This is what is happening at the background
To be Updated.
  
## Dilated Convolution
To be Updated.
#### What is dilated convolution doing?
To be Updated.  
  
## DECONVOLUTION or Fractionally Strided OR Transpose Convolution
To be Updated.
#### Simple but ineffective
To be Updated.
#### Better Approach
[Lesson 14: Deep Learning Part 2 2018 - Super resolution; Image segmentation with Unet](https://www.youtube.com/watch?v=nG3tT31nPmQ)
To be Updated with length to watch.
  
[Pixel Shuffle Paper](https://arxiv.org/pdf/1609.05158.pdf)  
  
## Depthwise Convolution
To be Updated.  
Great Explanation - [Depthwise Separable Convolution - A FASTER CONVOLUTION!](https://www.youtube.com/watch?v=T7o3xvJLuHk)  
  
## Strides
#### No Stride
To be Updated.
#### Strides
To be updated.
  
## MaxPool
To Be Updated.  
  
## Spacial Pyramidical Pooling
To be Updated.  
  
## Separable Convolution
To be Updated.  
  
## Grouped Convolution
To be Updated.  
  
## DropOut
To be Updated.  
  
## ResNet Blocks
To be Updated.  
  
## Architectural Basics
We need to follow some steps and consider few things before we can define our architecture. Let us assume we are training a heavy image recognition program.
What all do we need to consider?  
  
1. Data Augmentation
   - Use inbuilt data augmentation options in Keras, etc.
   - Use Image augmentation for machine learning experiments
   - Train network to one image size (say 224x224) and then fine tune after for less epochs to larger size (say 448x448)
   - Train image detection network with image classification data
  
2. Initialization
   - Random (default)
   - Xavier
   - Glorot
  
3. Activation Function
   - Sigmoid X(
   - ReLU
   - Leaky ReLU
   - ELU
   - SELU

4. Loss Function
   - Cross-Entropy Loss
   - Triplet-loss - multi-class loss from [1503.03832] FaceNet: A Unified Embedding for Face Recognition and Clustering
   - Center Loss from this paper
   - Angular Softmax from SphereFace: Deep Hypersphere Embedding for Face Recognition
   - Custom Loss Function

5. Regularization
   - DropOut
   - Label Smoothing (non-intuitive awesomeness)
  
6. Normalization
   - Batch Normalization
   - Layer Normalization
   - Weight Normalization
  
7. Optimizer
   - SGD
   - RMSProp
   - Adam
   - Cyclic Learning Rates
  
8. Convolutions
   - Usual Convolutions (stick to 3x3)
   - 1x1 Convolution
   - Cx1, 1XC Convolutions
   - Grouped Convolutions
   - Depthwise Separable convolutions
   - MaxPooling
  
9. Other Arch Decisions
   - Average Pooling as part of the last layer
   - Inception or ResNet or DenseNet module or VGG16
   - Skip Connections
___
## Assignment 3

1. Refer to the code shared in Session 1. Achieve 99.2 Validation Accuracy while using less than 20000 Parameters. Add the link to your Colab file.
2. Open this Notebook Change the skip-connection from layer 13, to layer 12, rename x to layer1, etc. and then train the network for 30 Epochs. Add the link to your Colab file.
3. In both the case we MUST be able to see the log of your training.
___
### Checkerboard Issue
[Reference Link](https://distill.pub/2016/deconv-checkerboard/)
