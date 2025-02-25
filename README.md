# AI-Powered Anomaly Detection in Medical Images (Mock Data)

This repository contains the code for an AI-powered diagnostic assistant that detects anomalies in simulated medical images (X-rays). This project was developed for the Girl Hackathon 2025 - Software Engineering Track, with a focus on iterative improvement and achieving a robust, well-generalized model.

## Problem Statement

This project aims to assist healthcare professionals in diagnosing diseases more accurately and efficiently by analyzing medical images and patient data.  A Convolutional Neural Network (CNN) is trained on mock data to identify potential anomalies.  The development process involved iteratively refining the model and data generation to achieve a balance between high accuracy and preventing overfitting.

## Repository Structure

*   **`main.py`:**  The main Python script containing the data generation, model definition, training, and evaluation code.  This script includes the final, best-performing model.
*   **`best_model.keras`:** (Created after running `main.py`) The saved Keras model representing the best-performing iteration.
*   **`requirements.txt`:** A list of required Python packages.

## Getting Started

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/prekshadhongade/Medical-diagnosis-googleindiahackathon
    cd Medical-diagnosis
    ```

2.  **Create a virtual environment (recommended):**

    ```bash
    python3 -m venv .venv
    source .venv/bin/activate  # On Linux/macOS
    .venv\Scripts\activate  # On Windows
    ```

3.  **Install dependencies:**

    ```bash
    pip install -r requirements.txt
    ```
     Or if ,errors:
    ```
     pip install tensorflow scikit-learn matplotlib numpy opencv-python
    ```
4.  **Run the code:**

    ```bash
    python main.py
    ```

    This will execute the complete pipeline: data generation, preprocessing, model definition, training, evaluation, and result visualization.

## Iterative Development and Model Evolution

The final model presented in `main.py` is the result of an iterative development process.  Key improvements made over multiple iterations include:

*   **Initial Model (Baseline):**  A simple CNN was created to establish a baseline performance.
*   **Data Augmentation:**  Techniques like random flips, rotations, brightness/contrast adjustments, and Gaussian blur were added to the training data pipeline to improve model robustness and prevent overfitting.  The `tf.data` API was used for efficient data handling.
*   **Model Complexity Adjustment:**  The number of layers and filters in the CNN was tuned, along with the size of the dense layers in both the image and patient data branches.
*   **Regularization:** Dropout and L2 regularization were incorporated to further combat overfitting.
*   **Hyperparameter Tuning:** The learning rate and other hyperparameters were adjusted based on validation set performance.  Callbacks like `EarlyStopping` and `ReduceLROnPlateau` were used to automate this process.
*   **Data Generation Refinement:** The mock data generation was improved to create more realistic and varied anomalies, including variations in shape, size, and intensity.  The class balance (ratio of images with and without anomalies) was also adjusted.
*   **Training Procedure**:Splitting training set to Train and Test and increasing the sample data.
## Data Generation

The `generate_mock_data` function in `main.py` creates synthetic X-ray images (64x64 grayscale). Anomalies, which are simulated as bright circles or ellipses on low intensity images, gaussian Blur are added. It also creates the dataset with patient data (age, fever, cough).
Data Augmentations like flips, rotations, brightness/contrast changes, gaussian blur,random JPEG Quality applied on data during Training to improve the generalisation and reduce the overfitting,
The data are divided to training,validation and testing dataset.

## Model Architecture

The final model is a multi-input CNN:

*   **Image Branch:** Convolutional and max-pooling layers (with Batch Normalization) extract features from the X-ray images.
*   **Patient Data Branch:** Dense layers process patient data (age, fever, cough).

The outputs are concatenated, then processed by further dense layers.  A final softmax layer predicts the anomaly probability.

## Training

*   **Optimizer:** Adam.
*   **Loss:** Categorical cross-entropy.
*   **Callbacks:** `EarlyStopping`, `ReduceLROnPlateau`, and `ModelCheckpoint`.
*   **Batch Size:** 32
*   **Epochs:** Up to 100 (but `EarlyStopping` typically terminates training sooner).

## Evaluation

Evaluation is performed on a held-out test set using accuracy, precision, recall, and F1-score.

## Contributing

Suggestions for further improvements are welcome.
## License

MIT License

