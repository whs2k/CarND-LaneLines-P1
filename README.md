# **Finding Lane Lines on the Road** 
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

![Alt Text](https://github.com/whs2k/findingLaneLines/blob/master/test_videos/Solid_Yellow_Left.gif?raw=true)
![Alt Text](https://media.giphy.com/media/vFKqnCdLPNOKc/giphy.gif)
![Alt Text](https://github.com/whs2k/findingLaneLines/blob/master/test_videos/Solid_Yellow_Left_Original.gif?raw=true)



Project WriteUp
---

### 1. The Pipeline
This project used a series of transformations (five) and masks (two) to detect and draw lane lines on an image or series of images (videso). The Pipeline was as follows:
  1. Import image `matplotlib.image`
  2. Transform Image to Greyscale `cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)`
  3. Identify Edges with Canny Function `cv2.Canny(img, low_threshold, high_threshold)`
  4. Gaussian Smoothing `cv2.GaussianBlur(img, (kernel_size, kernel_size), 0)`
  5. Create an Mask of the Region of Interest `line_img = region_of_interest(line_img, v)`
  6. Draw Hough Lines on the Image 
      `cv2.HoughLinesP(mask, 0.8, np.pi/180, 25, np.array([]), minLineLength=50, maxLineGap=200)`
  7. Combine Mask w/Lines and Original Image `weighted_img(line_img, image)`

### 2. Shortcomings
Two issues plagued me during this project. Other than the obvious frustration that acompangies installing new packages (sike: pip and homebrew make movie and cv installation a breeze), I received a constant error message when creating my pipeline: `TypeError: 'numpy.ndarray' object is not callable weighted_img`

After StackOverflow was surprisingly unhelpful, it took me a few retries and kernel restarts to figure out that you only should process each image and create each mask once, as additional processing is not done on the original image. Watch yout for your global variables; there are lots of functions that use the word 'image.'

### 3. Improvements
More Challenging Videos please! Anything offroad to test? How about some collisions (morbid as that is) to see what happens to the algos when they are really stretched. Great first project, excited for more!

---
Original Prompt
---

When we drive, we use our eyes to decide where to go.  The lines on the road that show us where the lanes are act as our constant reference for where to steer the vehicle.  Naturally, one of the first things we would like to do in developing a self-driving car is to automatically detect lane lines using an algorithm.

In this project you will detect lane lines in images using Python and OpenCV.  OpenCV means "Open-Source Computer Vision", which is a package that has many useful tools for analyzing images.  

To complete the project, two files will be submitted: a file containing project code and a file containing a brief write up explaining your solution. We have included template files to be used both for the [code](https://github.com/udacity/CarND-LaneLines-P1/blob/master/P1.ipynb) and the [writeup](https://github.com/udacity/CarND-LaneLines-P1/blob/master/writeup_template.md).The code file is called P1.ipynb and the writeup template is writeup_template.md 

To meet specifications in the project, take a look at the requirements in the [project rubric](https://review.udacity.com/#!/rubrics/322/view)

## If you have already installed the [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md) you should be good to go!   If not, you should install the starter kit to get started on this project. ##

**Step 1:** Set up the [CarND Term1 Starter Kit](https://classroom.udacity.com/nanodegrees/nd013/parts/fbf77062-5703-404e-b60c-95b78b2f3f9e/modules/83ec35ee-1e02-48a5-bdb7-d244bd47c2dc/lessons/8c82408b-a217-4d09-b81d-1bda4c6380ef/concepts/4f1870e0-3849-43e4-b670-12e6f2d4b7a7) if you haven't already.

**Step 2:** Open the code in a Jupyter Notebook

You will complete the project code in a Jupyter notebook.  If you are unfamiliar with Jupyter Notebooks, check out <A HREF="https://www.packtpub.com/books/content/basics-jupyter-notebook-and-python" target="_blank">Cyrille Rossant's Basics of Jupyter Notebook and Python</A> to get started.

Jupyter is an Ipython notebook where you can run blocks of code and see results interactively.  All the code for this project is contained in a Jupyter notebook. To start Jupyter in your browser, use terminal to navigate to your project directory and then run the following command at the terminal prompt (be sure you've activated your Python 3 carnd-term1 environment as described in the [CarND Term1 Starter Kit](https://github.com/udacity/CarND-Term1-Starter-Kit/blob/master/README.md) installation instructions!):

`> jupyter notebook`

A browser window will appear showing the contents of the current directory.  Click on the file called "P1.ipynb".  Another browser window will appear displaying the notebook.  Follow the instructions in the notebook to complete the project.  

**Step 3:** Complete the project and submit both the Ipython notebook and the project writeup

## How to write a README
A well written README file can enhance your project and portfolio.  Develop your abilities to create professional README files by completing [this free course](https://www.udacity.com/course/writing-readmes--ud777).

