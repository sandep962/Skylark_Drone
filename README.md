
# Aerial GCP Pose Estimation

## About the Project

This project is my solution for the Computer Vision Engineering assignment.

The goal is to automatically find the center of a Ground Control Point (GCP) marker from aerial drone images and identify its shape.

The model performs two tasks:

- Predict the center (x, y) coordinates of the GCP marker.
- Classify the marker as Cross, Square or L-Shape.

---

## Dataset

Training Images: 996

Test Images: 300

The dataset contains aerial images collected from different survey locations. The images are organized in nested folders based on project, survey and GCP ID.

During EDA, I found that 4 training images were missing shape labels, so I excluded them from training.

---

## What I Did

Before training the model, I first explored the dataset.

I checked:

- Image sizes
- Shape distribution
- Missing labels
- Coordinate ranges
- Corrupted images
- Sample annotations

This helped me understand the dataset before building the model.

---

## Model

I used a pretrained ResNet18 as the backbone because it is lightweight and performs well for image feature extraction.

The model has two output heads:

- Regression head to predict the GCP coordinates.
- Classification head to predict the marker shape.

The coordinates were normalized during training and converted back to the original image size during inference.

---

## Training

Image size: 512 × 512

Image preprocessing:

- Resize
- ToTensor
- ImageNet Normalization

Loss Functions:

- SmoothL1Loss for coordinate prediction
- Weighted CrossEntropyLoss for shape classification

Optimizer:

- AdamW

Learning Rate:

0.0001

Training Epochs:

16

---

## Challenges

Some challenges I faced during this assignment were:

- Different image resolutions
- Missing shape labels
- Imbalanced classes
- Stable coordinate prediction

I handled these during preprocessing and model training.

---

## Output

The final model generates a `predictions.json` file in the same format as the training annotations.

It predicts:

- GCP center coordinates
- Marker shape

The trained model weights are saved as:

`best_model.pth`

---

## How to Run

1. Load the trained model.
2. Run the inference script on the test dataset.
3. The script generates `predictions.json`.

---

## Libraries Used

- Python
- PyTorch
- Torchvision
- NumPy
- Pillow

---
