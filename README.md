# Cat and Dog Image Classification using CNN

A beginner-friendly image classification project built with TensorFlow and Keras. The notebook prepares a Cats and Dogs image dataset, trains a Convolutional Neural Network (CNN), plots training and validation accuracy, and lets you select up to five local images to predict whether each image contains a cat or a dog.

## Features

- Downloads the dataset using KaggleHub.
- Converts readable source images to RGB JPEG files and skips files that cannot be opened.
- Resizes images to **128 × 128** pixels and uses a **80% training / 20% validation** split.
- Normalizes pixel values to the range 0–1 in the model.
- Trains a CNN for **5 epochs**.
- Plots training and validation accuracy.
- Opens a file picker to select up to five images and displays the predicted class with a confidence score.

## Technologies

- Python
- TensorFlow / Keras
- NumPy
- Matplotlib
- Pillow
- KaggleHub
- Tkinter (included with many standard Python installations; used for the image file picker)

## Dataset

The notebook downloads the **Dog and Cat Classification Dataset** from Kaggle using KaggleHub:

`bhavikjikadara/dog-and-cat-classification-dataset`

The notebook expects the downloaded dataset to contain a `PetImages` folder with `Cat` and `Dog` subfolders. The dataset is downloaded locally when the notebook runs; do **not** upload the dataset or the generated `PetImages_Clean` folder to this repository.

## Model architecture

The CNN contains:

1. Rescaling layer (`1./255`)
2. Convolution layer with 32 filters and max pooling
3. Convolution layer with 64 filters and max pooling
4. Flatten layer
5. Dense layer with 128 units and ReLU activation
6. Dropout layer (`0.5`)
7. One sigmoid output for binary classification

The model uses the Adam optimizer, binary cross-entropy loss, and accuracy as its metric.

## Results

In one recorded run, after 5 epochs:

| Metric | Result |
|---|---:|
| Final training accuracy | 93.52% |
| Final validation accuracy | 78.40% |

These results are from a single run and may vary. The gap between training and validation accuracy suggests the model may be overfitting; validation accuracy is a more useful indicator of performance on unseen images than training accuracy. The displayed prediction confidence is the model's sigmoid-based score, not a guarantee that a prediction is correct.

## Getting started

### 1. Download or clone this repository

Download the repository as a ZIP from GitHub, or clone it with Git:

```bash
git clone https://github.com/YOUR-USERNAME/cat-dog-image-classification.git
cd cat-dog-image-classification
```

Replace `YOUR-USERNAME` with your GitHub username.

### 2. Install dependencies

Use Python with a compatible TensorFlow version, then run:

```bash
python -m pip install -r requirements.txt
```

### 3. Open the notebook

Open `Cat_Dog_Classification.ipynb` in Jupyter Notebook or JupyterLab and run the cells from top to bottom. The first run downloads the dataset and creates a cleaned copy locally. Training takes time and depends on your computer.

### 4. Try your own images

At the final step, a file-selection dialog opens. Select up to five JPG, JPEG, PNG, BMP, or WEBP images. The notebook displays each selected image with its predicted class and confidence score.

**Note:** Tkinter file dialogs require a desktop Python environment. They may not work in some hosted notebook environments.

## Repository structure

```text
cat-dog-image-classification/
├── Cat_Dog_Classification.ipynb
├── README.md
└── requirements.txt
```

## Possible improvements

- Add data augmentation and early stopping to help reduce overfitting.
- Evaluate the model on a separate test set.
- Save and reload the trained model instead of retraining each time.
- Add a confusion matrix and precision/recall metrics.

## License

This repository contains project code and documentation. Check the dataset's Kaggle page for its applicable terms and license before redistributing the dataset or derived data.