##Writeup Template
###You can use this file as a template for your writeup if you want to submit it as a markdown file, but feel free to use some other method and submit a pdf if you prefer.

---

**Vehicle Detection Project**

The goals / steps of this project are the following:

* Perform a Histogram of Oriented Gradients (HOG) feature extraction on a labeled training set of images and train a classifier Linear SVM classifier
* Optionally, you can also apply a color transform and append binned color features, as well as histograms of color, to your HOG feature vector. 
* Note: for those first two steps don't forget to normalize your features and randomize a selection for training and testing.
* Implement a sliding-window technique and use your trained classifier to search for vehicles in images.
* Run your pipeline on a video stream (start with the test_video.mp4 and later implement on full project_video.mp4) and create a heat map of recurring detections frame by frame to reject outliers and follow detected vehicles.
* Estimate a bounding box for vehicles detected.

[//]: # (Image References)
[image1]: ./examples/car_not_car.png
[image2]: ./examples/HOG_example.jpg
[image3]: ./examples/sliding_windows.jpg
[image4]: ./examples/sliding_window.jpg
[image5]: ./examples/bboxes_and_heat.png
[image6]: ./examples/labels_map.png
[image7]: ./examples/output_bboxes.png
[video1]: ./project_video.mp4

## [Rubric](https://review.udacity.com/#!/rubrics/513/view) Points
###Here I will consider the rubric points individually and describe how I addressed each point in my implementation.  

---
###Writeup / README

####1. Provide a Writeup / README that includes all the rubric points and how you addressed each one.  You can submit your writeup as markdown or pdf.  [Here](https://github.com/udacity/CarND-Vehicle-Detection/blob/master/writeup_template.md) is a template writeup for this project you can use as a guide and a starting point.  

You're reading it!

###Histogram of Oriented Gradients (HOG)

####1. Explain how (and identify where in your code) you extracted HOG features from the training images.

The first thing in the file was to install and the dependencies, extract all the images and save them into variables that are used throughout the entire project. After the initial setup, I went ahead and created the funtions: `get_hog_features` cell 3, `bin_spatial` cell 4, `color_hist` cell 5. I tested the hog funtion to see whether or not the output was correct and saved the image in the `output_images` directory. The image is chosen randomly and the `get_hog_function` is applied to the selected picture.

####2. Explain how you settled on your final choice of HOG parameters.

Various combinations of hog parameters were tested, but the one I chose was based on another student who cleverly tested each individual parameter and had the highest return accuracy. I try to give him the credit if I find his github becuase it was cleverly designed.

####3. Describe how (and identify where in your code) you trained a classifier using your selected HOG features (and color features if you used them).

The classifier was trained on cell 16 after most of the essential functions were created and ready to use. I thought about limiting the sample size to 2000 but the actual size of the entire classifier is not that big and decided to went along and train the entire thing, even though it took a little longer.

###Sliding Window Search

####1. Describe how (and identify where in your code) you implemented a sliding window search.  How did you decide what scales to search and how much to overlap windows?

The `slide_window` function was created in cell 10. The default overlap was set for 0.5 but I went back and forth between 0.5 & 0.8. I think I got the best result from a scale of 1.5 since it changes the scale of the scale measurement. A copy of the result of this can be found on cell 20.

####2. Show some examples of test images to demonstrate how your pipeline is working.  What did you do to optimize the performance of your classifier?

My pipeline goes search windows, marks the hot ones, draws them, takes the heatmap and returns the normal image. All images can be found in the notebook.

---

### Video Implementation

####1. Provide a link to your final video output.  Your pipeline should perform reasonably well on the entire project video (somewhat wobbly or unstable bounding boxes are ok as long as you are identifying the vehicles most of the time with minimal false positives.)

Copy of the video can be found in the `test_video` directory.


####2. Describe how (and identify where in your code) you implemented some kind of filter for false positives and some method for combining overlapping bounding boxes.

My pipeline interates through various locations of the frame and also changes the scale of the frames. I saved the amount of boxes saved that were found in the heatmap and returned in an array.



---

###Discussion

####1. Briefly discuss any problems / issues you faced in your implementation of this project.  Where will your pipeline likely fail?  What could you do to make it more robust?

Here I'll talk about the approach I took, what techniques I used, what worked and why, where the pipeline might fail and how I might improve it if I were going to pursue this project further.  

