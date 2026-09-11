# Stress Detection Using Physiological Signals

A deep learning project for identifying stress states from physiological signals using the **WESAD (Wearable Stress and Affect Detection)** dataset.

The project explores preprocessing, physiological feature extraction, class balancing, CNN-LSTM based sequence modelling, and model evaluation for binary stress classification.

## Overview

Stress produces measurable changes in physiological signals such as heart activity, skin conductance, respiration, and body temperature. This project uses these signals to build a machine learning pipeline capable of distinguishing between **stress** and **non-stress** states.

The main model combines convolutional layers for extracting local patterns from physiological signals with recurrent layers for capturing temporal dependencies.

## Key Components

* **Multi-scale CNN feature extraction** using different convolution kernel sizes
* **Bidirectional LSTM layers** to learn temporal relationships in the signals
* **Batch normalization and dropout** for improved training stability and regularization
* **Class balancing** to address differences in the number of stress and non-stress samples
* **Physiologically informed synthetic data generation** for augmenting the training data
* **Performance evaluation** using accuracy, precision, recall, F1-score, and confusion matrices
* **Separate inference module** for running predictions using the trained model

## Dataset

The project uses the **WESAD (Wearable Stress and Affect Detection)** dataset.

The dataset contains physiological recordings collected from subjects under different experimental conditions. The signals used in this project include:

* ECG — Electrocardiogram
* EDA — Electrodermal Activity
* EMG — Electromyogram
* Respiration
* Temperature
* Accelerometer

The WESAD dataset is **not included in this repository** because of its size.

Place the downloaded dataset in the following directory:

```text
WESAD/
```

The repository also contains a dataset download/helper script where applicable.

## Model

The primary model uses a hybrid **CNN-BiLSTM** architecture.

### CNN component

Multiple convolutional filters are used to capture physiological patterns at different temporal scales. The architecture uses kernel sizes of:

```text
3
5
7
```

This allows the model to learn both short-term and broader local variations in the input signals.

### LSTM component

Bidirectional LSTM layers process the extracted features in both temporal directions. This helps the model capture dependencies that occur across different points in a physiological signal sequence.

### Regularization

The network also uses:

* Batch normalization
* Dropout
* Weighted training/class balancing

The final improved architecture contains approximately **377,922 trainable parameters**.

## Model Performance

The evaluated model achieved the following results on the test set:

| Metric        |  Score |
| ------------- | -----: |
| Accuracy      | 98.79% |
| F1 Macro      | 98.76% |
| F1 Weighted   | 98.79% |
| Stress F1     | 98.94% |
| Non-Stress F1 | 98.59% |

### Classification Results

```text
              precision    recall  f1-score   support

Non-Stress       0.98       0.99      0.99       879
Stress           0.99       0.98      0.99      1182

accuracy                              0.99      2061
macro avg        0.99       0.99      0.99      2061
weighted avg     0.99       0.99      0.99      2061
```

These results indicate that the model performs well on the evaluated test data for distinguishing between the two classes.


## Results and Observations

The trained model achieves high classification performance on the evaluated test set. The combination of convolutional feature extraction and recurrent sequence modelling allows the network to learn both local signal patterns and temporal relationships.

The class-wise F1-scores are also closely balanced, suggesting that the model is not relying exclusively on one of the two classes.

However, the reported performance should be interpreted specifically in the context of the WESAD dataset and the evaluation methodology used in this project. Performance on other datasets or real-world physiological recordings may differ.

## Technologies Used

* **Python**
* **TensorFlow / Keras**
* **NumPy**
* **Pandas**
* **Scikit-learn**
* **SciPy**
* **Matplotlib**
* **Seaborn**
* **OpenCV**
* **DeepFace**
* **KaggleHub**
* **imbalanced-learn**

