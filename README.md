# Flatiron Capstone Project - River Delta Satellite Image Classification

* Student name: Alex Beat
* Student pace: part time
* Scheduled project review date/time: 8-19-20
* Instructor name: Yish Lim
* Blog post URL: NA

# Prerequisites
Runs on latest version of Python, Keras, with the addition of Google Colab for faster model processing using their GPUs. 

# Overview

* Problem: A model is needed to help process the large amounts of raw Mars images.
* Business Value: This model will speed up the processing of Mars image data to help classify river delta patterns and aid scientists in honing in on locations that contain traces of existing or preexisting water on the planet.
* Other use cases: This model has the potential to also be tweaked for use with environmental cases on Earth, such as changes in river deltas over time regarding climate change, analysis for farming data, real estate and commercial building viability. 
* Audience: Main audience is a space exploration company, with additional use in agricultural, real estate and environmental sectors depending how the model is adjusted to perform. 

# Content
The Earth dataset is organized into 2 folders (train, test) and contains subfolders for each image category (land, river Delta). There are 1,398 images (JPEG) and 2 categories. Image augmentation with generators was used to create a larger dataset of 2,232 images. 

Images were obtained from Google Image searches, using Selenium to interactively scroll through the webpage and scrape them. The process is shown in the separate notebook in this repository called [selenium_image_scraper](https://github.com/alexanderbeat/mod5project/blob/master/selenium_image_scraper.ipynb).

![folder structure](https://github.com/alexanderbeat/mod5project/blob/master/images/Screen%20Shot%202020-08-17%20at%203.14.13%20PM.png)


## Project Phase 1

This first part of the project covers processing and Earth land and river delta image tiles and training a model using those for the dataset. This starts as a basis for how the next phase will be performed, but in that next phase, a separate dataset of Mars image tiles will be used in place of the Earth tiles to train/test the model. 

The Earth images obtained from Google are not the cleanest and contain many different artifacts such as text, drawings on the image, and some outlier images are not an exact match of being a satellite image, but were shown on the image search page based on how the Google Image Search algortithm worked. I kept the images all in the dataset for now, but in order to clean, will attempt to view misclassifed images and remove those from the original dataset permanently. 

Will also plan to implement a supervised learning model into the mix as well in hopes of gaining other performance values along with a thorough grid search of hyperparameters. 

![image tiles](https://github.com/alexanderbeat/mod5project/blob/master/images/output_33_0.png)

### Model Performance

A convolutional neural network model with an SGD optimizer proved to have the highest performance with little overfitting and a classification accuracy of 90%. The precision was 88%, with a recall of 87% of the river delta labeled images. These scores seem a little too good to be true for now considering the lack of cleaner images, but it's a good springboard to work from.

test acc: 0.9025787711143494
test loss: 0.29313525557518005

Classification Report:
              precision    recall  f1-score   support

         0.0       0.92      0.92      0.92       212
         1.0       0.88      0.87      0.87       137

    accuracy                           0.90       349
   macro avg       0.90      0.90      0.90       349
weighted avg       0.90      0.90      0.90       349

Confusion Matrix:

![RMSprop](https://github.com/alexanderbeat/mod5project/blob/master/images/output_100_1.png)

Training and Validation accuracy and loss:

![accloss](https://github.com/alexanderbeat/mod5project/blob/master/images/output_100_2.png)


## Project Phase 2

From there, the next step will be to obtain the Mars images and continue training and testing in in hopes of being able to identify river delta patterns from the Mars imagery. Obtaining these next Mars images through an API could give the possible opportunity of pairing the model classified river delta images with provided location coordinates through the API calls, and would then be able to return each classified river delta with its corresponding location on Mars. The benefit would be a machine learning model that will give scientists a head start on where to continue their search for other signs of pre-existence of water on Mars. 

Notice on the images below to see what I mean about images containing artifacts, such as the text, boxes, and drawings on them. These are causing the image set to be dirty, because it was a basic scrape from a Google Image search with no control over their search algorithms. A cleaner dataset should prove to be better performing once obtained. Cleaner images will be obtained to improve model performance in the future. 

<img src=https://github.com/alexanderbeat/mod5project/blob/master/images/mars2.jpg width="450"/>

### Model Performance

Phase 2 performance details will be updated once Mars images are obtained from a scrape or more preferably, an API. 


# Visualize Feature Map Layers to see what's going on inside of CNN model pooling layers.

This will help show you what's happening with the images after each layer of the model network and how the patterns are developed. 

![png](https://github.com/alexanderbeat/mod5project/blob/master/images/output_68_1.png)
![png](https://github.com/alexanderbeat/mod5project/blob/master/images/output_68_7.png)
![png](https://github.com/alexanderbeat/mod5project/blob/master/images/output_68_11.png)

# Github Contents and Materials
* The notebook [selenium_image_scraper](https://github.com/alexanderbeat/mod5project/blob/master/selenium_image_scraper.ipynb) has code for getting the images from Google.
* The notebook [ALEX_BEAT_v2_1mod5project_notebook](https://github.com/alexanderbeat/mod5project/blob/master/ALEX_BEAT_v2_1mod5project_notebook.ipynb) includes all code for image processing and modeling.
