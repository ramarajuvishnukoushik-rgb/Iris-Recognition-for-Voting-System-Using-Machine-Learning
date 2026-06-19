# Iris-Recognition-for-Voting-System-Using-Machine-Learning     # Iris Recognition for Voting System Using Machine Learning

A biometric voter-authentication system that uses iris recognition powered by a Convolutional Neural Network (CNN) to verify voter identity before granting access to an electronic voting system.

This is a B.Tech Major Project from the Department of Computer Science and Engineering (AI&ML), CMR Engineering College (UGC Autonomous), affiliated to JNTU Hyderabad, 2024-2025.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [System Architecture](#system-architecture)
- [Dataset](#dataset)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Results](#results)
- [Future Work](#future-work)
- [Team](#team)
- [Acknowledgements](#acknowledgements)
- [Project Report](#project-report)

## Overview

Iris recognition is one of the most reliable biometric techniques for human identification, as the iris pattern is unique to every individual, stable over a lifetime, and extremely difficult to forge or duplicate. This project applies that reliability to a real-world problem: secure, fraud-resistant voter authentication.

The system captures a voter's iris image, extracts the iris region using the Hough Circle Transform, and classifies the individual using a trained Convolutional Neural Network. Once the voter's identity is confirmed against an enrolled database, they are authenticated to proceed with voting — reducing the risk of impersonation or duplicate voting in the process.

## Features

- Iris image acquisition and preprocessing
- Automatic iris localization and segmentation using the **Hough Circle Transform**
- Feature extraction from iris texture patterns
- Identity classification using a custom-trained **CNN** model
- Desktop GUI (built with Tkinter) for:
  - Uploading the iris dataset
  - Generating and loading the CNN model
  - Viewing accuracy/loss graphs
  - Uploading a test iris image and recognizing the voter's identity
- Trained and evaluated on the **CASIA Iris Dataset** (108 subjects)

## Tech Stack

| Component | Technology |
|---|---|
| Language | Python |
| Deep Learning | Keras / TensorFlow |
| Image Processing | OpenCV (`cv2`) |
| Numerical Computing | NumPy |
| GUI | Tkinter |
| Visualization | Matplotlib |

## System Architecture

```
Iris Image Acquisition
        │
        ▼
Preprocessing (grayscale, median blur, noise reduction)
        │
        ▼
Iris Segmentation (Hough Circle Transform)
        │
        ▼
Normalization
        │
        ▼
Feature Extraction (CNN convolutional layers)
        │
        ▼
Classification (Softmax over enrolled identities)
        │
        ▼
Match Decision → Accept / Reject voter
```

The CNN architecture used:

```
Input (64x64x3)
  → Conv2D(32,3x3) + ReLU → MaxPooling(2x2)
  → Conv2D(32,3x3) + ReLU → MaxPooling(2x2)
  → Flatten
  → Dense(256) + ReLU
  → Dense(108) + Softmax
```

## Dataset

This project uses the **CASIA Iris Dataset**, containing iris images from 108 subjects. Each subject folder contains multiple grayscale iris images used for training and testing the CNN model.

> Note: The dataset is not included in this repository due to size and licensing. Download it from the official [CASIA Iris Image Database](http://biometrics.idealtest.org/) source and place it in a `dataset/` folder before running the training script.

## Installation

1. Clone the repository
   ```bash
   git clone https://github.com/<your-username>/iris-recognition-voting-system.git
   cd iris-recognition-voting-system
   ```

2. Create a virtual environment (recommended)
   ```bash
   python -m venv venv
   source venv/bin/activate      # On Windows: venv\Scripts\activate
   ```

3. Install dependencies
   ```bash
   pip install -r requirements.txt
   ```

4. Place the CASIA Iris dataset inside the `dataset/` folder (see [Dataset](#dataset)).

## Usage

Run the main application:

```bash
python main.py
```

This opens the GUI with the following options:

| Button | Action |
|---|---|
| **Upload Iris Dataset** | Select the folder containing the CASIA Iris dataset |
| **Generate & Load CNN Model** | Train (or load an existing) CNN model on the dataset |
| **Accuracy & Loss Graph** | Display the training accuracy/loss curve |
| **Upload Iris Test Image & Recognize** | Upload a test iris image and predict the voter's identity |
| **Exit** | Close the application |

## Project Structure

```
iris-recognition-voting-system/
│
├── main.py                  # GUI entry point
├── requirements.txt
├── README.md
├── LICENSE
│
├── dataset/                 # CASIA Iris dataset (not included, see Dataset section)
│   └── CASIA1/
│
├── model/                   # Saved model artifacts (generated after training)
│   ├── model.json
│   ├── model_weights.h5
│   ├── X.txt.npy
│   ├── Y.txt.npy
│   └── history.pckl
│
├── testSamples/             # Sample iris images for testing recognition
│
└── docs/
    └── IRIS_RECOGNITION_REPORT.pdf   # Full major project report
```

> Adjust this section to match your actual folder layout before publishing.

## Results

- The CNN model was trained for 60 epochs on the CASIA Iris dataset (108 classes).
- Training accuracy approached 100%, with loss converging close to 0 as epochs increased.
- The system correctly predicted the enrolled person ID from unseen iris test images during evaluation.

*(Add your actual accuracy/loss graph screenshots here once uploaded, e.g. `![Loss Graph](docs/images/loss_graph.png)`)*

## Future Work

- Extend to a true multimodal system (iris + fingerprint or face) for higher accuracy and spoof resistance
- Test against larger and more diverse iris datasets beyond CASIA
- Tune CNN hyperparameters (layers, filters, learning rate) for improved generalization
- Add liveness detection to prevent spoofing attacks
- Deploy as a web or mobile application with real-time camera capture

## Team

| Name | Roll Number |
|---|---|
| M. Sharath | 228R5A6615 |
| P. Vignesh | 228R5A6617 |
| R. Vishnu | 228R5A6618 |
| S. Nithin | 228R5A6619 |

**Internal Guide:** Mr. D. Siva Raja Kumar, Assistant Professor, Dept. of CSE (AI&ML)

## Acknowledgements

This project was carried out at the Department of Computer Science & Engineering (AI&ML), **CMR Engineering College** (UGC Autonomous), Hyderabad, in partial fulfillment of the requirements for the degree of Bachelor of Technology, under the guidance of Mr. D. Siva Raja Kumar.

## Project Report

The complete major project report — including the literature review, methodology, mathematical formulation, and detailed findings — is available at [`docs/IRIS_RECOGNITION_REPORT.pdf`](docs/IRIS_RECOGNITION_REPORT.pdf).

## License

This project is intended for academic and educational purposes. Add a license of your choice (e.g., MIT) if you want others to be able to reuse the code — see [choosealicense.com](https://choosealicense.com/).
