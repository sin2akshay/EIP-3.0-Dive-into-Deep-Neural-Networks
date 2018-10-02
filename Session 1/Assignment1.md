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

### Convolution
In neural networks, by convolution we mean, putting a matrix over another and then calculating the weighted sum of all pixel values. One of these matrices is an image and the other one is a kernel matrix. The kernel matrix is generally smaller than the image (3x3 is the standard).
![Convolution](http://machinelearninguru.com/_images/topics/computer_vision/basics/convolution/1.JPG)

The Kernel matrix is moved over the image/channel to get the output as shown below. Here is how the Output Matrix/channel is calculated:
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
### 3x3 Convolution
3x3 Convolution is the process of applying a 3x3 filter to the image. To deal with the depth and large number of computational steps required, people nowadays use 3x3 convolutions exclusively. When stacked together, they act as a larger receptive field as you can see in the image below. The 2nd convulation layer sees the image just like 5x5 layer convulation output layer.  
![3x3 Convolution](https://raw.githubusercontent.com/sin2akshay/EIP2-MLBLR/master/Session%201/_files/3x3Convolution.JPG)  

Here you can see how each pixel on the First Convulation output sees a 3x3 area from input image. Then each pixel on the second convolution sees the pixel on first convolution making the stack behave like a 5x5 filter and also reducing the computational cost which we will see below.  
![3x3 Convolution Stacked](https://github.com/sin2akshay/EIP2-MLBLR/blob/master/Session%201/_files/3x3Stacked.png?raw=true)  

Suppose we have an input image of dimensions HxWxC and we use convolutions with C number of filters to keep the depth same. Comparing the compuational cost between using a 7x7 convolution vs a 3 stack of 3x3 convolutions:  
![3x3 Convulution Stacked vs 7x7 Convolution](https://github.com/sin2akshay/EIP2-MLBLR/blob/master/Session%201/_files/3x3StackComputation.JPG?raw=true)
___
### Feature Maps
A feature map is a mapping of the location of certain feature in an image.  
![Feature Maps](https://github.com/sin2akshay/EIP2-MLBLR/blob/master/Session%201/_files/Feature%20Maps.JPG?raw=true)  
In easier words, a feature map is produced when convolution is applied to the input data using a convolution filter. Suppose we have an input and 3x3 filter/kernel as shown below:  
![Input matrix and kernel matrix](https://cdn-images-1.medium.com/max/800/1*cTEp-IvCCUYPTT0QpE3Gjg@2x.png)  
We do the convolution using this filter and moving it over the input. The result goes into the feature map (3x3 matrix on right side) as shown below:  
![Animation | Feature Maps](https://cdn-images-1.medium.com/max/800/1*VVvdh-BUKFh2pwDD0kPeRA@2x.gif)  
We perform multiple convolutions on the input image using different filters to generate different feature maps. These feature maps are stacked together to become the output convolution layer.

___
### Feature Engineering
The success of our machine learning algorithm depends on how well we present the data to it. Algorithms cannot work on the data directly to give the desired results. They are not intelligent enough to extract the correct and meaningful features from our input data, hence the need for Feature Engineering. It is the process of transforming the raw data into meaningful features that better represents our problem. This results in our algorithm performing with greater accuracy to solve the problem. we redo the process until we get the desired accuracy from our model.

![Feature Engineering](https://raw.githubusercontent.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/master/Session%201/_files/featureengg.jpg)

___

## BONUS QUESTIONS

### Activation Function
In an Artificial Neural Network, the activation function of a neuron defines the output of that neuron given a set of inputs.

To understand this, we can say that this activation function is biologically inspired by the activities in our brain, where different neurons are fired/activated by different stimuli.

![Neurons being activated by different stimuli](https://raw.githubusercontent.com/sin2akshay/External-Internship-Program-2.0-Machine-Learning-for-Deep-Neural-Networks/master/Session%201/_files/neuron.jpg)  

For each different stimuli certain neurons fire. So within our brain, neurons are either firing or they are not. We can interpret this as a binary 'on' or 'off', 0 or 1. In sigmoid activation function the neuron can be between 0 and 1. So the more closer to 1, the more activated that neuron is and the closer to 0, the less activated that neuron is.   

However, one of the most commonly used activation function ReLu(Rectified Liner Unit) transforms the input to the maximum of either 0 or the input itself. So, if input <= 0, then ReLu will transform the input to be 0 and if the number is > 0 then ReLu will just output the given input.


___
### How to create an account on GitHub and upload a sample project
GitHub is an online browser based distributed version control system for software developers using the Git revision control system.

#### Creating a [GitHub](https://github.com/) account

GitHub is a web-based hosting service for version control using Git. It is most popular version control service in use right now. There are many alternatives that use Git to do version control but we will focus here on GitHub. To create an account:

1. Open [GitHub](https://github.com/). Enter a username, valid email address, and password as shown and then Click on the 'Sign up for GitHub' button.  
![Github1](https://1.bp.blogspot.com/-bC63hPldlrA/W7OmCTSS0hI/AAAAAAAAXYY/xcZzGvMNtisisYE3JJlCou6YvHXjAmXLACLcBGAs/s640/Github2.png)  
2. You will be redirected to the below shown page. Here you might be asked to solve a simple puzzle to prove that you are a real person. Complete the puzzle and click the 'Create an account' button.  
![Github2](https://4.bp.blogspot.com/-u8RinxNBa3A/W7OmCTytVkI/AAAAAAAAXYc/Fz_-ZSmhZJwRqPwyIoRHRgWHAJ5TPsr-wCLcBGAs/s640/Github3.png)  
3. In the next screen you will be asked to choose your personal plan. We will leave it at default which is free. Leave the 2 checkboxes on bottom unchecked and click on the 'Continue' button.  
4. In the third screen you will be asked to select you interests, it is also optional and can be skipped. Click Continue and Congratulations! Your GitHub account has been created.  


#### Uploading a sample project

Now, let's upload a sample project to the GitHub account we just created. There is an excellent intro guide for GitHub in this [link](https://guides.github.com/activities/hello-world/). You can use the GitHub website to create a repository and upload your project files. You can also upload your project via Command line as shown [here](https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line/). But for the simplicity, we are going to do it via GitHub Desktop.

1. Go to https://desktop.github.com/ and Download GitHub Desktop for whichever platform you are using.
![GitHubDesktop](https://3.bp.blogspot.com/-zDuWmin-cEA/W7PEbbfmo5I/AAAAAAAAXZI/vqnpGgQghKYA5icx-YHR5qSDh2fHKUsCQCLcBGAs/s640/GithubDesktop1.png)
2. Install the software using the downloaded setup and open GitHub Desktop.
3. Now to upload a project, first we need to create a repository. Click on File > New Repository inside GitHub Desktop. Select the local path where your project is or just give a path here and move your files to it later. Here we will move project files to it later.  
![](https://1.bp.blogspot.com/-NN7g3nT1wU4/W7PEbTNxwuI/AAAAAAAAXY8/cR5Zh6KgrIwHR3DHFSCwlZQmePL08_PtQCLcBGAs/s640/GithubDesktop2.png)  
4. After filling all the details, click the Create Repository button. Now this repository has been created into your local. To make it available on GitHub.com, you will have to Publish this repository. Click on the Publish repository button on top right on which you will get the below screen.
![](https://4.bp.blogspot.com/-qHyG-0xGz_Q/W7PEdUv7mMI/AAAAAAAAXZY/KcIa61alkFo8nENHkPpKvU__-1nWXutMQCLcBGAs/s640/GithubNew3.png)  
5. Uncheck the Keep Code Private checkbox (Premium user feature) and click the 'Publish repository button. Your repository has been published to your GitHub account. To check go to GitHub.com and login to your account. After logging in, click on your avatar on the right and select 'Your Repositories'   ![](https://2.bp.blogspot.com/-Uh6leW6Iiyk/W7PEdy2oAPI/AAAAAAAAXZc/eMpLhgiGsBkxr7GRArIyKnBq3Oy-bG8CACLcBGAs/s320/GithubNew5.png)  
6. Now as you can see, your repository has been created:  
![](https://1.bp.blogspot.com/-VtydBJppzxQ/W7PEbd8b4kI/AAAAAAAAXZA/5y8k0DCw0oUVBQKtZqHR-EVCb0CeEvcDgCLcBGAs/s640/GitHubNew4.png)  
7. Let's add some files to this repository. Go to the project/repository path and add your project files. Now go to GitHub Desktop. There you will see the list of changes. On the bottom there is a box to feel Commit message and description, fill it. Now we will commit it to master (since we have no branches, we are only using master here), click the Commit to master button.  
![](https://2.bp.blogspot.com/-X9oO2MzqFLM/W7PEeHvOCcI/AAAAAAAAXZg/bK8Zd54orqsP9CGVCASHivOuwcbT3jBdACLcBGAs/s640/GithubNew6.png)  
8. Now your commit has been made but we still have to push the change to our GitHub.com repository. In the History tab you can see all the commits and on the top right you can see that it is showing 1 commit needs to be pushed. Click on the Push Origin button.  
![](https://4.bp.blogspot.com/-BQ86piRZSXU/W7PEetcYPHI/AAAAAAAAXZo/b617KH7xcE8sD21K4Ya-Xmqj2vhW7wFhACLcBGAs/s640/GithubNew7.png)  
9. Now refresh the repository page and you will be able to see the changes available on Github.com. Congratulations, you just learnt to upload a project to GitHub.
![](https://4.bp.blogspot.com/-diiCeQrBj4w/W7PEejb-LjI/AAAAAAAAXZk/5pAJtOu4IHIHH56jYY_tmNyb-pTYKkfoQCLcBGAs/s640/GithubNew8.png)

___
### Receptive Field

A receptive field in a CNN is a part of the input image, i.e. pixel grid that is visible to a feature/kernel during the sliding/convolution operation.

When dealing with higher order input such as images it is not possible to connect all neurons with each other. Instead we connect each neuron to a local region of input space.

Receptive field is the region of input space that a particular feature is looking. Every neuron in conv layer represents a filter applied to previous layer. The area of the previous layer that this filter is applied to is called receptive field of that layer. This receptive field increases as we stack more conv layers.

___
### 10 examples of use of MathJax in Markdown

**1. Matrices**
- Code:
`
    \begin{matrix}
    1 & x & x^2 \\
    1 & y & y^2 \\
    1 & z & z^2 \\
    \end{matrix}
`
- MathJax:
$$
    \begin{matrix}
    1 & x & x^2 \\
    1 & y & y^2 \\
    1 & z & z^2 \\
    \end{matrix}
$$

**2. Definitions by cases (piecewise functions)**
- Code:
`
f(n) =
\begin{cases}
n/2,  & \text{if $n$ is even} \\
3n+1, & \text{if $n$ is odd}
\end{cases}
`
- MathJax:
$$
f(n) =
\begin{cases}
n/2,  & \text{if $n$ is even} \\
3n+1, & \text{if $n$ is odd}
\end{cases}
$$

**3. System of equations**
- Code:
`
\left\{
\begin{array}{c}
a_1x+b_1y+c_1z=d_1 \\
a_2x+b_2y+c_2z=d_2 \\
a_3x+b_3y+c_3z=d_3
\end{array}
\right.
`
- MathJax:
$$
\left\{
\begin{array}{c}
a_1x+b_1y+c_1z=d_1 \\
a_2x+b_2y+c_2z=d_2 \\
a_3x+b_3y+c_3z=d_3
\end{array}
\right.
$$

**4. Pythagorean Theorem if $x$ and $y$ two vectors such that $x\bot y$ :**
- Code:
`
\lVert x+y \rVert^2 = \lVert x \rVert^2 + \lVert y \rVert^2
`
- MathJax:
$$
\lVert x+y \rVert^2 = \lVert x \rVert^2 + \lVert y \rVert^2
$$

**5. Quadratic formula When $a≠0$, there are two solutions to $ax^2+bx+c=0$ and they are**
- Code:
`
x = {-b \pm \sqrt{b^2-4ac} \over 2a}
`
- MathJax:
 $$
 x = {-b \pm \sqrt{b^2-4ac} \over 2a}
 $$

**6. Square expansion**
- Code:
`
(a+b)^2 = a^2 + b^2+ 2ab
`
- MathJax:
$$
(a+b)^2 = a^2 + b^2+ 2ab
$$


**7. Difference of squares**
- Code:
`
(a+b)(a-b) = a^2-b^2
`
- MathJax:
$$
(a+b)(a-b) = a^2-b^2
$$


**8. Logarithm**
- Code:
`
$y = \log_{b}(x)$ if and only if $x = b^y$ and $b\neq0$
`
- MathJax:
$y = \log_{b}(x)$ if and only if $x = b^y$ and $b\neq0$


**9. Sum of square of n natural numbers**
- Code:
`
S_n^2 = \sum n(n+1)(2n+1)/6
`
- MathJax:
$$
S_n^2 = \sum n(n+1)(2n+1)/6
$$

**10. Convolution on two function**
- Code:
`
(fg)(c) = \sum_{a} f(a).g(c-a)$$ $$or$$ $$(fg)(c) = \int_{-\infty}^{\infty}f(a).g(c-a)dc
`
- MathJax:
$$(fg)(c) = \sum_{a} f(a).g(c-a)$$ $$or$$ $$(fg)(c) = \int_{-\infty}^{\infty}f(a).g(c-a)dc$$
___
#### References
- [Ludwig_ImageConvolution.ppt](http://web.pdx.edu/~jduh/courses/Archive/geog481w07/Students/Ludwig_ImageConvolution.pdf)
- [How Blurs & Filters Work - Computerphile](https://www.youtube.com/watch?v=C_zFhWdM4ic)
- [Applications of Convolution in Image Processing Dhruv](https://www.youtube.com/watch?v=BQyMZ0caFbg)
- [Image Filtering](http://machinelearninguru.com/computer_vision/basics/convolution/image_convolution_1.html)
- [Image Kernels](http://setosa.io/ev/image-kernels/)
- [Basic Image Processing](https://users.itk.ppke.hu/kep/Lectures/IPA_02_Convolution.pdf)
- [What is a 1x1 convolution - Quora](http://qr.ae/TUGNbk)
- [A Beginner's Guide To Understanding Convolutional Neural Networks](https://adeshpande3.github.io/adeshpande3.github.io/A-Beginner%27s-Guide-To-Understanding-Convolutional-Neural-Networks/)
- [Deep Learning: Practice and Trends (NIPS 2017 Tutorial, parts I & II)](https://www.youtube.com/watch?v=YJnddoa8sHk&feature=youtu.be&t=1140)
- CS231n Lecture 11 - ConvNets in practice [[Video]](https://youtu.be/dUTzeP_HTZg?t=1513) [[Lecture Notes - Page 40]](http://cs231n.stanford.edu/slides/2016/winter1516_lecture11.pdf)
- [Applied Deep Learning - Part 4: Convolutional Neural Networks](https://towardsdatascience.com/applied-deep-learning-part-4-convolutional-neural-networks-584bc134c1e2)
- [MathJax basic tutorial and quick reference](https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference)
___
#### Doubts
- Does the depth of the convolution filter always matches the depth of the image?
- Are all the filters same or different while convolving. Means if we are using 10 numbers of 3x3 filters, are all 10 different and would be giving different feature maps as output?
- How do you know that at this layer we would use Max Pooling, instead of 3x3 convolution?
- The notes mention,"We must add as many layers as needed to reach the required receptive field, and as we have learned, each time we add a convolution layer, our receptive field increases by 2x2. " Is this true? Even if we add a single 3x3 layer the output matrix would be generated after going through all the pixels of the input image.
