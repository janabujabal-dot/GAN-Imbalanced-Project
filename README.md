# Exploring GAN Variants for Balancing Imbalanced Datasets

## Course
Special Topics in Data Science

## Student
Jana AbuJabal

## Project Overview
This project investigates the use of Generative Adversarial Networks (GANs) to solve the class imbalance problem in the Bank Marketing dataset.

Two generative models were implemented:

- Vanilla GAN
- Wasserstein GAN (WGAN)

Synthetic samples were generated for the minority class and used to balance the dataset. A Random Forest classifier was then trained to evaluate the impact of data augmentation.

---

## Dataset
- **Dataset Name:** Bank Marketing Dataset
- **Source:** UCI Machine Learning Repository
- **Target Variable:** `deposit`

### Original Class Distribution
- No: 5,873
- Yes: 5,289

### Artificially Imbalanced Distribution
- No: 5,873
- Yes: 1,000

---

## Data Preprocessing
The following preprocessing steps were applied:

1. Target encoding (`no = 0`, `yes = 1`)
2. One-hot encoding for categorical features
3. Feature scaling using `MinMaxScaler`

Final dataset shape:
- Samples: 6,873
- Features: 42

---

## GAN Models

### Vanilla GAN
- Generator and Discriminator implemented using fully connected layers
- Trained for 1,000 epochs using Adam optimizer

### WGAN
- Critic network replaces the discriminator
- Uses Wasserstein loss and RMSprop optimizer
- Weight clipping applied for stability

---

## Synthetic Data Generation
Each model generated **4,873 synthetic minority samples** to balance the dataset.

Balanced class distribution:
- No: 5,873
- Yes: 5,873

---

## Classification Model
A **Random Forest Classifier** was trained and evaluated on:

1. Original Imbalanced Dataset
2. Dataset Balanced with Vanilla GAN
3. Dataset Balanced with WGAN

Train-test split:
- 70% Training
- 30% Testing

---

## Evaluation Metrics
The following metrics were used:

- Accuracy
- Precision
- Recall
- F1-score
- AUC-ROC
- Confusion Matrix

---

## Results

| Dataset | Accuracy | Precision | Recall | F1-score | AUC-ROC |
|--------|--------:|--------:|--------:|--------:|--------:|
| Original Imbalanced | 0.8783 | 0.6467 | 0.3600 | 0.4625 | 0.9107 |
| Vanilla GAN Balanced | 0.9293 | 0.9684 | 0.8876 | 0.9263 | 0.9852 |
| WGAN Balanced | 0.9308 | 0.9691 | 0.8899 | 0.9278 | 0.9851 |

---

## Key Findings
- Recall improved from **36%** to approximately **89%**.
- F1-score improved from **0.46** to approximately **0.93**.
- WGAN achieved the best overall performance.

---

## Project Files

- `gan_project.ipynb` — Source code
- `GAN_Project_Report.pdf` — Final report
- `GAN_Project_Presentation.pptx` — Presentation slides
- `README.md` — Project documentation

---

## Technologies Used
- Python
- TensorFlow / Keras
- Scikit-learn
- Pandas
- NumPy
- Matplotlib

---

## Conclusion
GAN-based synthetic data generation proved highly effective for balancing imbalanced datasets and significantly improved classification performance. WGAN achieved the best results and demonstrated slightly better performance than Vanilla GAN.
