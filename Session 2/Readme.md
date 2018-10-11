
# Session 2 | Back Propagation & Misc
We cover Back Propagation and misc topics here. 

### Kernel Normalization
![CNN Filter](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%202/_files/cnnfilter.jpg?raw=true)  
This is how our trained kernels look like. On the face of they look just fine, but when we convert them into grey-scale to see their amplitudes we see a grave issue. Here is how they look in grey-scale:  
![CNN Filter BW](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%202/_files/cnnfilter_bnw.png?raw=true)  
What we can see now is that only a few kernels have enough amplitude distribution to be able to scale the features they want to extract. This may happen due to a mismatch in the number of features available to be learned from our database.  
  
We would like to normalize our kernels to make sure each one of them can contribute. This is how they'd look like after the normalization process:  
![CNN Filter BW Normalized](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%202/_files/cnnfilter_bnw_eql.png?raw=true)  
Normalization has now tried to equalize the kernels, i.e. pulled up the values.  
  
Let's look at these in 3d. Remember the 3D component here is just for reference, and represent the amplitudes.  
  
These are normal kernels:  
![](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%202/_files/ezgif-4-024a490477.gif?raw=true)  
These kernels are now "normalized":  
![](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%202/_files/ezgif-4-6ba4093f05.gif?raw=true)  
  
### Softmax
You'd remember softmax from our Session 1 code:

>model.add(Convolution2D(32, 3, 3, activation='relu', input_shape=(28,28,1))) 
model.add(Convolution2D(10, 1, activation='relu')) 
model.add(Convolution2D(10, 26)) model.add(Flatten()) 
model.add(Activation('softmax'))

Few people blatantly refer to softmax as Probability. The only common thing it shares with probability is that it's output scores for all the classes sums up to 1. But not all things which sum up to 1 is a probability.  
#### What is SoftMax?
The softmax function is often used in the final layer of a neural network-based classifier to help us clearly identify the winning class. Look at this image below:  
![](https://github.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/blob/master/Session%202/_files/softmax.png?raw=true)  
As discussed in the class you'd remember how it is skewing outputs. Cat in the first row does not deserve a score of 71% prediction when Dog score (4) is just 20% less than Cat's score (5).  
  
Remember, softmax is not probability, but probability like. Interpret SoftMAx's results with caution.  

### BackProp
As in the class, we will cover these videos in sequence to understand BackProp:  
**Video 1**  
[But what *is* a Neural Network? | Deep learning, chapter 1](https://www.youtube.com/watch?v=aircAruvnKk)  
  
**Video 2**  
[Gradient descent, how neural networks learn | Deep learning, chapter 2](https://www.youtube.com/watch?v=IHZwWFHWa-w)  
  
**Video 3**  
[What is backpropagation really doing? | Deep learning, chapter 3](https://www.youtube.com/watch?v=Ilg3gGewQ5U)  
  
**Video 3**  
[Backpropagation calculus | Deep learning, chapter 4](https://www.youtube.com/watch?v=tIeHLnjs5U8)  
  
### Assignment 2
1. Refer to this link [[AnalyticsVidhya]](https://www.analyticsvidhya.com/blog/2017/05/neural-network-from-scratch-in-python-and-r/), change all the "random values" we used to initialize our weights, and then write the tables again. Follow the description shared in the class.  (Links to an external site.)Links to an external site.
2. This [[link]](https://github.com/machinelearningblr/machinelearningblr.github.io/blob/master/tutorials/CS231n-Materials/CS231n-python-numpy-tutorial.ipynb) would cover most of the Python you'd need to know. Submit this file in .pynb format. None of the variables used in this link should be the same as yours. 