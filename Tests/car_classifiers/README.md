## Buiding and deploying a Computer Vision model using FastAI and Gradio

### Overview
This is a project I came up with to walk through the FastAI CV module. Ever experience the decision paralysis, in trying to decide what product you want, this classifier helps to streamline your choices of a car type. Anyway, In this project, I trained a model using the fastai framework and evaluated model performance and deployed using Gradio on hugging face spaces.

### Summary
The data used here are images of cars extracted from the duckduckgo search engine and used to classify cars into two categories ("SUV", "Sedan"). We use a pretrained ResNet model which has been trained on millions of images to learn our data and make predictions on the "hold-out" data. I evaluated the performance and after a couple of iterations, I deployed the model using Gradio to build a mini web app to visualize our data.

### Pipeline architecture
* Insert image

### Key Steps

and it contains pictures of different car types that fall in the "SUV", "Sedan" categories