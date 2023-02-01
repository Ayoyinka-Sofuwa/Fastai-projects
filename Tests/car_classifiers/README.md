# Buiding and deploying a Computer Vision model using FastAI and Gradio

## Overview
This is a project I came up with to walk through the FastAI CV module. Ever experience the decision paralysis, in trying to decide what product you want, this classifier helps to streamline your choices of a car type. Anyway, In this project, I trained a model using the fastai framework and evaluated model performance and deployed using Gradio on hugging face spaces.

## Summary
The data used here are images of cars extracted from the duckduckgo search engine and used to classify cars into two categories ("SUV", "Sedan"). We use a pretrained ResNet model which has been trained on millions of images to learn our data and make predictions on the "hold-out" data. I evaluated the performance and after a couple of iterations, I deployed the model using Gradio to build a mini web app to visualize our data.

## Pipeline architecture
* Insert image

## Key Steps
### Process and Experiment

#### Gathering Data
The data used for this experiment was downloaded from the duckduckgo search engine and it contains pictures of different car types that fall in the "SUV", "Sedan" categories. I first downloaded two images, one in each of the categories and then saved that in a folder, then I downloaded all the images in those categories and saved them in another folder. We thus have two holdout datasets:
- Validation data
- Initially Downloaded data
Then remove/unlink the images which failed during download

#### Preprocess the data and Train the model
##### Preprocessing
The fastai DataBlock is an important concept that provides a flexible and modular way to pre-process and manage datasets in machine learning.
The DataBlock API automates the entire data pipeline, from loading to pre-processing to batching and shuffling, reducing the amount of code you need to write and improving code quality and readability.
Here, we are working on a classification computer vision project so we'll work with the ImageBlock and CategoryBlock. Then we view our data with the dataloaders method and then resize to fit how we want to view the data. 
The different data resizing methods explored here:
* Pad
* Crop
* RandomResizedCrop
* Squish.
Another data transformation method to view our data in other ways in realtime is the data augumentation method. It reshapes our data in real time and can be useful for training out model to view and be exposed to different aspects of our data.

##### Training the model
Here we pass our augumented and/or resized data to our learner, this time(vision_learner). Using a pretrained model, ResNet34 and defining our metric as the error rate, we finetune the model and run it over 5 - 6 epochs. We note the losses and eroor rate progression, then we visualize the top losses

<p align="center">
  <img src="https://github.com/Ayoyinka-Sofuwa/Fastai-projects/blob/main/Tests/car_classifiers/top_losses.png">
 </p>

Then we clean the data using the ImageClassifierCleaner which is a vision widget that helps to reclassify, delete false data.

You can retrain your model on the reclassified and relabelled data.
Run through the experiments again and save and export model (pkl file). Test model on new data, deploy to gradio to view data and test predictions that the model will make.

Experiment result and future work
In this experiment, the model performed poorly on the validation set, the loss was really high, prediction was poor and it wasn't making any accurate prediction. So I had a couple of iterations after visualizing the prediction performance on a confusion matrix and performance significantly improved.

Issues observed:
* Bias towards SUVs due to imbalanced data
* Check labelled data and reclassify misclassified data

## Setting up Gradio
* Open up hugging spaces
* Create a new space selecting gradio SDK, follow instructions to run the gradio space:

<p align="center">
  <img src="https://github.com/Ayoyinka-Sofuwa/Fastai-projects/blob/main/Tests/car_classifiers/Hugging face space.png">
 </p>

<p align="center">
  <img src="https://github.com/Ayoyinka-Sofuwa/Fastai-projects/blob/main/Tests/car_classifiers/gradio_app.png">
 </p>
