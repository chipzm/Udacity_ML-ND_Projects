# CNN_Dog-Breed-Classifier_Udacity
Dog-breed-classifier using CNN and transfer learning in PyTorch
This is the repo of Dog breed classifier project in Udacity ML Nanodegree.
This project is to classify the different dog breeds using CNN (created from scratch) and transfer learning in PyTorch as part of Udacity Machine Learning Nanodegree

## Project Overview
The goal of the project is to build a machine learning model that can be used within web app to process real-world, user-supplied images. The algorithm has to perform two tasks:
1. Given an image of a dog, the algorithm will identify an estimate of the canine’s breed.
2. If supplied an image of a human, the code will identify the resembling dog breed.

For performing this multiclass classification, we can use Convolutional Neural Network to solve the problem.The solution involves three steps. 
1. To detect human images- an existing algorithm like OpenCV’s implementation of Haar feature based cascade classifiers is used. 
2. To detect dog-images - A pretrained VGG16 model is used. 
3. After the image is identified as dog/human - this image is passed to a CNN model which will process the image and predict the breed      that matches the best out of 133 breeds.

## CNN model created from scratch
A CNN model has been created from scratch to solve the problem. The model has 3 convolutional layers. All convolutional layers have kernel size of 3 and stride 1. The first conv layer (conv1) takes the 224*224 input image and the final conv layer (conv3) produces an output size of 128. ReLU activation function is used here. The pooling layer of (2,2) is used which will reduce the input size by 2. We have two fully connected layers that finally produces 133-dimensional output. A dropout of 0.25 is added to avoid over overfitting.

## Refinement - CNN model created with transfer learning
The CNN created from scratch have accuracy of 13%, Though it meets the benchmarking, the model can be significantly improved by using transfer learning. To create CNN with transfer learning, I have selected the Resnet101 architecture which is pre-trained on ImageNet dataset, the architecture is 101 layers deep. The last convolutional output of Resnet101 is fed as input to our model. We only need to add a fully connected layer to produce 133-dimensional output (one for each dog category). The model performed extremely well when compared to CNN from scratch. With just 6 epochs, the model got 83% accuracy.


## Model Evaluation
The CNN model created using transfer learning with ResNet101 architecture was trained for 6 epochs, and the final model produced an accuracy of 83% on test data. The model correctly predicted breeds for 694 images out of 836 total images.

Accuracy on test data: 83% (694/836)

