# LEAP-ML_Project

This project consisted on creating a Convolutional Neural Network (CNN) capable of reading handwritten numbers and identify the correct digit between 0 and 9. The objective of the project also includes identifying the possible mistakes made by the network, and how different changes in the model may affect the precision and accuracy of the predictions.

## Data

As stated before, the data consisted on a set of handwritten digits. It included 70 000 grayscale images of 28 by 28 pixels, included in the datasets in scikit-learn. The import of the data was included in the notebook, so we don't make any modifications to it.

### Preparation

The data was normalized (also given with the project) to help the training of the network, and an extra axis was added, for the color channel (only one, given that it is grayscale). Originally, it was only divided between training and test data, with 20% of it being test data.

Before starting the training of the model, we split the training set again, so that 10% of it becomes our validation set.

## Model

Our model consist on a small CNN with sequentially stacked layers: 
- The input layer, where we read the data
- A convolution layer with 32 filters of 3 by 3, where each filter creates a feature map. They are activated via the ReLU method, and we also added padding, as suggested in lesson 6, to ensure that each map has the same dimensions.
- A Pooling layer, which halves the size of each feature map, so the network can work with smaller elements and look for more robust patterns.
- A Dropout layer, which deactivates 30% of the neurons during each epoch of the training, trying to ensure that the network doesn't overfit on the training data.
- A Flatten layer, which converts the feature maps to a 1D vector that a dense layer can interpret.
- A hidden Dense layer, which learns about the patterns on the 1D vector.
- The Output dense layer, which uses the softmax activation method to classify each digit between the 10 possible categories.

### Compiling

We compile the model in a standard way: We use the Adam optimizer, with sparse categorical cross-entropy (useful for many categories with integer labels) and with the accuracy as the metric.

### Training

During the training, the model passes through 15 epochs, each with a batch size of 128. We defined an early stopping callback, so that if the model doesn't improves its validation loss during 3 epochs, the training stops.

### Evaluation

The loss and accuracy of the training and validation sets are relatively close 4 epochs, so the model is not overfitting nor underfitting.

The model has an accuracy of 98.7% on the test set, which is quite high, and a loss of 0.043.

## Answers and Discussion

The answers and discussion stated in the instructions are directly included in the notebook in this repository.
