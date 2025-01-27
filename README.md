# Application of Deep Learning to Classify Vandalism and Non-Vandalism Images

##Group 3
1. Bocah Aditya Rohmaulana (2203488)
2. Defrizal Yahdiyan Risyad (2206131)
3. Muhammad Furqon Al-Haqqi (2207207)
4. Raya Cahya Nurani (2205714)
5. Septiani Eka Putri (2206000)

## Introduction
This notebook aims to discuss the application of deep learning algorithms to the task of classifying vandalism and non-vandalism images. With rapid urbanization, monitoring signs of vandalism is important to maintain the beauty and cleanliness of the environment.

### Definition of Vandalism and Its Differences with Graffiti and Murals
- Vandalism: An act of cruelly destroying other people's work and valuables.
- Graffiti: Scribbling on a wall with artistic considerations (color, line, shape, volume).

- Mural: Painting on a permanent surface such as a wall or a wall.

We group graffiti and murals into the `not_vandalized` class assuming that graffiti and murals are not vandalism if done with permission.

## Settings
- **Framework**: TensorFlow
- **Dataset**: Vandalized and non-vandalized images uploaded to Google Drive.

## Preprocessing the Dataset
### Dataset Size
- **Initial classes**:
- `vandalized`: 168 images
- `not_vandalized`: 133 images

### Split Dataset
- Training: 80%
- Validation: 20%

### Data Augmentation
Augmentation is done to increase the variation of the dataset with techniques such as:
- Horizontal flip
- Random rotation
- Random zoom

### Data Normalization
RGB values ​​from [0,255] are normalized to [0, 1].

## Deep Learning Model Architecture
### Model 1 (Base)
1. **Convolution Layer**:
- 3 layers with 16, 32, 64 filters.
2. **Pooling**: Max Pooling.
3. **Dense Layer**: 128 units.
4. **Output Layer**: Based on the number of classes (2 classes).

### Model 2 (With Dropout)
Added dropout (0.2) to reduce overfitting.

### Model 3 (Revised Dataset)
The `not_vandalized` data was improved by moving 51 graffiti/mural images that were considered vandalism to the `vandalized` class. New dataset:
- **`vandalized`: 219 images**
- **`not_vandalized`: 82 images**

## Training Model
- Optimizer: Adam
- Loss Function: SparseCategoricalCrossentropy
- Epochs: 10-15

### Evaluation Results
The evaluation results show that the model has better validation accuracy after the dataset revision. The previous model had difficulty classifying images due to ambiguous initial assumptions.

## Conclusions
- Deep learning is effective for vandalism image classification with proper preprocessing.
- The dataset revision has a significant effect on model performance.
- Validation accuracy increases after transferring graffiti/mural data to the `vandalized` class.

## Additional Notes
- The dataset can be used to improve the generalization model.
- Hyperparameter tuning is needed for more optimal performance.

---
Created by Group 3 as part of a case study of deep learning application.