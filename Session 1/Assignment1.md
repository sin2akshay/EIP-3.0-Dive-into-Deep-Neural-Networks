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
### Convolution
In image processing, by convolution we mean, putting a matrix over another and then calculating the weighted sum of all pixel values. One of these matrices is an image and the other one is a kernel matrix. The kernel matrix is generally smaller than the image (3x3 is the standard).
![Convolution](http://machinelearninguru.com/_images/topics/computer_vision/basics/convolution/1.JPG)

The Kernel matrix is moved over the image matrix to get the output matrix as shown below. Here is how the Output Matrix is calculated:
![Convolution Output1](http://machinelearninguru.com/_images/topics/computer_vision/basics/convolution/3.JPG)
![Convolution Output2](http://machinelearninguru.com/_images/topics/computer_vision/basics/convolution/4.JPG)
We will see below how different Kernels affect the output image after the process of convolution takes place.
___
### Filters/Kernels
Kernels or filters are small matrices that are used to apply some effects on the target image(matrix). The process of using these Kernels(matrix) and applying them on the target image is known as Convolution. The Kernel is a square matrix generally having odd number of rows and columns (3x3, 5x5, 7x7 ..). We use different types of kernels to apply different types of effects on the final output image like blurring, sharpening, outlining or embossing. These are also used in machine learning for extracting features from an image. Following are some of the examples:  
__Simple Blur__
![Simple Blur](http://aishack.in/static/img/tut/conv-simple-blur-result1.jpg)  
__Line Detection__
![Line Detection](http://aishack.in/static/img/tut/conv-line-detection-horizontal-result.jpg)  
__Edge Detection__
![Edge Detection](http://aishack.in/static/img/tut/conv-edge-detection-result.jpg)
___

___
#### References
- [Ludwig_ImageConvolution.ppt](http://web.pdx.edu/~jduh/courses/Archive/geog481w07/Students/Ludwig_ImageConvolution.pdf)
- [How Blurs & Filters Work - Computerphile](https://www.youtube.com/watch?v=C_zFhWdM4ic)
- [Applications of Convolution in Image Processing Dhruv](https://www.youtube.com/watch?v=BQyMZ0caFbg)
- [Image Filtering](http://machinelearninguru.com/computer_vision/basics/convolution/image_convolution_1.html)
- [Image Kernels](http://setosa.io/ev/image-kernels/)
