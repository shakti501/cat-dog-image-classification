# Cat and Dog Image Classification using CNN

A beginner-friendly binary image-classification project built with TensorFlow/Keras. The notebook downloads a Cats and Dogs dataset, converts readable images to RGB JPEG files, trains a Convolutional Neural Network (CNN), plots training and validation accuracy, and predicts whether selected local images contain a cat or a dog.

## Features

- Downloads the dataset with KaggleHub.
- Converts readable images to RGB JPEG files and skips files that cannot be opened.
- Loads images at **128 × 128** pixels.
- Uses an **80% training / 20% validation** split.
- Normalizes pixel values to the range 0–1 with a Keras rescaling layer.
- Trains the CNN for **3 epochs** in the current notebook.
- Plots training and validation accuracy with Matplotlib.
- Opens a desktop file picker for JPG, JPEG, PNG, BMP, and WEBP images; processes at most five selected images per run and displays the predicted class with a sigmoid-based confidence score.

## Technologies

- Python
- TensorFlow / Keras
- NumPy
- Matplotlib
- Pillow
- KaggleHub
- Tkinter (used for the desktop image file picker)

## Dataset

The notebook downloads the **Dog and Cat Classification Dataset** from Kaggle using KaggleHub:

`bhavikjikadara/dog-and-cat-classification-dataset`

It expects the downloaded dataset to contain a `PetImages` folder with `Cat` and `Dog` subfolders. The notebook creates a local `PetImages_Clean` directory containing converted images.

In the saved notebook output, the cleaned dataset contained **24,998 images**: **19,999** used for training and **4,999** for validation. These counts can vary if the source dataset changes or some images cannot be read. Do not upload the dataset or generated `PetImages_Clean` folder to this repository.

## Model architecture

The Sequential CNN contains:

1. Rescaling layer (`1./255`)
2. `Conv2D` with 32 filters and ReLU activation
3. `MaxPooling2D`
4. `Conv2D` with 64 filters and ReLU activation
5. `MaxPooling2D`
6. `Flatten`
7. `Dense` layer with 128 units and ReLU activation
8. `Dropout(0.5)`
9. `Dense(1)` with sigmoid activation for binary classification

The model is compiled with the **Adam** optimizer, **binary cross-entropy** loss, and **accuracy** metric.

## Results

The following values are taken from the saved output of the notebook's final training epoch (epoch 3). They describe that recorded run, not a guarantee of future results.

| Metric | Epoch 3 result |
|---|---:|
| Training accuracy | 80.04% |
| Validation accuracy | 75.60% |
| Training loss | 0.4308 |
| Validation loss | 0.5234 |

Validation accuracy is lower than training accuracy, and validation loss is higher than training loss in this run. This may indicate some overfitting; additional evaluation and experiments would be needed to assess generalization reliably. The displayed prediction confidence is derived from the sigmoid output and is not a guarantee that a prediction is correct.

## Getting started

### 1. Clone the repository

```bash
git clone https://github.com/shakti501/cat-dog-image-classification.git
cd cat-dog-image-classification
```

### 2. Install dependencies

Use a Python environment compatible with the TensorFlow version in `requirements.txt`, then run:

```bash
python -m pip install -r requirements.txt
```

KaggleHub is used to download the dataset when the notebook runs. The notebook was saved from a local Jupyter environment; training time and compatibility depend on your computer and installed packages.

### 3. Open and run the notebook

Open `AI_11_Cat&Dog.ipynb` in Jupyter Notebook or JupyterLab and run the cells in order. The first run downloads the dataset and creates the cleaned image directory locally.

### 4. Predict your own images

The notebook uses a Tkinter file-selection dialog. Select up to five JPG, JPEG, PNG, BMP, or WEBP images; the notebook resizes them to 128 × 128 and displays each image with its predicted class and confidence percentage.

**Environment note:** Tkinter dialogs require a desktop environment and may not work in hosted notebook services.

## Current notebook note

The saved notebook contains **three repeated copies** of the image-selection and prediction code. Running all cells in order can therefore open the file picker three times. This repetition can be removed by keeping one copy of that code.

## Repository structure

```text
cat-dog-image-classification/
├── AI_11_Cat&Dog.ipynb
├── README.md
└── requirements.txt
```

## Possible improvements

- Remove the repeated image-prediction cells.
- Add data augmentation and early stopping.
- Evaluate the model on a separate test set and report additional metrics such as a confusion matrix, precision, and recall.
- Save and reload the trained model instead of retraining each time.

## Dataset licensing

This repository contains project code and documentation. Check the dataset's Kaggle page for its applicable terms and license before redistributing the dataset or derived data.
