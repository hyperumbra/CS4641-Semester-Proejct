# CS 4641 Semester Project
_Created by Joshua Donegal_

## Introduction/Background
For many, cars are a tool of transportation, objects meant to decrease the time a person uses to go from point A to point B. However, for some, cars are a means of representation of lifestyle and can serve as an extension of the personality and living conditions. Some may attempt to stretch themselves financially to afford more expensive cars, but I believe these scenarios are few and between and are still representative of the individual. The ability to classify a car using only an image is a problem that lies under computer vision: a specialized field of machine learning focused on the application of identification and classification techniques on images and videos.

## Problem Definition
Classification of images that contains a vehicle parked at Stanford by make, model, and year. This can be achieved via removing the noise and background data from the composition of the image and isolating the car’s model within a 3-dimensional plane, allowing for classification of the vehicle from multiple different angles.

## Data Collection
Data was collected from Kaggle, an online community of data scientists and machine learning practitioners. The dataset was already pre-processed into a training and test dataset, each containing just over 8,000 images for classification. After importing the dataset, the only task left at hand was to ensure proper image naming for training the model.

[visualization of classes]

[visualization of class distribution]

[Another cool visualization]

[cool 3d visualization]

## Methods
I am currently utilizing a convolutional neural network (CNN), a supervised methodology of machine learning, to do image classification of vehicle make, model, and year. Instead of attempting to utilize several different models for classification, such as a decision tree or random forest for image classification, I have decided to focus on working with a CNN due to its powerful classification abilities and wide application of usage. This is a problem that’s commonly found within computer vision that is able to utilize supervised machine learning to aggregate the training and testing data to increase accuracy.

## Results & Discussion
Admittedly, I do not have results from trraining my CNN yet. This is due to my model not having been trained yet as I am still debugging parrts of the codebase to enable training. However, I do not believe training will take a substantial amount of time due to Pytorch's capabilities in utilizing CUDA cores for training paired with a NVIDIA GTX 1080Ti. With that being said, I do believe that the implementation of ResNet18 that frerezes all but the last fully connected layer will yield a fairly high accuracy. Additionally, I am contemplating creating my own custom CNN via Pytorch, but I do need to draw a conclusion on how many layers and feautres will be necessary to create a well-trained model that does not overfit to the training data.

## References
- [Kaggle]https://www.kaggle.com/getting-started/44916
- (3D Object Representations for Fine-Grained Categorization Jonathan Krause, Michael Stark, Jia Deng, Li Fei-Fei 4th IEEE Workshop on 3D Representation and Recognition, at ICCV 2013 (3dRR-13). Sydney, Australia. Dec. 8, 2013.)
- [What is Copmuter Vision?]https://machinelearningmastery.com/what-is-computer-vision/ 
- [Review: SENet, Winnerr of ILSVRC 2017 (Image Classification)]https://towardsdatascience.com/review-senet-squeeze-and-excitation-network-winner-of-ilsvrc-2017-image-classification-a887b98b2883
- [SE-ResNeXt101-32x4d for PyTorch]https://catalog.ngc.nvidia.com/orgs/nvidia/resources/se_resnext_for_pytorch
