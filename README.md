# Deep Learning Projects

This repository contains two self‑contained Jupyter notebooks that demonstrate image‑classification models built with **PyTorch** and **TensorFlow/Keras**. Both notebooks are designed to run in Kaggle's Python environment and use publicly available datasets.

---

## Notebooks

| Notebook | Framework | Task | Dataset (Kaggle) |
|----------|-----------|------|------------------|
| `ann-pytorch.ipynb` | PyTorch | Fashion‑MNIST classification (10 classes) | [Zalando Research – Fashion‑MNIST](https://www.kaggle.com/datasets/zalando-research/fashionmnist) |
| `dog-vs-cat.ipynb` | TensorFlow/Keras | Binary dog vs. cat classification | [Anthony Therrien – Dog vs Cat](https://www.kaggle.com/datasets/anthonytherrien/dog-vs-cat) |

### 1. `ann-pytorch.ipynb`
* **Model** – Fully‑connected ANN with four linear layers (784 → 128 → 64 → 16 → 10). ReLU activations on all hidden layers.
* **Training** – SGD optimizer (lr = 0.1), Cross‑Entropy loss, 100 epochs, batch size 32, 80/20 train‑test split.
* **Pre‑processing** – Pixel values scaled to `[0, 1]`.

### 2. `dog-vs-cat.ipynb`
* **Model** – Sequential CNN: Conv2D‑ReLU → MaxPool → Conv2D‑ReLU → MaxPool → Conv2D‑ReLU → MaxPool → Flatten → Dense‑ReLU (128) → Dense‑ReLU (64) → Dense‑Sigmoid (binary output).
* **Training** – Adam optimizer, Binary Cross‑Entropy loss, 10 epochs, batch size 32, 80/20 train‑validation split.
* **Pre‑processing** – Images resized to `256×256×3` and pixel values normalised to `[0, 1]`.

---

## Requirements

The notebooks rely on the standard Kaggle Python image, which includes the following packages (no additional installation required):

* Python 3
* NumPy, Pandas, Matplotlib
* **PyTorch** (`torch`, `torchvision`) – for `ann-pytorch.ipynb`
* **Scikit‑learn** – for data splitting in the PyTorch notebook
* **TensorFlow** / **Keras** – for `dog-vs-cat.ipynb`

If you wish to run the notebooks locally, install the same packages via `pip` or `conda`.

---

## Usage (Kaggle)
1. Open the notebook in a Kaggle notebook or a Kaggle competition kernel.
2. Attach the corresponding dataset through the *Add Data* UI (or use `kagglehub.dataset_download`).
3. Run all cells sequentially. The notebooks will download the data, build the model, train, and display basic accuracy plots.

### Running locally
```bash
# Clone the repo
git clone <repo_url>
cd repo

# (Optional) Create a virtual environment
python -m venv venv && source venv/bin/activate

# Install dependencies
pip install torch torchvision scikit-learn tensorflow pandas matplotlib

# Launch Jupyter
jupyter notebook
```
Open the desired notebook and execute the cells.

---

## Project Structure
```
repo/
├─ README.md                # This documentation
├─ ann-pytorch.ipynb        # PyTorch ANN for Fashion‑MNIST
└─ dog-vs-cat.ipynb         # TensorFlow CNN for Dog vs Cat
```

---

## License
This work is provided for educational purposes and is released under the MIT License.
