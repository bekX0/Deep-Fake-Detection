# Setup & Execution Instructions

This repository implements deepfake detection using transfer learning with EfficientNet models on a subset of the DFDC dataset.

---

##  Installation

First, create a virtual environment and install dependencies:

```bash
pip install -r requirements.txt
```
## Dataset Preparation
This project expects a preprocessed version of the DFDC dataset where each video is represented by a folder of face-cropped images (JPEG format).

Download the dataset from Kaggle:
DFDC Part 34 - Kaggle Dataset

Unzip the downloaded dataset.

Move the extracted dataset folders under the data/images/ directory.
The structure should look like this:

```
deepfake-detection/
├── data/
│   ├── test_data.csv
│   └── images/
│       ├── video_001/
│       │   ├── 0001.jpg
│       │   ├── 0002.jpg
│       │   └── ...
│       ├── video_002/
│       └── ...
```
Make sure that test_data.csv (video labels) is placed in the data/ directory.

This ensures that the training script can correctly match video IDs and access image frames for each sample.

---

## Start Training

Instead of a script, you can run the training directly using the provided notebook:

```bash
# Inside the src/ folder
open and run: dfdc.ipynb
```

Make sure that your dataset paths are correctly defined inside the notebook or `config.py`.

---

## Monitor Training with TensorBoard

To track training progress (loss, accuracy, AUC):

```bash
cd src
tensorboard --logdir=runs
```

Then open your browser and go to: http://localhost:6006

---

## Results Summary

### EfficientNet-B0 (50 Epochs)
- **Validation Accuracy:** 73.92%
- **F1 Score:** 0.7631
- **AUC-ROC:** 0.8212

### EfficientNet-B7 (2 Epochs)
- Reached **65.6% accuracy** and **0.70 AUC** in just 2 epochs
- Training time was significantly longer (7+ min/epoch), making it computationally intensive

---

## Dataset Used

We used the [DFDC Part 34 dataset from Kaggle](https://www.kaggle.com/datasets/greatgamedota/dfdc-part-34/data), which provides 5–10 pre-cropped face frames per video. This eliminates the need for separate face detection and preprocessing.

---

## Contributors

|Member| GitHub |
|------------|--------------------------|
| Dorukhan YILDIZ | [![GitHub](https://skillicons.dev/icons?i=github)](https://github.com/Vitralius) |
| Hikmet Berkin BULUT | [![GitHub](https://skillicons.dev/icons?i=github)](https://github.com/bekX0) |
