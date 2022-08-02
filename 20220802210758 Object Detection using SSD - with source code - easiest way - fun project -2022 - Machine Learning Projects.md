---
title: Object Detection using SSD - with tags: android blog rtrvl
author: retr0ville
source: 
source: https://machinelearningprojects.net/object-detection-using-ssd/
---
Object Detection using SSD - with source code - easiest way - fun project -2022 - Machine Learning Projects Skip to content  
[![Machine Learning Projects](https://machinelearningprojects.net/wp-content/uploads/2021/06/cropped-logo_transparent-1-65x65.png)](https://machinelearningprojects.net/)  
[Machine Learning Projects](https://machinelearningprojects.net/)

Find your next ML project here...  
* [Projects](https://machinelearningprojects.net/projects/)Menu Toggle
  * [Machine Learning Projects with Source Code](https://machinelearningprojects.net/machine-learning-projects/)
  * [Deep Learning Projects with Source Code](https://machinelearningprojects.net/deep-learning-projects/)
  * [Computer Vision Projects with Source Code](https://machinelearningprojects.net/opencv-projects/)
  * [Flask Projects with Source Code](https://machinelearningprojects.net/flask-projects/)
  * [NLP Projects with Source Code](https://machinelearningprojects.net/nlp-projects/)
* [Study](https://machinelearningprojects.net/handwritten-data-science-notes/)Menu Toggle
  * [Data Science Resources](https://machinelearningprojects.net/data-science-resources/)
  * [Handwritten Data Science Notes](https://machinelearningprojects.net/handwritten-data-science-notes/)
* [AWS](https://machinelearningprojects.net/aws/)
* [Blog](https://machinelearningprojects.net/blog/)
* [About](https://machinelearningprojects.net/about/)
* [Newsletter](https://forms.gle/8qhFGfY3qGZz9X6u9)  
Search for:  
Search  
[![Machine Learning Projects](https://machinelearningprojects.net/wp-content/uploads/2021/06/cropped-logo_transparent-1-65x65.png)](https://machinelearningprojects.net/)  
[Machine Learning Projects](https://machinelearningprojects.net/)

Find your next ML project here...  
Main Menu  
* [Projects](https://machinelearningprojects.net/projects/)Menu Toggle
  * [Machine Learning Projects with Source Code](https://machinelearningprojects.net/machine-learning-projects/)
  * [Deep Learning Projects with Source Code](https://machinelearningprojects.net/deep-learning-projects/)
  * [Computer Vision Projects with Source Code](https://machinelearningprojects.net/opencv-projects/)
  * [Flask Projects with Source Code](https://machinelearningprojects.net/flask-projects/)
  * [NLP Projects with Source Code](https://machinelearningprojects.net/nlp-projects/)
* [Study](https://machinelearningprojects.net/handwritten-data-science-notes/)Menu Toggle
  * [Data Science Resources](https://machinelearningprojects.net/data-science-resources/)
  * [Handwritten Data Science Notes](https://machinelearningprojects.net/handwritten-data-science-notes/)
* [AWS](https://machinelearningprojects.net/aws/)
* [Blog](https://machinelearningprojects.net/blog/)
* [About](https://machinelearningprojects.net/about/)
* [Newsletter](https://forms.gle/8qhFGfY3qGZz9X6u9)  

Object Detection using SSD -- with source code -- easiest way -- fun project --2022
===================================================================================

By [Abhishek Sharma](https://machinelearningprojects.net/author/sharmaji27/ "View all posts by Abhishek Sharma") / August 21, 2021 February 23, 2022 / [Machine Learning](https://machinelearningprojects.net/category/machine-learning/), [Computer Vision](https://machinelearningprojects.net/category/opencv/)  
![](https://machinelearningprojects.net/wp-content/uploads/2022/02/Object-Detection-using-SSD-1024x536.png)  
So guys in today's blog we will see how can we perform Object Detection using SSD in the simplest way possible. SSDs are very fast in Object Detection when compared to those big boys like R-CNN or Fast R-CNN, etc. This is going to be a very fun project with endless use cases. So without any further due.  
Table of Contents

* Let's do it...
  * Create a conda environment and install required libraries
  * Code for Object Detection using SSD...
* Download files for Object Detection using SSD...

### Let's do it...

#### Create a conda environment and install required libraries

    conda create -n od python=3.9
    conda activate od
    pip install opencv-python numpy imutils
#### Code for Object Detection using SSD...

```
from imutils.video import FPS
import numpy as np
import imutils
import cv2


use_gpu = True
live_video = False
confidence_level = 0.5
fps = FPS().start()
ret = True
CLASSES = ["background", "aeroplane", "bicycle", "bird", "boat",
           "bottle", "bus", "car", "cat", "chair", "cow", "diningtable",
           "dog", "horse", "motorbike", "person", "pottedplant", "sheep",
           "sofa", "train", "tvmonitor"]

COLORS = np.random.uniform(0, 255, size=(len(CLASSES), 3))

net = cv2.dnn.readNetFromCaffe('ssd_files/MobileNetSSD_deploy.prototxt', 'ssd_files/MobileNetSSD_deploy.caffemodel')

if use_gpu:
    print("[INFO] setting preferable backend and target to CUDA...")
    net.setPreferableBackend(cv2.dnn.DNN_BACKEND_CUDA)
    net.setPreferableTarget(cv2.dnn.DNN_TARGET_CUDA)


print("[INFO] accessing video stream...")
if live_video:
    vs = cv2.VideoCapture(0)
else:
    vs = cv2.VideoCapture('test.mp4')

while ret:
    ret, frame = vs.read()
    if ret:
        frame = imutils.resize(frame, width=400)
        (h, w) = frame.shape[:2]

        blob = cv2.dnn.blobFromImage(frame, 0.007843, (300, 300), 127.5)
        net.setInput(blob)
        detections = net.forward()

        for i in np.arange(0, detections.shape[2]):
            confidence = detections[0, 0, i, 2]
            if confidence > confidence_level:
                idx = int(detections[0, 0, i, 1])
                box = detections[0, 0, i, 3:7] * np.array([w, h, w, h])
                (startX, startY, endX, endY) = box.astype("int")

                label = "{}: {:.2f}%".format(CLASSES[idx], confidence * 100)
                cv2.rectangle(frame, (startX, startY), (endX, endY), COLORS[idx], 2)

                y = startY - 15 if startY - 15 > 15 else startY + 15
                cv2.putText(frame, label, (startX, y), cv2.FONT_HERSHEY_SIMPLEX, 0.5, COLORS[idx], 2)
                
        cv2.imshow('Live detection',frame)

        if cv2.waitKey(1)==27:
            break

        fps.update()

fps.stop()

print("[INFO] elasped time: {:.2f}".format(fps.elapsed()))
print("[INFO] approx. FPS: {:.2f}".format(fps.fps()))
```

* Line 1-5 -- Importing libraries required for Object Detection using SSD.
* Line 7-15 -- Defining some constants and **Classes**array. Our SSD model is trained on these 21 classes.
* Line 17 -- Defining colors array where each class is randomly assigned a color.
* Line 19 -- Reading the network in a variable called net using [cv2.dnn.readNetFromCaffe](https://docs.opencv.org/3.4/d6/d0f/group__dnn.html#ga29d0ea5e52b1d1a6c2681e3f7d68473a).
* Line 21-24 -- If the parameter use_gpu is set to TRUE, set the backend and target to Cuda.
* Line 27-31 -- Initialize the [VideoCapture](https://docs.opencv.org/3.4/d8/dfe/classcv_1_1VideoCapture.html)object either with 0 for live video or with the video file name.
* Line 34 -- Let's get in the infinite array and read the frames.
* Line 35 -- If ret says that if the [VideoCapture](https://docs.opencv.org/3.4/d8/dfe/classcv_1_1VideoCapture.html)object is returning True, then only proceed.
* Line 36-37 -- Resize the frame and get its height and width.
* Line 39-41 -- Create a blob from the image, set it as input, and pass it forward through the network using [cv2.blobFromImage](https://docs.opencv.org/4.5.2/d6/d0f/group__dnn.html#ga29f34df9376379a603acd8df581ac8d7).
* Line 43 -- Let's traverse in the detections we got.
* Line 44 -- Let's check the confidence of each and every detection.
* Line 45 -- If the confidence is greater than a threshold then proceed.
* Line 47-48 -- Calculate the coordinates of the box and convert them to int.
* Line 50 -- Creating text like **'Class_name: confidence%'**.
* Line 51 -- Drawing the rectangle around the found object.
* Line 53-54 -- Finally putting this label onto the original frame.
* Line 56 -- Show final results.
* Line 58-59 -- Break if someone hits the ESC key.
* Line 61 -- Update the fps counter.
* Line 63 -- Stop the fps counter.
* Line 65-66 -- Printing FPS metrics.

![Object Detection using SSD](https://machinelearningprojects.net/wp-content/uploads/2021/08/1-1.png)  

**NOTE -- You will see some results like these after the successful execution of the code. I am using GPU that's why FPS is quite high but if you are not using GPU, you might see lower FPS.**

### *[Download files for Object Detection using SSD...](https://machinelearningprojects.net/wp-content/uploads/2021/07/source%20codes/Object%20Detection%20using%20SSD.zip)*

Do let me know if there's any query regarding Object Detection using SSD by contacting me on email or LinkedIn.

*So this is all for this blog folks, thanks for reading it and I hope you are taking something with you after reading this and till the next time ?...*

***Read my previous post:*** ***[SOCIAL DISTANCING USING YOLOV3](https://machinelearningprojects.net/social-distancing-using-yolov3/)***

**Check out my other [machine learning projects](https://machinelearningprojects.net/machine-learning-projects/), [deep learning projects](https://machinelearningprojects.net/deep-learning-projects/), [computer vision projects](https://machinelearningprojects.net/opencv-projects/), [NLP projects](https://machinelearningprojects.net/nlp-projects/), [Flask projects](https://machinelearningprojects.net/flask-projects/) at [machinelearningprojects.net](https://machinelearningprojects.net/)**.  
Post navigation  
[← Previous Post](https://machinelearningprojects.net/social-distancing-using-yolov3/)  
[Next Post →](https://machinelearningprojects.net/human-segmentation-using-u-net/)  

Read More
---------

[![](https://machinelearningprojects.net/wp-content/uploads/2022/02/Generating-cifar-10-fake-images-using-DCGAN-1024x536.png)](https://machinelearningprojects.net/deep-convolutional-generative-adversarial-networks/)

### [Generating cifar-10 fake images using Deep Convolutional Generative Adversarial Networks (DCGAN) -- 2022](https://machinelearningprojects.net/deep-convolutional-generative-adversarial-networks/)

[Leave a Comment](https://machinelearningprojects.net/deep-convolutional-generative-adversarial-networks/#respond) / [Deep Learning](https://machinelearningprojects.net/category/deep-learning/), [Computer Vision](https://machinelearningprojects.net/category/opencv/) / By [Abhishek Sharma](https://machinelearningprojects.net/author/sharmaji27/ "View all posts by Abhishek Sharma")  
[![](https://machinelearningprojects.net/wp-content/uploads/2022/02/Helmet-and-Number-Plate-Detection-and-Recognition-using-YOLOv3-1024x536.png)](https://machinelearningprojects.net/helmet-and-number-plate-detection-and-recognition/)

### [Helmet and Number Plate Detection and Recognition using YOLOv3 -- interesting project -- 2022](https://machinelearningprojects.net/helmet-and-number-plate-detection-and-recognition/)

[22 Comments](https://machinelearningprojects.net/helmet-and-number-plate-detection-and-recognition/#comments) / [Deep Learning](https://machinelearningprojects.net/category/deep-learning/), [Computer Vision](https://machinelearningprojects.net/category/opencv/) / By [Abhishek Sharma](https://machinelearningprojects.net/author/sharmaji27/ "View all posts by Abhishek Sharma")  
[![](https://machinelearningprojects.net/wp-content/uploads/2022/02/healthcure-an-all-in-one-medical-solution-1024x536.png)](https://machinelearningprojects.net/healthcure-medical-project/)

### [HealthCure -- an all in one medical solution -- medical project -- 7 disease detections -- 2022](https://machinelearningprojects.net/healthcure-medical-project/)

[18 Comments](https://machinelearningprojects.net/healthcure-medical-project/#comments) / [Machine Learning](https://machinelearningprojects.net/category/machine-learning/), [Computer Vision](https://machinelearningprojects.net/category/opencv/), [Deep Learning](https://machinelearningprojects.net/category/deep-learning/), [Flask](https://machinelearningprojects.net/category/flask/) / By [Abhishek Sharma](https://machinelearningprojects.net/author/sharmaji27/ "View all posts by Abhishek Sharma")  
[![](https://machinelearningprojects.net/wp-content/uploads/2022/02/Invisible-Man-using-Mask-RCNN-1024x536.png)](https://machinelearningprojects.net/invisible-man-using-mask-rcnn/)

### [Invisible Man using Mask-RCNN -- with source code -- fun project -- 2022](https://machinelearningprojects.net/invisible-man-using-mask-rcnn/)

[Leave a Comment](https://machinelearningprojects.net/invisible-man-using-mask-rcnn/#respond) / [Deep Learning](https://machinelearningprojects.net/category/deep-learning/), [Computer Vision](https://machinelearningprojects.net/category/opencv/) / By [Abhishek Sharma](https://machinelearningprojects.net/author/sharmaji27/ "View all posts by Abhishek Sharma")  

### Leave a Comment Cancel Reply

Your email address will not be published. Required fields are marked \*  
Type here..  
Name\*

Email\*

Website

Save my name, email, and website in this browser for the next time I comment.

<br />

Δ  

### 💌 Join our newsletter 💌

Subscribe to our newsletter to receive blog updates  
[Subscribe](https://forms.gle/8qhFGfY3qGZz9X6u9)  
* [About](https://machinelearningprojects.net/about/)
* [Contact](https://machinelearningprojects.net/contact/)
* [Privacy Policy](https://machinelearningprojects.net/privacy-policy/)
* [Terms and Conditions](https://machinelearningprojects.net/terms-and-conditions/)  
Copyright © 2022 \| machinelearningprojects.net
