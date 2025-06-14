# Plant-Disease-Detection

## Overview

This project aims to develop a deep learning-based classification system for identifying **plant diseases from leaf images**. Using a Convolutional Neural Network (CNN) trained on a large, augmented dataset of healthy and diseased leaves, the system classifies input images into categories such as *Healthy*, *Early Blight*, and *Late Blight*.

The training process achieved high performance:
- **98.10% accuracy on the training set**
- **95.08% accuracy on the validation set**

This suggests the model generalizes well on clean and consistent image data. The system is suitable for research, early-stage deployment, and educational use in digital agriculture.

### Where the Model Performs Well
- On high-quality, lab-like images with consistent lighting and backgrounds
- On the specific diseases and plant types included in the training dataset
- In environments where images are collected in controlled settings (e.g., research labs, phone apps with leaf scanner modes)

### Where the Model May Perform Poorly
- On images taken in real-world conditions with **variable lighting**, **blur**, **partial leaves**, or **noisy backgrounds**
- On **plant species or disease types not included** in the training set
- When applied to **non-leaf plant parts** (e.g., stem or fruit)
- In scenarios where multiple diseases appear simultaneously or where symptoms are subtle or overlapping

To improve field performance, further training with diverse, real-world images and domain-specific tuning would be required.

This project demonstrates the feasibility of CNNs for agricultural image classification and serves as a foundation for scalable, AI-assisted plant health monitoring tools.

---
## Dataset Credit

- **Source**: Subset of potato leaf images from the PlantVillage dataset, sourced via [Mendeley Data](https://data.mendeley.com/datasets/tywbtsjrjv/1) (Pandian & Gopal, 2019, DOI: 10.17632/tywbtsjrjv.1), derived from the original [PlantVillage dataset](https://arxiv.org/abs/1511.08060) (Hughes & Salathé, 2015).

---

## Model Architecture

The CNN model used in this project includes the following components:

- Multiple `Conv2D` layers with ReLU activation
- `MaxPooling2D` layers for downsampling
- `Dropout` layers for regularization
- `Flatten` and `Dense` layers
- Final `Dense` output layer with Softmax for multi-class classification

**Compiled with**:
- **Loss Function**: `SparseCategoricalCrossentropy`
- **Optimizer**: `Adam`
- **Metrics**: `Accuracy`

---

## Training

Training is done using the notebook: `Train_plant_disease.ipynb`.

- Uses `image_dataset_from_directory` for loading images
- Images normalized by scaling pixel values to [0, 1]
- Trained for 10 epochs
- Model saved as:
  - `trained_model.h5`
  - `trained_model.keras`
- Metrics saved in `training_hist.json`

---

## Evaluation

After training for 10 epochs, the model was evaluated on the complete training and validation datasets.

| Metric                   | Value       |
|--------------------------|-------------|
| Final Training Accuracy  | 98.10%      |
| Final Validation Accuracy| 95.08%      |
| Final Training Loss      | 0.0600      |
| Final Validation Loss    | 0.1969      |

These results confirm that the model generalizes well, with strong validation performance and minimal signs of overfitting.
## Screenshots

### Model Accuracy and Loss over Epochs
![Accuracy and Loss Plot](screenshots/a.png)

### Confusion Matrix
![Confusion Matrix](screenshots/b.png)



---

## Testing

Testing is performed in `Test_Plant_Disease.ipynb`:

- Load image using `load_img()`
- Preprocess to match input size (256x256), normalize, and batch
- Predict using `model.predict()`
- Map index to class name and display result

Currently tested manually by specifying the image file path.

---

## Installation

### 1. Clone the repository
```bash
git clone https://github.com/anant13sharma/Plant-Disease-Detection.git
cd Plant-Disease-Detection

