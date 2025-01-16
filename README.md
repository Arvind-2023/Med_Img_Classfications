# Med_Img_Classfications
## Brain-Tumor-Detector
Built a Brain-tumor detection model using a convolutional neural network in Tensorflow & Keras.

## Dataset Overview

The dataset includes two categories of brain MRI images:

- **Yes** (Tumorous): 155 images
- **No** (Non-Tumorous): 98 images

In total, the dataset consists of 253 images, which were used for training, validation, and testing.

## Data Augmentation

Data augmentation was employed to address the small size of the dataset and to mitigate the class imbalance issue. Augmentation helped to generate more diverse data, allowing the neural network to learn more effectively.

### Data Augmentation Results:
- **Before augmentation**: 253 images (155 positive, 98 negative).
- **After augmentation**: 2065 images (1085 positive, 980 negative), which includes the original 253 images stored in the 'augmented data' folder.

## Data Preprocessing

The following preprocessing steps were applied to each image:

1. **Cropping**: Extract the brain region from the image (the most critical part).
2. **Resizing**: Resize the image to a uniform size of (240, 240, 3), where 240x240 is the image resolution and 3 represents the RGB channels.
3. **Normalization**: Scale the pixel values to a range of 0-1.

## Data Split

The dataset was split into:

- **70% for training**
- **15% for validation**
- **15% for testing**

## Neural Network Architecture

The model uses a simple CNN architecture, designed for efficiency given computational constraints. Below is a summary of the architecture:

1. **Zero Padding**: To maintain spatial dimensions.
2. **Convolutional Layer**: 32 filters, filter size (7x7), stride 1.
3. **Batch Normalization**: To normalize activations and improve convergence.
4. **ReLU Activation**: To introduce non-linearity.
5. **Max Pooling**: Two layers with a filter size of (4x4) and stride 4.
6. **Flatten**: Convert the 3D matrix to a 1D vector.
7. **Fully Connected Layer**: Output layer with one neuron and a sigmoid activation (for binary classification).

### Why This Architecture?

Though transfer learning with models like ResNet50 or VGG-16 could be effective, they were too computationally expensive given the dataset size and available hardware (Intel i7 CPU, 8GB RAM). Therefore, a simpler architecture was designed and trained from scratch, yielding good results.

## Training the Model

The model was trained for 24 epochs. Below are the loss and accuracy plots:

- **Loss Plot**:

  ![Loss Plot](Loss.PNG)

- **Accuracy Plot**:

  ![Accuracy Plot](Accuracy.PNG)

The best validation accuracy was achieved on the 23rd epoch.

## Results

The best-performing model (with the highest validation accuracy) achieved the following results:

- **Test Set Accuracy**: 88.7%
- **Test Set F1 Score**: 0.88

These results are impressive considering the balanced dataset and the simplicity of the architecture.

### Performance Table:

| Metric     | Validation Set | Test Set |
| -----------| ---------------| -------- |
| Accuracy   | 91%            | 89%      |
| F1 Score   | 0.91           | 0.88     |
