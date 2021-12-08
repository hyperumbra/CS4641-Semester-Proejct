# Standford Car Classifier
_Created by Joshua Donegal_

## Introduction/Background
For many, cars are a tool of transportation, objects meant to decrease the time a person uses to go from point A to point B. However, for some, cars are a means of representation of lifestyle and can serve as an extension of the personality and living conditions. Some may attempt to stretch themselves financially to afford more expensive cars, but I believe these scenarios are few and between and are still representative of the individual. The ability to classify a car using only an image is a problem that lies under computer vision: a specialized field of machine learning focused on the application of identification and classification techniques on images and videos.

## Problem Definition
The Stanford Car Classifier categorizes images that contains a vehicle parked at Stanford by make, model, and year. This can be achieved via removing the noise and background data from the composition of the image and isolating the car’s model within a 3-dimensional plane, allowing for classification of the vehicle from multiple different angles.

## Data Collection
Data was collected from Kaggle, an online community of data scientists and machine learning practitioners. The dataset was already pre-processed into a training and test dataset, each containing just over 8,000 images for classification. After importing the dataset, the only task left at hand was to ensure proper image naming for training the model.

To ensure proper image naming for training, the images were split into categories. Currently, there are 196 possible categorical classifications of vehicles for the images to be labelled. Depicted below are visualizations of the possible categories.

![visualization of classes](/img/class_visualizations.png)

*Visualization of a subset of all possible labels and example classified images.*

![visualization of class distribution](/img/class_distribution.png)

*Distribution of classified images.*

## Methods
I am currently utilizing a convolutional neural network (CNN), a supervised methodology of machine learning, to do image classification of vehicle make, model, and year. Instead of attempting to utilize several different models for classification, such as a decision tree or random forest for image classification, I have decided to focus on working with a CNN due to its powerful classification abilities and wide application of usage. This is a problem that’s commonly found within computer vision that is able to utilize supervised machine learning to aggregate the training and testing data to increase accuracy.

The architecture of the Neural Network follows the architecture of a pretrained ResNeXt101-32x4d with the addition of the Squeeze-and-Excitation module (also known as SE-ResNeXt101-32x4d). The primary advantages to utilizing this neural network architecture are two-fold: increased accuracy while decreasing training time. On the first layer, the model will pass an input through a pooling layer, a fully connected layer, an ReLU activation, a fully connected layer, and a Sigmoid activation before scaling to be output. However, the model may "freeze" layers past the first one. Freezing is the phenomonon of preventing a layer's weights from being modified to drastically reduce computation due to significantly less back propogations. We do this since we're adding more generral objects to this pretrained model for the network to realize.

![visualization of architecture](/img/se-resnet_architecture.png)

*Visualization of ResNet compared to SE-ResNeXt101-32xd. Image from Squeeze-and-Excitation Networks as reference below.*


## Results & Discussion
Depicted below are tables that detail the training of the network. With the initial learning rate, weight decay, and epochs, the model was able to train to just under 70% accuracy. While this is a good benchmark to begin with, the model has potential for increases in accuracy when balancing learning rates, weight decays, and epochs.

![Table of initial training](/img/training_initial.png)

*Training with initial learning rate and weight decay (lr=2.75e-2, wd=1e-5). Final accuracy evaluates to 69.67%.*

![Table of final training](/img/training_final.png)

*Training with initial learning rate and weight decay (lr=3.22e-2, wd=1e-7). Final accuracy evaluates to 80.41%.*

As depicted above, the accuracy of the model after tuning the learning rate and weight decay rises to just above 80% despite taking the same number of epochs (30) to train as the initial model. To increase the accuracy, to circumvent the increase in epochs for training that would result in longer training times, I decided to tune the learning rate and weight decay of the model. When adjusting the learning rate, I increased the learning rate slightly as a means to increase training accuracy at the risk of overfitting the data. On the other hand, adjusting weight decay was much trickier as the pretrained model employs the use of frozen layers, a technique in which the model will prevent a layer's weights from being modified at the benfit of decreasing computation time via reduced back propoagations.

The use of a pretrained model provides significant advantages over architecting and training a model from scratch. The first main advantage lies in the optimization of training time due to ongoing development. Another significant advantage is the ability to readily take advantage of the processing power of graphical processing units (GPUs), specialized hardware designed for processing images and videos and is much more efficient than a traditional computer processor.

## References
- [Kaggle](https://www.kaggle.com/getting-started/44916)
- 3D Object Representations for Fine-Grained Categorization Jonathan Krause, Michael Stark, Jia Deng, Li Fei-Fei 4th IEEE Workshop on 3D Representation and Recognition, at ICCV 2013 (3dRR-13). Sydney, Australia. Dec. 8, 2013.
- [What is Copmuter Vision?](https://machinelearningmastery.com/what-is-computer-vision/)
- [Review: SENet, Winnerr of ILSVRC 2017 (Image Classification)](https://towardsdatascience.com/review-senet-squeeze-and-excitation-network-winner-of-ilsvrc-2017-image-classification-a887b98b2883)
- [SE-ResNeXt101-32x4d for PyTorch](https://catalog.ngc.nvidia.com/orgs/nvidia/resources/se_resnext_for_pytorch)
- [Squeeze-and-Excitation Networks](https://arxiv.org/pdf/1709.01507.pdf)
