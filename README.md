# ARMD-Classification
Deep learning project for classifying Age-related Macular Degeneration (Wet, Dry, Healthy) using U-Net and a CNN-LSTM model.
**Project Overview**
This project focuses on detecting Age-related Macular Degeneration (AMD) from fundus
images using a hybrid deep learning pipeline. It includes image preprocessing, data
augmentation, segmentation, and a CNN-LSTM-based classification model to classify the
fundus images into three categories:
1. Wet AMD
2. Dry AMD
3. Healthy

**Project Structure**
The project is divided into the following stages:
1. Image Preprocessing (ARMD_Preprocessing.ipynb)
Applies CLAHE (Contrast Limited Adaptive Histogram Equalization) to enhance
contrast in the L-channel of LAB colour space.
Uses Median Filtering to reduce noise while preserving edges and fine structures.
Operates category-wise over folders: wetAMD, dryAMD, and healthy.
2. CycleGAN-Based Image Generation (ARMD_Preprocessing.ipynb)
Trains a CycleGAN with two generators and two discriminators to generate synthetic fundus images for wetAMD, dryAMD, and healthy classes.
Uses adversarial loss, cycle consistency loss, and identity loss to ensure realistic image
translation.
Outputs 50 additional images per class to improve training dataset diversity.
3. Traditional Data Augmentation (ARMD_Preprocessing.ipynb)
Employs Albumentations library to apply augmentations like:
• Horizontal Flip
• Rotation
• Brightness/Contrast adjustment
• Shift-Scale-Rotate
• Gaussian Blur
• Hue/Saturation change
Ensures a balanced and enriched dataset with 150 additional images per category.
4. Segmentation using U-Net (Classification_WebInterface.ipynb)
Applies U-Net architecture to segment lesion areas and retinal features in the fundus
images.
Enhances feature extraction and helps focus the classifier on disease-relevant regions.
5. Dataset Preparation and Normalization (Classification_WebInterface.ipynb)
o Reads and resizes images to 128×128.
o Normalizes pixel values to range [0, 1].
o Organizes images into separate training and validation folders.
o One-hot encodes labels into 3 classes: wetAMD, dryAMD, and healthy.
6. Classification Model (Classification_WebInterface.ipynb)
Implements a CNN-LSTM hybrid model to capture both spatial and temporal (or
structured) features.
CNN layers extract spatial patterns; LSTM layers model dependencies across sequences
or patches.
Output: Predicts each image as either Wet AMD, Dry AMD, or Healthy.

**Dataset**
Fundus images were collected from private hospitals and were organized into three categories- dry, wet and healthy.
Preprocessed images are stored in output_dir.
Augmented images are stored in augmented_images.

**Requirements**
Python 3.8+
OpenCV
NumPy
TensorFlow / Keras
Albumentations
Scikit-learn
Install dependencies using:
pip install opencv-python numpy tensorflow albumentations scikit-learn

**How to Run**
1. Set up your environment: Make sure Python 3.8+ is installed. Install all dependencies using:
pip install opencv-python numpy tensorflow albumentations scikit-learn
2. Run the preprocessing and augmentation notebook:
Open Augmentation_CycleGAN.ipynb and run all cells to apply image enhancement, CycleGAN
generation, and traditional augmentations.
3. Run the classification notebook:
Open Classification_WebInterface.ipynb and run all cells to prepare the dataset, apply U-Net
segmentation, and train the CNN-LSTM classification model.
