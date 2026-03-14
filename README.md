This project builds a machine learning pipeline that decodes EEG signals to classify left vs right hand motor imagery using Common Spatial Patterns and an SVM classifier.

The final pipeline reached approximately **90% cross-validated accuracy** on session-specific data.

## Overview

Motor imagery refers to the mental simulation of movement without any actual motion. Even when a person only imagines moving their hand, the brain produces measurable changes in EEG activity. In this project, I used those signals to build a classifier that predicts whether a subject imagined moving their left or right hand.

This project was implemented in Python using:

- **MNE** for EEG preprocessing and dataset access
- **Matplotlib** for visualization
- **scikit-learn** for CSP feature extraction, SVM classification, and model evaluation

## Dataset

For this project, I used the **EEG Motor Movement/Imagery Dataset (EEGBCI)** available through the MNE-Python library. The dataset contains multi-channel EEG recordings from subjects performing motor imagery tasks such as imagined left- and right-hand movement.

## Pipeline

The final pipeline follows this structure:

Raw EEG  
→ Band-pass filtering  
→ Epoch segmentation  
→ Common Spatial Patterns (CSP)  
→ SVM classifier  
→ Left vs right prediction

## Results

The project improved step by step as I refined the signal representation and model setup.

| Method | Accuracy |
|--------|--------:|
| Variance baseline | 50% |
| Frequency restriction | 50% |
| Motor cortex channel selection | 50% |
| CSP + Logistic Regression | 61% |
| Mu-band + temporal window refinement | 70% |
| Session-specific modeling + SVM | 73% |
| CSP + SVM + hyperparameter tuning | **~90%** |

## Repository Structure
```text
eeg-motor-imagery-classifier/
│
├── README.md
├── requirements.txt
├── .gitignore
├── LISCENSE
├── motor_imagery_csp_svm.ipynb
└── pipeline_and_accuracy.png
```
## Running the Project

**1. Clone the repository**
```text
git clone https://github.com/denizflz/eeg-motor-imagery-classifier.git
cd eeg-motor-imagery-classifier
```

**2. Install dependencies**
```text
pip install -r requirements.txt
```

**3. Open the notebook**
```text
jupyter notebook motor_imagery_csp_svm.ipynb
```

## Notes
This implementation focuses on single-subject motor imagery classification in a controlled setting. A natural next step would be extending the pipeline to handle cross-session or cross-subject generalization, or building a closed-loop cursor control simulation using prerecorded EEG data.

## Article
I also wrote a full article explaining the reasoning behind the pipeline, the failed baselines, and the progression from 50% to 90% accuracy. You can access it from [here.](https://medium.com/@denizfiliz/from-raw-eeg-to-90-accuracy-building-a-motor-imagery-classifier-5d3d5659349e)

# License
This project is licensed under the MIT License.
