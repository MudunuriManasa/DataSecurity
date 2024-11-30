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
  - **Test Accuracy:** ~98-99%.  
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
  - **Test Accuracy:** ~97%.  
  - **Model Saved:** `federated_model.pth`.  

---

### **Level 3: Adversarial and Malicious Data Detection**
- **Dataset Used:** MNIST  
- **Model:** Custom CNN.  
- **Objective:**
  - Detect and mitigate adversarial or malicious patterns in the dataset.  
- **Features:**
  - Detect adversarial patterns using FFT and Sobel edge detection.  
  - Identify poisoned labels using DBSCAN clustering.  
  - Mitigate noisy inputs with Gaussian blur preprocessing.  
- **Output:**
  - **Test Accuracy:** ~96-98% after mitigation.  
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
