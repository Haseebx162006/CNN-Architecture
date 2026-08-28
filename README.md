# Deep Learning Projects

This repository contains two deep learning notebooks for image classification tasks, built using PyTorch and TensorFlow/Keras respectively.

## Notebooks

### 1. Fashion-MNIST Classification with PyTorch (`ann-pytorch.ipynb`)

An Artificial Neural Network (ANN) built with PyTorch for classifying images from the Fashion-MNIST dataset.

#### Dataset

- **Source**: [Kaggle - Zalando Research Fashion-MNIST](https://www.kaggle.com/datasets/zalando-research/fashionmnist)
- **Dataset Path**: `/kaggle/input/datasets/zalando-research/fashionmnist/fashion-mnist_train.csv`
- **Description**: Fashion-MNIST is a dataset of 70,000 grayscale images (28x28 pixels) across 10 clothing categories. It is commonly used as a drop-in replacement for the original MNIST dataset.
- **Classes**: 10 categories (e.g., T-shirt/top, Trouser, Pullover, Dress, Coat, Sandal, Shirt, Sneaker, Bag, Ankle boot)

#### Architecture

The model is a fully connected (dense) neural network implemented using PyTorch:

| Layer | Type | Input | Output | Activation |
|-------|------|-------|--------|------------|
| 1 | Linear | 784 (28x28 flattened) | 128 | ReLU |
| 2 | Linear | 128 | 64 | ReLU |
| 3 | Linear | 64 | 16 | ReLU |
| 4 | Linear | 16 | 10 (classes) | None |

**Total Parameters**: ~102,000

#### Training Configuration

- **Optimizer**: SGD
- **Learning Rate**: 0.1
- **Loss Function**: CrossEntropyLoss
- **Epochs**: 100
- **Batch Size**: 32
- **Train/Test Split**: 80/20 (random_state=42)
- **Preprocessing**: Pixel values normalized to [0, 1] by dividing by 255.0

---

### 2. Dog vs Cat Classification with CNN (`dog-vs-cat.ipynb`)

A Convolutional Neural Network (CNN) built with TensorFlow/Keras for binary classification of dogs and cats.

#### Dataset

- **Source**: [Kaggle - Anthony Therrien Dog vs Cat](https://www.kaggle.com/datasets/anthonytherrien/dog-vs-cat)
- **Dataset Path**: `/kaggle/input/datasets/anthonytherrien/dog-vs-cat/animals`
- **Description**: A dataset containing images of dogs and cats organized in directory structure for easy loading with `image_dataset_from_directory`.
- **Classes**: 2 (Dog, Cat)
- **Image Size**: 256x256 pixels (RGB, 3 channels)

#### Architecture

The model is a CNN implemented using TensorFlow/Keras Sequential API:

| Layer | Type | Filters | Kernel | Strides | Pooling | Activation |
|-------|------|---------|--------|---------|---------|------------|
| 1 | Conv2D | 32 | 3x3 | - | - | ReLU |
| 2 | MaxPooling2D | - | - | 2 | 2x2 | - |
| 3 | Conv2D | 64 | 3x3 | - | - | ReLU |
| 4 | MaxPooling2D | - | - | 2 | 2x2 | - |
| 5 | Conv2D | 128 | 3x3 | - | - | ReLU |
| 6 | MaxPooling2D | - | - | 2 | 2x2 | - |
| 7 | Flatten | - | - | - | - | - |
| 8 | Dense | 128 | - | - | - | ReLU |
| 9 | Dense | 64 | - | - | - | ReLU |
| 10 | Dense | 1 (binary output) | - | - | - | Sigmoid |

**Input Shape**: (256, 256, 3)

#### Training Configuration

- **Optimizer**: Adam
- **Loss Function**: Binary Crossentropy
- **Metrics**: Accuracy
- **Epochs**: 10
- **Batch Size**: 32
- **Train/Validation Split**: 80/20 (seed=42)
- **Preprocessing**: Pixel values normalized to [0, 1] by dividing by 255.0

---

## Requirements

### Common
- Python 3
- NumPy
- Pandas
- Matplotlib

### PyTorch Notebook (`ann-pytorch.ipynb`)
- PyTorch
- Scikit-learn

### TensorFlow Notebook (`dog-vs-cat.ipynb`)
- TensorFlow / Keras

## Environment

Both notebooks are designed to run on the [Kaggle Python environment](https://github.com/kaggle/docker-python). Datasets are loaded from Kaggle's read-only `/kaggle/input/` directory.

## Usage

1. Upload the notebooks to Kaggle.
2. Attach the respective datasets through Kaggle's interface or using `kagglehub`.
3. Run all cells sequentially.

## Notes

- The Fashion-MNIST notebook uses a simple ANN (fully connected layers) rather than a CNN, as the input images are small (28x28) and flattened.
- The Dog vs Cat notebook uses a CNN architecture, which is better suited for larger image classification tasks with spatial feature extraction.