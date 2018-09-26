# _ASSIGNMENT 1_
- Download Typora (or any markdown editor you prefer)
- You can refer this link to learn about markdown: [Markdown Cheatsheet](https://guides.github.com/features/mastering-markdown/)
- Write articles on the topics mentioned below between 50-100 words in a markdown format and upload it on the LMS (would be soon made enabled)
- You must mention your name, batch number in your markdown file.
- Your markdown file must have an image of your choice.
- Topics:
  + Convolution
  + Filters/Kernels
  + Epochs
  + 1x1 convolution
  + 3x3 convolution
  + Feature Maps
  + Feature Engineering (older computer vision concept)
- Bonus points if you write on any of these:
  + Activation Function
  + How to create an account on GitHub and upload a sample project
  + Receptive Field.
  + 10 examples of use of MathJax in Markdown
- Deadline 1 hour before your next session.
- You MUST use your own words while writing any of the above, if we find plagiarism, 0 marks would be awarded for that article.
___
## AKSHAY KUMAR | EIP2 Batch1
___
### Convolution
In image processing, by convolution we mean, putting a matrix over another and then calculating the weighted sum of all pixel values. One of these matrices is an image and the other one is a kernel matrix. The kernel matrix is generally smaller than the image (3x3 is the standard).
![Convolution](http://machinelearninguru.com/_images/topics/computer_vision/basics/convolution/1.JPG)

The Kernel matrix is moved over the image matrix to get the output matrix as shown below. Here is how the Output Matrix is calculated:
![Convolution Output1](http://machinelearninguru.com/_images/topics/computer_vision/basics/convolution/3.JPG)
![Convolution Output2](http://machinelearninguru.com/_images/topics/computer_vision/basics/convolution/4.JPG)
We will see below how different Kernels affect the output image after the process of convolution takes place.
___
### Filters/Kernels
Kernels or filters are small matrices that are used to apply some effects on the target image(matrix). The process of using these Kernels(matrix) and applying them on the target image is known as Convolution. The Kernel is a square matrix generally having odd number of rows and columns (3x3, 5x5, 7x7 ..). We use different types of kernels to apply different types of effects on the final output image like blurring, sharpening, outlining or embossing. These are also used in machine learning for extracting features from an image. Some common kernels can be found [here](https://en.wikipedia.org/wiki/Kernel_(image_processing)). Following are some of the examples: 
  
__Simple Blur__  
![Simple Blur](http://aishack.in/static/img/tut/conv-simple-blur-result1.jpg)  
__Line Detection__  
![Line Detection](http://aishack.in/static/img/tut/conv-line-detection-horizontal-result.jpg)  
__Edge Detection__  
![Edge Detection](http://aishack.in/static/img/tut/conv-edge-detection-result.jpg)
___
### Epochs
An epoch describes the number of times our algorithm has went over the whole dataset. Once our algorithm has seen all the samples(batches) from our dataset, we can say that an epoch has been completed. Generally, training a neural network involves multiple epochs to be completed.
___
### 1x1 Convolution
Convolving an image with a 1x1(WXH) filter is called 1x1 Convolution. This process is used to control the depth of the input image, either increase it or decrease it, as it is passed to the next layer. But in general we use it for reducing the dimension just before the more computationally costly convolutions (3x3, 5x5..). Let's take an example where we take a 6x6 image with three color channels (depth = 3). Then we take a 1x1x3 filter (Here 3 is the depth which is variable as per input image. Depth of the filter is always same as the input image), we can see the output below:
![1x1 Convolution | Single Filter](https://qph.fs.quoracdn.net/main-qimg-3d412cacb0435a8e56eda709ae26795f)

Here, by increasing the number of such filters used we can control the depth of the output. Say, if we used 2 such filters:
![1x1 Convolution | 2 Filters](https://qph.fs.quoracdn.net/main-qimg-0b3c4bbc86cc5c73efb8dbf2c699265a)

We can see from the below images, how 1x1 reduces the computational cost significantly. First lets see the case where we use a 5x5 filter and 32 is the number of filters used:
![Computational Cost - 5x5 Convolution](https://qph.fs.quoracdn.net/main-qimg-7df9c28f92d879d9f9e6d25f6f991a1e)
We can see above that ~120 Million computational steps was required. Now let's pass a 1x1 filter(16 number of filters) just before this process:
![Computational Cost - 1x1 and 5x5 Filter together](https://qph.fs.quoracdn.net/main-qimg-93361dde6ee02fb428e5df5416718c0c)
As we can see in the above image. Computational cost was reduced from ~120 Million to ~12.4 Million.
___
#### References
- [Ludwig_ImageConvolution.ppt](http://web.pdx.edu/~jduh/courses/Archive/geog481w07/Students/Ludwig_ImageConvolution.pdf)
- [How Blurs & Filters Work - Computerphile](https://www.youtube.com/watch?v=C_zFhWdM4ic)
- [Applications of Convolution in Image Processing Dhruv](https://www.youtube.com/watch?v=BQyMZ0caFbg)
- [Image Filtering](http://machinelearninguru.com/computer_vision/basics/convolution/image_convolution_1.html)
- [Image Kernels](http://setosa.io/ev/image-kernels/)
- [Basic Image Processing](https://users.itk.ppke.hu/kep/Lectures/IPA_02_Convolution.pdf)
- [What is a 1x1 convolution - Quora](http://qr.ae/TUGNbk)
___
#### Doubts
- Does the size of the filters we use, always same as that of the input image?