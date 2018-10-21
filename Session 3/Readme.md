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
Reference Links: 
1. Data Augmentation
   - [Building powerful image classification models using very little data](https://blog.keras.io/building-powerful-image-classification-models-using-very-little-data.html)
   - [Image Augmentation for Deep Learning With Keras](https://machinelearningmastery.com/image-augmentation-deep-learning-keras/)
   - Examples :
     - [Udacity - CNN in Keras for Image Augmentation](https://github.com/pablomateo/ImageAugmentation/blob/master/cifar10_augmentation.ipynb)
     - [Image Augmentation for Deep Learning using Keras and Histogram Equalization](https://towardsdatascience.com/image-augmentation-for-deep-learning-using-keras-and-histogram-equalization-9329f6ae5085)
     - [Image classification with Keras and deep learning](https://www.pyimagesearch.com/2017/12/11/image-classification-with-keras-and-deep-learning/)

2. Initialization
   - [Deep Learning Best Practices (1) — Weight Initialization](https://medium.com/usf-msds/deep-learning-best-practices-1-weight-initialization-14e5c0295b94)
   - [How to Initialize weights in a neural net so it performs well? — Super fast explanation for Xavier’s Random Weight Initialization](https://hackernoon.com/how-to-initialize-weights-in-a-neural-net-so-it-performs-well-3e9302d4490f)

3. Activation Function
   - [Fundamentals of Deep Learning – Activation Functions and When to Use Them?](https://www.analyticsvidhya.com/blog/2017/10/fundamentals-deep-learning-activation-functions-when-to-use-them/)
   - [Quora - What is the role of the activation function in a neural network? How does this function in a human neural network system?](https://www.quora.com/What-is-the-role-of-the-activation-function-in-a-neural-network-How-does-this-function-in-a-human-neural-network-system)
   - [Deep Learning: Overview of Neurons and Activation Functions](https://medium.com/@srnghn/deep-learning-overview-of-neurons-and-activation-functions-1d98286cf1e4)
   - [Understanding Activation Functions in Deep Learning](https://www.learnopencv.com/understanding-activation-functions-in-deep-learning/)

4. Loss Functions
   - [[Youtube] Loss Functions Explained - Siraj Raval](https://www.youtube.com/watch?v=IVVVjBSk9N0)

___
## Assignment 3

1. Refer to the code shared in Session 1. Achieve 99.2 Validation Accuracy while using less than 20000 Parameters. Add the link to your Colab file.
2. Open this Notebook Change the skip-connection from layer 13, to layer 12, rename x to layer1, etc. and then train the network for 30 Epochs. Add the link to your Colab file.
3. In both the case we MUST be able to see the log of your training.
___
### Checkerboard Issue
[Reference Link](https://distill.pub/2016/deconv-checkerboard/)
