# ComputerVision

# Project: Age Verification with Computer Vision

## Table of Contents
1. [Project Overview](#project-overview)  
2. [Installation and Setup](#installation-and-setup)  
3. [Data Description](#data-description)  
4. [Exploratory Data Analysis](#exploratory-data-analysis)  
5. [Model Training and Evaluation](#model-training-and-evaluation)  
6. [Results and Conclusions](#results-and-conclusions)  
7. [Project Status](#project-status)  
8. [License](#license)  
9. [Contact](#contact)

---

## Project Overview
The **Good Seed Supermarket** chain aims to stop underage alcohol sales by introducing an automated age verification system. Using **Computer Vision**, the project team analyzes face images to predict a person's age. This repository contains:
- A **Jupyter Notebook** (`ComputerVision.ipynb`) detailing all steps from data exploration to model evaluation.  
- Instructions and code used to train, evaluate, and interpret the age estimation model.

---

## Project Steps 
1. **Perform exploratory data analysis (EDA)** to understand the dataset’s structure and identify potential issues.  
2. **Train and evaluate** a deep learning model for age verification using a GPU platform.  
3. **Compile** all code, outputs, and findings into the **final Jupyter notebook**.  
4. **Summarize conclusions** in the same notebook.  

---

## Installation and Setup
1. **Clone the repository**:
   ```bash
   git clone https://github.com/haladesigns/ComputerVision.git
   cd ComputerVision
   ```
   
2. **Create a virtual environment**:
   ```bash
     python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

5. **Launch Jupyter Notebook**:
   ```bash
     jupyter lab
   ```

6. **Open and explore the `ComputerVision.ipynb`**

## Data Description
- Dataset Size: Approximately 7.6k images.
- Age Range: From 1 to 47 years.
- Data Format:
  - Images: JPEG files in subfolders or a single directory.
  - Labels: A CSV file indicating each image’s true age.
- Preprocessing:
  - Face Detection: Cropping or alignment (if applicable)
  - Image Augmentation: Random flips, rotations, or color jittering (if used)
Refer to the “Data Exploration” section in the notebook for a detailed breakdown of the dataset.

## Exploratory Data Analysis
In the EDA section of the notebook, you’ll find:

Distribution of Ages: A histogram or boxplot showing how many samples exist per age range.
- Sample Images: A few random samples with their annotated ages to confirm label accuracy.
- Missing/Invalid Data: Explanation of any missing images or inconsistent labels and how they were handled.
- Potential Outliers: Observations of ages that may be unrealistic or incorrectly labeled.

EDA highlights:
- Age Distribution: The data is heavily concentrated on the younger ages, with the frequency peaking around ages 15-25.
- Peak Age Group: The highest frequency of individuals seems to be in the age range of approximately 15 to 30 years, suggesting a young population.
- Outliers: There are very few individuals aged 70 and above, which might indicate outliers or a natural cutoff in the dataset.

## Model Training and Evaluation
Inside the notebook, find detailed:

1. Model Architecture:
- Used a pre-trained ResNet50 fine-tuned on the dataset.
- Why this architecture: balanced performance vs. complexity

2. Training Configuration:
- GPU Environment: Training utilized a GPU for faster convergence.
- Hyperparameters: Learning rate set at 1e-4, batch size of 32, trained for 20 epochs.
- Loss Function: Mean Squared Error (MSE) or Mean Absolute Error (MAE) for regression-based age prediction.

3. Evaluation Metrics:
- MAE (Mean Absolute Error) to measure the average absolute difference between predicted and true ages.
- Accuracy Threshold: The percentage of predictions within ± 3 years of the ground truth (example).

4. Cross-Validation or Train/Validation/Test Split:
- Split the dataset into 70% train, 15% validation, 15% test.
- No overlap between sets to avoid data leakage.

5. Training Process:
- Early stopping or checkpoint saving used to prevent overfitting.
- Logs and metrics plotted over epochs in the notebook.

## Results and Conclusions

**Training and Validation Metrics**

- **Training Loss and MAE**  
  - **Loss**: Decreased from **95.35** to **17.02**  
  - **MAE**: Decreased from **7.43** to **3.17**

- **Validation Loss and MAE**  
  - **Loss**: Started at **124.34**, fluctuated throughout, and ended at **93.41**  
  - **MAE**: Started at **8.49**, dropped to **6.64** at best, but rose to **7.65** by the end

**Observations**

- **Consistent Training Improvement**  
  - The training metrics (loss and MAE) steadily decreased, suggesting the model effectively learned from the training data.

- **Validation Fluctuations**  
  - The validation metrics showed significant variation.  
  - Notably, **Epoch #12** saw a spike with a validation loss of **185.63** and MAE of **11.46**.  
  - Although the metrics improved somewhat afterward, they did not reach substantially lower values.

**Conclusions**

- The model demonstrates **steady improvement** on the training set.  
- **Validation performance** is less stable, indicating possible overfitting or the need for more data/preprocessing strategies.  
- Overall, results suggest that while the model can learn age-related features, further refinements (e.g., additional data, hyperparameter tuning) would improve its **generalization** on unseen data.

## Project Status
- Current Status: Completed the initial proof-of-concept model.
- Next Steps:
  - Acquire more balanced data across different age brackets.
  - Explore advanced architectures like Vision Transformers or ensemble methods.
  - Conduct real-time inference tests to gauge performance in a production environment.

## Contributing
If you would like to contribute to this project, please follow these steps:
1. Fork the repository
2. Create a new branch (`git checkout -b feature-branch`)
3. Make your changes and commit them (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature-branch`)
5. Open a pull request

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact
For any questions or feedback, please contact hala.francis@gmail.com
