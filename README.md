# Metro-AQI: Hybrid Deep Learning for Urban Air Quality Classification 🌍🌫️

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.0%2B-orange)
![Flask](https://img.shields.io/badge/Flask-Web%20Framework-lightgrey)
![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)

**Metro-AQI** is an automated, hybrid intelligent framework designed for highly accurate Air Quality Index (AQI) category classification. By combining a **1-Dimensional Convolutional Neural Network (1D-CNN)** with a **Bidirectional Long Short-Term Memory (Bi-LSTM)** network, this system effectively captures both the complex spatial interactions of chemical pollutants and their long-term temporal momentum.

This project abandons traditional single-architecture reliance to provide citizens and authorities with stable, highly reliable early-warning health classifications (e.g., Safe, Moderate, Severe) for highly volatile metropolitan environments.

---

## 🚀 Key Features
* **Hybrid Spatial-Temporal Engine:** Uses a 1D-CNN to extract localized cross-chemical spatial features (PM2.5, PM10, NO2, SO2, CO) and a Bi-LSTM to analyze historical and future momentum.
* **Live Environmental Data Fetching:** Bypasses static datasets in production by connecting directly to the **Open-Meteo API** to fetch real-time pollutant metrics.
* **Advanced Data Pipeline:** Implements localized forward/backward filling for sensor downtime, target discretization for CPCB categories, and 30-day sliding sequence windows for 3D tensor generation.
* **Interactive Web Dashboard:** Fully deployed using a Python Flask backend, allowing end-users to select a metropolitan city and receive instant, color-coded health warnings.

---

## 🧠 System Architecture

The deep learning pipeline is structured to handle the chaotic, non-linear nature of environmental data:

1. **Data Acquisition:** Historical training via CPCB datasets (`city_day.csv`) and live inference via Open-Meteo API.
2. **Preprocessing:**
   * **Imputation:** Localized forward/backward filling to maintain continuous chronological sequences.
   * **Target Discretization:** Raw AQI values are mapped to official CPCB health risk categories and One-Hot Encoded.
   * **Sequence Windowing:** Flat 2D data is transformed into `(samples, time_steps, features)` 3D overlapping arrays using a 30-day sliding window.
   * **Normalization:** Min-Max scaling is applied to balance wild chemical concentration disparities.
4. **Classification Engine:** * **1D-CNN:** Scans the 30-day window to extract immediate chemical dependencies.
   * **Bi-LSTM:** Analyzes the extracted feature maps bidirectionally to understand pollution buildup/dissipation.
   * **Optimization:** Trained using the **Adam Optimizer** and Categorical Crossentropy loss.

---

## 💻 Tech Stack
* **Machine Learning:** TensorFlow, Keras, Scikit-Learn, Pandas, NumPy
* **Data Visualization:** Matplotlib, Seaborn
* **Web Deployment:** Flask, HTML/CSS, Bootstrap
* **External APIs:** Open-Meteo API

git clone [https://github.com/yourusername/Metro-AQI.git](https://github.com/yourusername/Metro-AQI.git)
cd Metro-AQI
