# Daisy_Sunflowers — Adam vs SGD Optimization

## Overview

This project builds and trains a Convolutional Neural Network (CNN) to classify images of daisy and sunflower flowers.
The goal of this lab is to understand several concepts that are involved in the construction of CNN and was developed 
as part of my personal deep learning path.

## Motivation

* I wanted to practice the generator-based data loading to work directly with image file paths instead of loading all images into memory.
* I was particularly interested in exploring how different data transformations operate and how they contribute to improving the model’s accuracy.
* I wanted to understand how optimization choices affect model behavior. How differents are the learning curves for Adam and SGD optimization. 


## Model Architecture

A used a simple CNN model that was effective for the classification:
* 4 convolutional blocks with ReLU, MaxPool, BatchNorm and Dropout
* Adaptive average pooling
* Fully connected classifier with dropout
* Output: 2 classes (daisy, sunflower)

## Optimizers Compared
### Adam

* Faster convergence

* Smoother validation curves after 20 epochs

* Best results in this experiment

### SGD (with momentum)

* Oscillation with higher peaks in validation curve 

* Accuracy very similar to Adam

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

* Both optimizers plateau, but Adam reaches a better little higher score

* Small gap between training and validation curves → no overfitting issues

## Acknowledgements

Special thanks to the IBM course *AI Capstone Project with Deep Learning*, which helped me understand several support concepts used in this lab.
The utility functions "set_seed()" and the "misclassified-image display" function were copied from the IBM ungraded labs, where they were provided as part of the learning materials.
All model design, training loops, optimizer comparison, plots, and analysis were created independently.

Special thanks to all the photographers associated to the Flowers dataset. 


# Revisited Version
Last month, I shared an earlier version of this notebook. After reading more literature and spending more time reviewing the code,  I realized that I had made two important mistakes: 
1. Lack of reproducibility due to hard-coded data paths

I initially downloaded and referenced the dataset using absolute paths pointing to my local home directory. While this worked locally, it made the notebook non-reproducible when shared on GitHub.

2. Splitting train/val/test and Applying data transformations incorrectly
   
When loading the dataset, I applied the transformations defined for the training set to the entire dataset. Later, after splitting the data into training and validation sets, I applied a separate 
validation transformation to the validation set. As a result, the validation data was transformed twice, which is incorrect.

## Corrections and Improvements
These issues have been corrected in the current version of the notebook.  
* Reproducibility was fixed by using project-relative paths and downloading the dataset programmatically inside the project.
* Data splitting was rectified by using  "Subset" from "from torch.utils.data" to correctly create the train/val/test sets.
* Data transformations were fixed by applying a data augmentation only to the training set and  using  deterministic transformations  for  the validation and test sets.
* Additionally, I adjusted the "Dropout"  rate from 0.4 to 0.1 to improve the loss and accuracy curves. 

While the overall behavior of the model remained similar, correcting the data pipeline led to an improvement in accuracy, and the validations curves now reflect true generalization rather than augmented noise.


## Final remarks

Paraphrasing an idea often attributed to Daniel Dennett: “An unacknowledged error is still an error; once acknowledged, it becomes progress.”

Revisiting this notebook helped me understand how easily subtle issues in data handling can affect both reproducibility and experimental correctness. These are small details, but they matter a lot in deep learning projects and fixing them is part of the learning process. 

As a final note, the results presented in the poster correspond to the original version of the notebook. I decided not to change the results in the poster in order to highlight how the loss curves were improved after implementing the corrections described above. 


## Future Improvements
The complete dataset  of 5 flower classes is significantly imbalanced, which introduces additional challenges during training.
I tested a similar model on the full dataset, but the resulting accuracy was not strong enough. As a next step, I plan to apply transfer learning to improve performance on the complete dataset.




