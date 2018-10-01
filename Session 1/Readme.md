# Session 1 | ML Basics
## Machine Learning Basics & 1st CNN HandsOn
Session 1 will cover the basics of Convolution Neural Networks. Session 1 content can be categorized as "medium to advance" w.r.t. difficult level. The idea here is to present these concepts right away, so we can repeat them later on with some pre-built background. 

### Building the intuition!
DNNs no doubt are inspired from our brain, though there are tons of differences. DNNs like our brain follow neural connections, but unlike our brain, connections we make in DNNs are far more ordered and restricted. Either all of them take part or none. The image below shows the spiking which occurs inside our brains: 
![Inside Brain](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%201/_files/giphy-downsized-large.gif?raw=true)

### Vision
EIP will focus only on vision-related problems. Fortunately today any problem can be broken down into a vision problem. For example, below you can see how human voice can be interpreted as an audio-graph and then a CNN can learn how the sound of the words "look" like. 
![Voice](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%201/_files/PvPpN.png?raw=true)

We need to learn a bit about how our eyes function. 

Below, in the picture, all that brown stuff you see is actually a group of muscles which pulls the transparent lens allowing us to focus on objects placed at different depths. 

The image projected on the retina is captured by the rods and cones there. Look at the image below and take a note of the optic nerve. What we see travels through this pipe. 

![eye-close-up](http://3.bp.blogspot.com/-Elau01j_Uy8/VnWucwCsm_I/AAAAAAAALEs/03zy4R_sAoI/s1600/CrossSection.JPG)


Image processed digitally are broken down into three channels normally, R, G and B. We need to focus on this concept of the channels. 

Soon you'll see that the concept of channels will become tough to track. In images you capture through your phone, there are only 3 channels. But we can divide our images into multiple channels, not only in color channels but texture, edge and pattern channels as well. 

Before we go delve deeper into channels, let us build some intuition on why we would need so many channels, and more importantly some background behind what has led to the current architecture of DNN/CNNs. 

### The Experiments
2 experiments have given us a great insight into how brains actually see things. 

In the first experiment, we inject a cat with radioactive glucose and hope to see absorption of this glucose in the brain wherever it was absorbed to see a particular image. The results are magical:
![Experiment1](http://fourier.eng.hmc.edu/e180/lectures/figures/retinotopicmap.gif)

What we observe is that the image which the cat saw, got actually "printed" on the head. This is fascinating as this tells us that images what we see are first physically drawn inside our head. 

In the second experiment, we connect a few electrodes again on the region of the brain used for viewing and observe that there are some neurons which fire if an edge at a particular angle is shown. These neurons will fire if and only if they observe a particular edge, else remain silent.  
![Experiment2](http://www.utdallas.edu/~tres/integ/sen4/8_05.jpg)  

Combining these two experiments give us some idea of what is happening. First, the image is "sort-of" printed inside our heads, and then neuron under this print-area fires if the print happens to be similar to the feature they were expecting, like horizontal or vertical edge.

What we want to focus here is "small features". We need to deconstruct the image into smaller features, and once we have these smaller features, we can build complex features on top of them. Very similar to how alphabets make words, words make sentences, sentences make paragraphs and paragraphs make stories. 

What is also important here is to remember that we need to maintain a separate channel for any feature. A kernel or feature extractor or filter extracts features and then these features are stored in a channel or a feature map (which we will call image as well).

### Understanding features through music
Below, we are going to listen to windows booting sound, then simple kernels/notes which make up that sound and then perform convolution and then hear what they extract. Kernels/notes themselves are boring, but what they extract is beautiful!  
[[Youtube Video]](https://www.youtube.com/watch?v=ILvq4kmjk5g)  

### Feature Extractors
Now, look at the image below. We now have two simple kernels convolving on top of an image, and what they extract can be also be seen.  
![Feature Extractor](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%201/_files/giphy.gif?raw=true)  

### The Alphabets of CNN.
This is how the first basic kernels look like. They are the building blocks for more complicated features.  
![Filters](https://qph.fs.quoracdn.net/main-qimg-4bfdf63a4c5b24590f0deec9673eaee5-c)  
You can imagine how these similar kernels can be used to create complex features are shown below:  
![Kernels](https://ujwlkarn.files.wordpress.com/2016/08/screen-shot-2016-08-10-at-12-58-30-pm.png)  

## CNN Concepts
  
### What is a convolution?
![2x2Convolution](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%201/_files/4-2ConvolutionSmall-1.gif?raw=true)

This is what convolution in-process looks like. What you are seeing is a 4x4 channel (purple in color) being convolved with 3x3 kernel (dark purple), and creating a new 2x2 output channel. You are looking at 9 product finally being summed up in the green output. These 9 numbers are picked randomly, but it is these 9 numbers are are training and hoping that they are extracting the edges/gradients/features we want. 

Please notice that when a 3x3 kernel convolves over say 4x4 image/channel, we get an output of 2x2. So a drop of 2x2 in resolution.  
![3x3 Convolution](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%201/_files/5-3%20Convolution%20Small.gif?raw=true)  
  
Similarly, when a 5x5 image/channel is convolved with a 3x3 kernel/filter, we get 3x3 as the output. Each kernel produces its own output/channel.  
  
Another way of looking at this is, each cell/pixel in the output/channel has "seen" 3x3 input, something we refer to an as receptive field.  
  
### The receptive field and why do we always use 3x3 kernel
![Receptive Field Small.gif](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%201/_files/Receptive%20Field%20Small.gif?raw=true)  

Scaling this up, we notice that 5x5, after convolution with a 3x3 kernel/filter, produces 3x3 channel/output/image, and when a 3x3 channel/image/output is convolved with another 3x3 kernel, the output is just 1x1 channel. That is, if we convolve 5x5 with a 5x5 kernel, we will get 1x1. So, if you want a 5x5 kernel, just perform two 3x3 convolutions. Three 3x3 equates to a 7x7 kernel, and so on. 3x3 is much more compute-friendly than a large kernel, and this is the reason why 3x3 is now used as a default. 

The local receptive field at the "yellow" channel is 3x3, as each pixel sees 3x3 pixels/area. The local receptive field at "cyan" channel is also 3x3 as it also sees 3x3 pixels. But the global receptive field at "cyan" is 5x5. Whenever we are adding a convolution layer, not only we are extracting features, we are also increasing our receptive field. 

Consider this, if I give you a character "q" and ask you if you can tell me the meaning of the word I am talking about which has "q" in it, you would say that you need much more information than just "q". Similarly, if we are expecting our DNN to be able to predict what is exactly is there in the image the last layer should have "seen" the whole image, i.e. the receptive should be near to the size of the image. 

### How many layers do we need in a network? 
We must add as many layers as needed to reach the required receptive field, and as we have learned, each time we add a convolution layer, our receptive field increases by 2x2. 

### Let's build a network
Say our images are 400x400. As a CEO of a company would you want to talk to 400x400 people? Probably you'd rather want a group max, say, of 100 people whom you'd talk and hope that they, each in return get more information from 100s of more people reporting to them. In DNN/CNN this number is generally 128, 256, 512, 1024 or 2048 depending on how accurate you want your network to be. We will consider 100, for easy calculations here. 

So we need to move from 400x400 to 10x10 or cover 390x390 in receptive field. This is how things would progress each time we add a 3x3 convolution layer:  

| | | | | | |
|-|-|-|-|-|-|
| 400x400 | 398x398 | 396x396 | 394x394 | 392x392 | 390x390 

and so on. If we naively keep on add layers we would end up with 390/2 = 195 layers. 195 layer network is a huge network. If we add these many layers, we'd need a really expensive GPU to handle such a network. We need to be smarter than this. 
  
### The Pyramids
What basically we are looking for is to reach the top of a pyramid. 
![Pyramids](https://getsready.com/wp-content/uploads/2015/09/Egyptian-Pyramids-2.jpeg)  
If the only objective is to reach on top of the pyramid, we can take the Mayan approach, a stepped pyramid:
![Stepped-Pyramid](https://media-cdn.tripadvisor.com/media/photo-s/11/0e/10/c1/day-trip-to-chichen-itza.jpg)  

So, if at each step, if we can make sure that we do not use a lot of information, and maintain out receptive fields, we are good to go. 

Look at this image below:  
![Image.png](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%201/_files/Image.png?raw=true)  
What all can you tell about the image? A man, a woman, a child, a house, green walkway. House probably have a chimney. Sun and cloud, etc. We can say all of this about this image because these are the feature which is the "loudest". Now, Look at the original image below:  
![Original-Drawing](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%201/_files/children-drawing.jpg?raw=true)  
So if we carry forward largest features we can be sure that we can follow the Mayan stepped pyramid approach. We will not be doing this kind of extreme scaling, but only 2x2. 

### Max-pooling
![MaxPool Small.gif](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%201/_files/MaxPool%20Small.gif?raw=true)  
  
What you see here is Max-pooling at 3x3 scale. We nearly always perform Maxpooling at 2x2 scale. Our result for 2x2 pooling on this 6x6 channel/image would result in a 3x3 channel below:  

| | | |
|-|-|-|
| 5 | 6 | 4 |
| 9 | 7 | 5 |
| 3 | 3 | 5 |

These numbers are the "loudest", the class monitors of their classes, representing the rest of the numbers. 

If we build our network again, we'd be using many fewer layers:  
![NetworkMatrix](https://raw.githubusercontent.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/master/Session%201/_files/Network%20Matrix.JPG)  
From 195 to 28 layers, impressive, isn't it?

Now, let's look at the channels again. 

In the first layer, we would be convolving with 32 3x3 kernels and then with 64.

|Input Channels|Kernel|Output Channels|
|--------------|------|---------------|
400x400|3x3, 32|398x398, 32|
398x398, 32 |3x3, 64 |396x396, ??|

The question we need to ask ourselves is, how many channel second layer would create. The answer is 64, but what exactly is happening to those 32 channels in the input space? 

We add layers because we want to make complex compound feature extractors. To make an eye detector/extractor, we need to mix an arc detector, an inverted arc detector and a black ball/circle detector. All these simpler features would be available in different channels. This means any kernel we add, MUST interact with all the channels available in the input space. The table above must be re-written as below:  
| Input Channels | Kernel | Output Channels |
|----------------|--------|-----------------|
400x400, 1|[3x3, 1], 32|398x398, 32|
398x398, 32|[3x3, 32], 64|396x396x64|

Our 3x3 kernel MUST have 32 channels to be able to interact with 32 channels in the input space.  

In the animation below you can see a 5x5 input with 3 channel being convolved with 4 3x3 kernels, and those 3x3 kernels themselves have 3 channels.  
![convolution.gif](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%201/_files/convolution.gif?raw=true)  

So instead of 9 multiplication, we have 3x3, 3 = 27 multiplications, and the result is then summed up. 

But we have a problem here. You see, we generally increase our kernels from 32 to 64, to sometimes upto 512 and beyond, depending on how complex the problem is. This increase is required because not only we want extract features related to the object we want to detect, we also want to detect background. Imagine if we can get rid of the background, and only "show" or pass on features of the object in context to out 10x10, detection can be much better. 

Look at this table:

|Input Channels|	Kernel|	Output Channels|
|-|-|-|
|400x400, 1	|[3x3, 1], 32|	398x398, 32|
|398x398, 32|	[3x3, 32], 64|	396x396, 64|
|396x396, 64|	[3x3, 64], 128|	394x394, 128|
|394x394, 128|	[3x3, 128], 256|	392x392, 256|
|392x392, 256|	[3x3, 256], 512|	390x390, 512|
  
You see the last layer output? 390x390, 512 just too many parameters, and if do not do something now our network will blow up and our GPU is going to scream OOM (out of memory). 

No one stopped us from using as many kernels as we want, so no one is stopping us from doing this:

||||
|-|-|-|
390x390, 512|	[3x3, 512], 64|	388x388, 64|

This is good as this is allowing us to reduce the number of channels, but 3x3 is going to reinterpret the data. We do not want that. And like we can use any number of kernels, we can also use a new size kernel:

||||
|-|-|-|
|390x390, 512|	[1x1, 512], 64|	390x390, 64|

1x1 is a great kernel. It can only look at one pixel at a time, so it is not interpreting local data, but combining whole channels. Back-propagation works in sync and makes sure that 1x1 only combines those channels which are related to each other semantically. This is how 1x1 kernel convolution looks like:  
![1x1-min.gif](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%201/_files/1x1-min.gif?raw=true)  
  
This is what is happening above:

||||
|-|-|-|
32x32, 10|	[1x1, 10], 4|	32x32, 4|
  
### Sample Neural Network
Let's write a pseudo code for a simple CNN on MNIST dataset
`
Input(28x28x1)
Conv2D(32, 3, 3, act=ReLU) >?
MaxPooling(2) >?
Activation (ReLU) << Useless here. 
Conv2D(10, 1, 1, act=ReLU) Perfectly OK
Conv2D(10, 13, 13, act=None) >?
SoftMax()
Compile/Fit/Optimise
`
Code is self explanatory, but we have adding "act" or activation function above. We (covered activation function in the class) will cover activation in much more detail in Session 3, but for now, just think that, an activation function help us decide which information should be filtered and which one shouldn't. 

The way we write a similar CNN in Keras would look like this: 
`
model.add(Convolution2D(32, 3, 3, activation='relu', input_shape=(28,28,1)))
model.add(Convolution2D(10, 1, activation='relu'))
model.add(Convolution2D(10, 26))
model.add(Flatten())
model.add(Activation('softmax'))
`
This is a really bad network, but check this code working at this link:  
[bit.ly/2IBqQJD](bit.ly/2IBqQJD)  
This bad code gets 99.62% accuracy! And on validation set, it gets 98.29% accuracy. This is the real power of a DNN/CNN.  
I urge you to look at the code and try and reduce the number of parameters and try and also increase the validation accuracy to ~99.6. It is important to get a "feel" of how to train a DNN and what all can be changed. So start playing with it!
