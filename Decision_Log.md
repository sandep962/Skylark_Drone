
# Decision Log

## Name

Sandeep Dattatreya Bhajantri

Registration Number: 1BY23AI139

---

## Assignment Understanding

I understood the assignment as a multi-task learning problem where the model has to predict the center coordinates of a Ground Control Point (GCP) and classify its shape at the same time.

---

## My Approach

I started with Exploratory Data Analysis (EDA) to understand the dataset.

I analyzed:

- Image resolutions
- Shape distribution
- Missing labels
- Coordinate ranges
- Sample annotations
- Corrupted images

During EDA, I found that 4 images were missing shape labels, so I excluded them from training.

---

## Model Selection

I selected a pretrained ResNet18 backbone because it is lightweight, reliable, and suitable for feature extraction.

The model has two prediction heads:

- Regression Head for predicting x and y coordinates.
- Classification Head for predicting the marker shape.

---

## Data Preprocessing

The following preprocessing steps were used:

- Resize images to 512 × 512
- Convert images to tensors
- Apply ImageNet normalization

The coordinates were normalized between 0 and 1 during training and converted back to pixel coordinates during inference.

---

## Training Strategy

Loss Functions

- SmoothL1Loss for coordinate prediction
- Weighted CrossEntropyLoss for shape classification

Optimizer

- AdamW

Learning Rate

- 0.0001

Training was stopped after obtaining a stable and low training loss.

---

## Challenges

The main challenges I faced were:

- Different image resolutions
- Missing shape labels
- Class imbalance
- Stable coordinate prediction

These challenges were handled during preprocessing and training.

---

## Final Deliverables

The final submission includes:

- Source Code / Notebook
- README.md
- requirements.txt
- predictions.json
- best_model.pth

The trained model was used to generate predictions for all 300 test images successfully.
