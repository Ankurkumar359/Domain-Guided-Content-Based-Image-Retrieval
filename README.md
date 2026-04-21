# Domain-Guided Content-Based Image Retrieval

## 📁 Required Folder Structure

```bash
Dataset/
├── Art/
├── Clipart/
├── Product/
├── Real World/

requirements.txt
config.py
dataset.py
inference.py
losses.py
metrics.py
model.py
run_pipeline.bat
test.py
train.py
utils.py
val.py
EDA.py
create_csv.py
plot_config_scores.py
```

---

## 📦 Requirements

Install the following dependencies:

* torch
* numpy
* pandas
* matplotlib
* torchvision
* tqdm
* transformers
* scikit-learn
* Pillow

---

## 🚀 How to Run

Run the following command from the project root:

```bash
.\run_pipeline.bat
```

This will automatically:

* Create a virtual environment
* Install dependencies
* Perform EDA
* Train all configurations
* Evaluate the best model on test data
* Build rankings
* Generate retrieval samples

All outputs will be stored in the **`outputs/`** folder.

---

## 📂 Main Output Folders

### `outputs/checkpoints/`

* Best checkpoint for each configuration

### `outputs/logs/`

* Training history CSV
* Per-configuration loss plots

### `outputs/reports/`

* Validation reports
* Test reports
* Best model summary
* Validation ranking CSV + bar plot
* Test ranking CSV for best model

### `outputs/embeddings/`

* Saved train, validation, and test embeddings

### `outputs/samples/`

* Qualitative retrieval examples

### `outputs/eda/`

* Dataset analysis plots after splitting

---

## 🧠 Architecture

Paper-style model and image-flow diagram.

---

## 📄 Files and Their Roles

### `plot_config_scores.py`

* Plots validation bar graphs for all 27 configurations

### `create_csv.py`

* Builds `dataset_index.csv` by scanning dataset folders
* Assigns train/val/test splits per class-domain

### `EDA.py`

* Performs exploratory data analysis

### `config.py`

* Stores hyperparameters, paths, model configs, augmentations, output paths

### `dataset.py`

* Loads dataset splits
* Creates training triplets
* Prepares evaluation datasets

### `model.py`

* Loads pretrained backbones
* Adds:

  * Trainable head
  * Embedding projection
  * Class classifier
  * Gradient Reversal Layer (GRL)
  * Domain classifier

### `losses.py`

* Class cross-entropy loss
* Domain cross-entropy loss

### `train.py`

* Trains all configurations
* Saves history and best checkpoints
* Selects best model

### `val.py`

* Runs retrieval evaluation
* Saves:

  * Metrics
  * Retrieval outputs
  * t-SNE plots
  * Embeddings

### `test.py`

* Builds ranking CSV across checkpoints
* Evaluates best validation model on test set
* Saves final metrics and summaries

### `metrics.py`

* Generates embeddings
* Computes cosine similarity
* Computes retrieval metrics

### `utils.py`

* Helper utilities for:

  * Transforms
  * Checkpoints
  * History plots
  * Score calculation

### `inference.py`

* Generates qualitative retrieval examples

---

## 📊 Outputs Summary

All experiment artifacts are organized inside:

```bash
outputs/
├── checkpoints/
├── logs/
├── reports/
├── embeddings/
├── samples/
├── eda/
```

---

## ✨ Notes

* Ensure dataset follows the exact folder structure
* Run pipeline from root directory
* Outputs are automatically managed per configuration

---
