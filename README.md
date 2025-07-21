 Anomaly Detection in Network Traffic using Autoencoder & Isolation Forest

Goal -> Detect unusual patterns in network traffic that may indicate intrusions or security breaches using unsupervised learning.

[![Open In Colab](https://colab.research.google.com/drive/1jRoMnTvmVTv6dn42xgGkoWADXq_-gB4t?usp=sharing)


📌 Table of Contents
Problem Statement

Dataset

Techniques Used

Project Structure

Implementation Steps

Visualizations

Results

Future Enhancements

✅ Problem Statement
Network attacks are increasing daily. Detecting malicious traffic early is crucial.
We use unsupervised ML models (Autoencoder & Isolation Forest) to detect anomalies without prior knowledge of attacks.

📂 Dataset
Name: KDD Cup 1999

Size: ~4.8M rows

Features: 41 + 1 label

Target: Normal (0) vs Attack (1)

📥 Download Dataset


🛠 Techniques Used
One-Hot Encoding (for categorical)

Standard Scaling

Autoencoder (Deep Neural Network)

Isolation Forest

ROC-AUC & Confusion Matrix for evaluation

t-SNE for visualization



🔍 Implementation Steps

 Step 1: Data Loading
 
<img width="1020" height="784" alt="image" src="https://github.com/user-attachments/assets/fd1612b9-fb92-4eeb-9bc2-5927b60bb2fa" />


 Step 2: Data Cleaning
 
<img width="1129" height="586" alt="image" src="https://github.com/user-attachments/assets/1d991a89-a253-4e79-ba83-bcd58b5b4826" />


 Step 3: One-Hot Encoding + Scaling
 
<img width="765" height="700" alt="image" src="https://github.com/user-attachments/assets/2302512a-71dd-4e45-95fd-379ba6fd2780" />


 Step 4: Autoencoder Model
 
<img width="672" height="716" alt="image" src="https://github.com/user-attachments/assets/1c0cfcdd-c151-4a1c-9c9c-4cbb6f60abf5" />

autoencoder.compile(optimizer='adam', loss='mse')

autoencoder.fit(X_scaled, X_scaled, epochs=10, batch_size=256, validation_split=0.1)



 Step 5: Anomaly Detection & Evaluation
 
<img width="630" height="620" alt="image" src="https://github.com/user-attachments/assets/b0d14d37-f3d9-40ef-aaa7-9b634884a924" />
✔ Detected anomalies using reconstruction error.

✔ Compared predicted anomalies vs actual.


 Step 6: ROC Curve
 
<img width="556" height="402" alt="image" src="https://github.com/user-attachments/assets/88aeb729-a7ac-4afb-bf70-d19400ba15b9" />


 Step 7: Model Comparison
 
<img width="456" height="171" alt="image" src="https://github.com/user-attachments/assets/a2671f23-331c-4c48-b8ba-80a22b461106" />

<img width="1025" height="408" alt="image" src="https://github.com/user-attachments/assets/9084e067-ee96-4d31-a4cd-d3a11ef70225" />



 Step 8: t-SNE Visualization
 
plot actual labels 

<img width="706" height="557" alt="image" src="https://github.com/user-attachments/assets/a6b18101-2e6b-4c05-99d3-947177d11441" />

plot autoencoder prediction

<img width="706" height="556" alt="image" src="https://github.com/user-attachments/assets/21e81177-7ce0-4bcb-9b34-3dc4d9554652" />


✅ Results

      precision    recall  f1-score   support


           0       0.79      0.99      0.88    812814
           1       0.92      0.19      0.31    262178

    accuracy                           0.80   1074992
    macro avg       0.85      0.59      0.60   1074992
    weighted avg       0.82      0.80      0.74   1074992
  

🚀 Future Enhancements
Deploy as Streamlit Dashboard

Real-time detection API

Compare with Variational Autoencoder and GAN-based models

