# EEG Classification_LSTM-CNN

This project explores the relationship between deep learning and neuroscience to develop a classification model for EEG data analysis. The main focus is on diagnosing epilepsy, a neurological condition marked by uncontrollable seizures. In addition to being essential for diagnosing epilepsy, EEG data helps to explain a variety of brain conditions and states. The unique patterns that can be seen during seizures, like epileptiform discharges, highlight how useful EEG recordings are for diagnosis.


## Dataset
The Bonn dataset consists of 100 single-channel EEG recordings with a spectral bandwidth of 0.5 Hz to 85 Hz. The recordings last 23.6 seconds and are sampled at 173.61 Hz. Multi-channel EEG recordings were extracted into five distinct sets (A, B, C, D, and E) from an original 128-channel acquisition system. Sets A and B show surface EEG recordings from healthy patients with their eyes closed and open, respectively. While set E consists of intracranial EEG during epileptic seizures, sets C and D record intracranial EEG during seizure-free intervals from both inside and outside of seizure-generating areas of epileptic patients. Each set consists of 100 text files containing 4097 ASCII-coded samples of a single EEG time series. Bandpass filtering was applied to the data, with cutoff frequencies set at 40 Hz and 0.53 Hz. Surprisingly, since strong eye movement artifacts have been removed, this artifact-free dataset.

## 1. Data Preprocessing

The amplitude of the voltage changes in microvolts (mV) over time in seconds. The
x-axis goes from 0 to 4000 seconds, while the y-axis goes from -300 to 400 mV.

![image](https://github.com/Samhita-kolluri/EEGClassification_LSTM-CNN/assets/65637090/83dbc6c3-341a-4f60-8576-054379083f85)

After Feature Extraction 
![image](https://github.com/Samhita-kolluri/EEGClassification_LSTM-CNN/assets/65637090/36c37eb1-08d6-472b-8fd1-5a4bb7e58353)



## 2. Feature Extraction

Utilizing Welch's method, the feature extraction process yields both frequency-domain (peak frequency, average power) and time-domain features (mean, std, skewness, kurtosis) from EEG signals. The resulting NumPy arrays offer valuable insights into signal characteristics, forming a basis for deeper analyses, particularly in EEG classification tasks.

![image](https://github.com/Samhita-kolluri/EEGClassification_LSTM-CNN/assets/65637090/cfab5941-3901-4ae1-9f4a-0c7237714caa)


## 3. Model Selection and Model Training

 A thorough diagram of the neural network's architecture is shown below. The Sequential model, "sequential_2" is composed of multiple layers: a MaxPooling1D layer sits after a Convolutional layer with 64 filters and a kernel size of 3. Two LSTM layers are then used, the first with 128 units and the second with an additional 128 units. The model is intended for binary classification tasks, as evidenced by the final layer, a Dense layer with a sigmoid activation function and one output unit. The model has 230,785 total trainable parameters and uses 901.50 kilobytes of memory.
 
![image](https://github.com/Samhita-kolluri/EEGClassification_LSTM-CNN/assets/65637090/6535f7d3-58b2-4ccc-ad0f-c2209f2759ff)


# Model Evaluation

The model's loss and accuracy evolution over training epochs are shown by the plotted
curves. Effective learning is indicated by a steady decrease in the initial high loss. Nevertheless, the accuracy and loss curves level off at epochs 6 and 8, respectively, indicating that there isn't much more training data improvement possible.

![image](https://github.com/Samhita-kolluri/EEGClassification_LSTM-CNN/assets/65637090/08e46732-2aaf-4ef5-9d2e-097d2ff9fe8b)


# Results and Visualization

A deep learning model's precision-recall curve, with recall represented by the x-axis and precision by the y-axis. The curve's initial high precision and low recall indicate that the model may be accurate overall, but it may be missing true positives. Precision decreases with recall, suggesting a trade-off. With an AUC of 0.78, the model performs well overall in generating predictions across a range of recall thresholds.


![image](https://github.com/Samhita-kolluri/EEGClassification_LSTM-CNN/assets/65637090/5f034dca-e8fa-4ad6-b789-c7e2546cf50d)

