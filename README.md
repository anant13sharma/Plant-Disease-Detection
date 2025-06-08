# Plant-Disease-Detection
---
## Dataset Credit

**Dataset**: New Plant Diseases Dataset (Augmented)  
**Author**: Samir Bhattarai  
**Source**: [Kaggle - New Plant Diseases Dataset](https://www.kaggle.com/datasets/vipoooool/new-plant-diseases-dataset)  
**Description**: This dataset contains approximately 87,000 RGB images of crop leaves, both healthy and diseased, categorized into 38 classes. It includes an 80/20 split for training and validation, with an additional test set of 33 images for prediction.  
**License**: As per the original authors.

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

Extracted from `training_hist.json` after 10 epochs:

| Metric                   | Value     |
|--------------------------|-----------|
| Final Training Accuracy  | 97.07%    |
| Final Validation Accuracy| 95.08%    |
| Final Training Loss      | 0.1028    |
| Final Validation Loss    | 0.1969    |

The model generalizes well with minimal overfitting.

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

