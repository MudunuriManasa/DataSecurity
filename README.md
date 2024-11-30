# DataSecurity

## COURSE PROJECT

### Teammates:
- **Mamatha Mudunuri**: 002846231  
- **Manasa Mudunuri**: 002846232  

---

## Project Overview

This project demonstrates training and evaluation of deep learning models using the MNIST dataset with three levels of implementation:

### **Level 1: Fine-Tuning ResNet50 on MNIST**
- **Dataset Used:** MNIST  
- **Model:** ResNet50 (Modified for single-channel MNIST data).  
- **Objective:**
  - Fine-tune the ResNet50 model for classifying MNIST digits.  
  - Use Stochastic Weight Averaging (SWA) for better generalization.  
- **Features:**
  - Adjusted ResNet50 for grayscale MNIST images.  
  - SWA applied to achieve improved accuracy.  
  - Label smoothing for better regularization.  
- **Output:**
  - **Model Saved:** `swa_best_model.pth`.  

---

### **Level 2: Federated Learning with MNIST**
- **Dataset Used:** MNIST  
- **Model:** Custom CNN with batch normalization and dropout.  
- **Objective:**
  - Simulate Federated Learning (FL) with 10 clients.  
  - Detect and mitigate malicious client updates.  
- **Features:**
  - FedAvg (Federated Averaging) for global aggregation.  
  - Malicious client detection using L2 norm outlier analysis.  
  - Local training on client-specific data partitions.  
- **Output:**
  - **Model Saved:** `federated_model.pth`.  

---

### **Level 3: Adversarial and Malicious Data Detection**
- **Dataset Used:** MNIST  
- **Model:** Custom CNN.  
- **Objective:**
  - Detect and mitigate adversarial or malicious patterns in the dataset.  
- **Features:**
  - Detects adversarial patterns in data using **FFT**, **Sobel edge detection**, and statistical heuristics.
  - Identifies poisoned labels using **DBSCAN clustering**.
  - Simulates a scenario where one of the 10 clients becomes **malicious** from a certain training round onward.
    - The malicious client submits **falsified model updates** (e.g., random or incorrect parameters).
    - Implements a **mechanism to detect the malicious client** using L2 norm distance analysis of updates.
    - Minimizes the impact of the malicious client on the overall model by excluding malicious updates during global aggregation.
    - Ensures the learning process remains **robust and accurate** despite the presence of an attacker.
- Applies data cleaning and preprocessing techniques, such as **Gaussian blur** and **label replacement**, for mitigation.
- **Output:**  
  - **Model Saved:** `robust_federated_model.pth`.  

---

## Instructions

1. **Copy the respective level's code** (e.g., Level 1, Level 2, or Level 3) to a Colab notebook.

2. **Ensure that GPU is enabled**:
   - Go to **Runtime > Change runtime type > Select GPU** in the Hardware Accelerator field.

3. **Run each cell sequentially** in the notebook.

---

## General Requirements

### **Python Version**
- **Python 3.x** (Python 3.10 recommended, used in Colab).

### **Hardware and Environment**
- **Platform:** Google Colab (or a local environment with a GPU-enabled machine).  
- **Hardware Acceleration:**
  - Use **GPU** for faster training.
  - Ensure that the runtime type in Google Colab is set to **GPU**:
    - Go to **Runtime > Change runtime type > Select GPU** in the Hardware Accelerator field.
- **CUDA Version:** The default GPU environment in Google Colab is compatible with PyTorch versions using **CUDA 11.x**.

### **Python Libraries**
Install the following dependencies. For Google Colab, install them at the beginning of each notebook using:
```bash
!pip install torch torchvision scikit-learn matplotlib numpy scipy
