---
title: "Surgical Tool Detection with YOLOv8"
date: 2024-01-06
description: Project
menu:
  sidebar:
    name: Surgical tool detection
    identifier: yolov8
    parent: dl
    weight: 35
#tags: ["unity","game"]
hero: front.png
categories: ["ia","project", "yolo", "detection", "health"]

draft: true


---

The goal of this project made with Pauline Spinga was to try to detect surgical tools on images and then on video streams.
We used a Kaggle dataset with different approachs to achieve a better classification and detection.

### Dataset

The first step is to find a dataset. We found on [Kaggle](https://www.kaggle.com/datasets/dilavado/labeled-surgical-tools/data) a dataset of 2000 images divided into 4 classes : 
- Scalpel
- Clamp 
- Straight Scissors
- Curved Scissors

This dataset also contains images in which we can see pairs of tools or all 4 in the same image. We notice that most of the images are similar, even if tools are different. The background is either gray or black. Thus, one pitfall is that background and objects can be easily confused. 

Text files are also given, giving the label of the image and the bounding box coordinates.

<img src="/posts/dl/yolov8/dataset.png" height="250">

### First CNN model classification

#### Basic CNN

We started with the image classification step. 
In order to do that we computed a basic CNN that have the following structure : 
Feature extraction with 3 Convolution-Max pooling layers : in order to extract relevant features. We put a relu activation function to introduce non linearities in the model 
Classification step with 2 layers of fully connected neurons. The last layer has 4 neurons corresponding to the 4 classes. The softmax activation function allows to obtain probability for each class.

<img src="/posts/dl/yolov8/cnn.png" height="250">

No matter the number of epochs or batch size, validation accuracy doesn’t exceed 24%. The CNN has only random guesses on the 4 classes.

<img src="/posts/dl/yolov8/cnn_r.png" height="250">


#### VGG 



#### Disappointing results 

### Yolov8

#### Explanation of the model

#### Set up and data organization

#### Metrics

#### Results

#### Video stream