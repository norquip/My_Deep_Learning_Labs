# My_Deep_Learning_Labs
This repository contains my explorations and hands-on practice labs on  Deep Learning. 

# Flower Classification with CNN — Adam vs SGD Optimization

## Overview

This project builds and trains a Convolutional Neural Network (CNN) to classify images of daisy and sunflower flowers. See ([DaisySun_Adam_SGD](https://github.com/norquip/My_Deep_Learning_Labs/blob/main/DaisySun_Adam_SGD.ipynb)).
The goal is to compare two popular optimization algorithms—Adam and SGD—and evaluate their effect on training stability, convergence speed, and overall performance.

This lab was developed as part of my personal deep learning learning path.

## Motivation

* I wanted to practice the generator-based data loading to work directly with image file paths instead of loading all images into memory.
* I was particularly interested in exploring how different data transformations operate and how they contribute to improving the model’s accuracy.
* I wanted to understand how optimization choices affect model behavior.
Even with the same architecture and data, Adam and SGD can produce different learning curves, stability patterns, and ROC/AUC results.

## Model Architecture

A used a simple CNN model that was effective for the classification:
* 4 convolutional blocks with ReLU, MaxPool, BatchNorm
* Adaptive average pooling
* Fully connected classifier with dropout
* Output: 2 classes (daisy, sunflower)

## Optimizers Compared
### Adam

* Faster convergence

* Smoother validation curves

* Best results in this experiment

### SGD (with momentum)

* More oscillation early in training

* Lower accuracy compared to Adam

* More sensitive to learning rate

## Visualizations

* Accuracy curves

* Loss curves

* ROC curves (Adam)

* Confusion matrix

* Misclassified images

## Key Insights

* Adam reaches good performance faster

* SGD shows spikes

* Both optimizers plateau, but Adam reaches a better score

* Small gap between training and validation curves → no overfitting issues

## Acknowledgements

Special thanks to the IBM course *AI Capstone Project with Deep Learning*, which helped me understand several support concepts used in this lab.
The utility functions "set_seed()" and the "misclassified-image display" function were copied from the IBM ungraded labs, where they were provided as part of the learning materials.
All model design, training loops, optimizer comparison, plots, and analysis were created independently.

## Future Improvements
The complete dataset  of 5 flower classes is significantly imbalanced, which introduces additional challenges during training.
I tested a similar model on the full dataset, but the resulting accuracy was not strong enough. As a next step, I plan to apply transfer learning to improve performance on the complete dataset.


