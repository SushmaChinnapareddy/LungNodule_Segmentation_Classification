Lung Nodule Segmentation Using UNet and Ensemble-Based Classification

Overview

This project uses deep learning to detect and classify lung nodules from CT scan images. It involves two major stages:

1. Segmentation using a UNet++ model with a MobileNetV2 encoder.  
2. Classification using an ensemble of VGG16 and InceptionV3.

The system aims to assist radiologists in early lung cancer diagnosis by improving accuracy and reducing false positives.

Dataset

Dataset Used: LIDC-IDRI (Lung Image Database Consortium and Image Database Resource Initiative)  (Kaggle 2D Slices)

- Total Patients: 1,018  
- Contains annotated CT scans with nodule masks  
- Preprocessing:
  - Converted DICOM to PNG  
  - Resized to 128×128  
  - Normalized pixel values  
  - Threshold-based labeling using mask pixel sum

Methodology

Segmentation:
- Architecture: UNet++  
- Encoder: MobileNetV2 (pretrained on ImageNet)  
- Loss Function: Binary Cross Entropy + Dice Loss  
- Activation: Sigmoid (output)

Classification:
- Models: VGG16 + InceptionV3 (ensemble)  
- Frozen Layers: 25% of each model  
- Fusion: Concatenation of feature vectors  
- Final Layer: Fully connected layer with sigmoid activation

Implementation Details

- Language: Python  
- Libraries: TensorFlow, Keras, NumPy, OpenCV, Matplotlib  
- Training Split: 80% training, 20% testing (patient-wise)  
- Augmentation: Flipping, rotation, brightness/contrast  
- Optimization: Adam optimizer  
- Techniques used: Early stopping and dropout layers to prevent overfitting

Results

Segmentation Performance:
- Dice Coefficient: 0.7516  
- IoU Score: 0.6181

Classification Performance:
- Accuracy: 87.93%  
- Precision: 88.39%  
- Recall: 86.14%  
- AUC: 0.9468
