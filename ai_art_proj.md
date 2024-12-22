## AI Image Classification

**Project description:** This project applies machine learning techniques such as Random Forests and Convolutional Neural Networks (CNN) to classify artwork as AI-generated or "real" (i.e. human-made). As AI-generated content becomes increasingly prevalent, this work attempts to address the need for tools that can reliably label content, particularly when it comes to the spread of misinformation. By completing this project, I exercised skills in hyperparameter tuning, model evaluation, and balancing model accuracy with overfitting.

### 1. Initial Data
- **Libraries**: `pandas`, `numpy`, `matplotlib`, `scikit-learn`, `torch`, `torchvision`, `Pillow`
- **Dataset**:
  - 975 images tagged as either "real" (human-made) or "AI", from Kaggle

### 2. Preprocessing
- images were resized to 224x224 pixels and converted to RGB format
- 70/30 split used to create training/testing sets

### 3. Model Performance
- **Random Forest Classifier**:
- performed randomized search cross-validation to find best-performing hyperparameters
  - determined max-depth of 17 and 49 estimators
- used a pruning path to find the best cost-complexity parameter (CCP) alpha
  - determined specifying an alpha only decreased testing accuracy scores
- highest testing accuracy: **68.04%**
- high evidence of overfitting; training accuracy of 100%
  
- **Convolutional Neural Network**:
- experimented with image dimensions, learning rates, and the number of full layers
  - determined learning rate of 0.0005, 256x256 dimensions, and 5 full layers
- with each epoch, testing loss decreased smoothly, suggesting the model was successfully "learning"
- highest testing accuracy: **71.9%**

### 4. Key Findings
- CNN outperformed Random Forest on testing accuracy 80% of the time
- evidence of overfitting with both models

### 5. Future Work & Limitations
- incorporate larger and more diverse datasets to decrease overfitting/make the model more generalizable
- experiment with more advanced models 
