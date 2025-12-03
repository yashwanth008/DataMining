# Clustering Assignments Overview

This repository contains a collection of Python notebooks  implementing various clustering algorithms and anomaly detection techniques. Each assignment focuses on a specific method or data modality (tabular, text, image, audio, time-series).

## Table of Contents

| Assignment | Topic | Key Libraries |
| :--- | :--- | :--- |
| **A** | K-Means from Scratch | `numpy`, `matplotlib` |
| **B** | Hierarchical Clustering | `scipy`, `sklearn` |
| **C** | Gaussian Mixture Models | `sklearn` |
| **D** | DBSCAN | `sklearn` |
| **E** | Anomaly Detection | `pyod` |
| **F** | Time Series Clustering | `tslearn` |
| **G** | Document Clustering | `sentence-transformers` |
| **H** | Image Clustering | `clip`, `torch`, `PIL` |
| **I** | Audio Clustering | `librosa`, `sklearn` |

## Implementation Details: What i Have Done

### A) K-Means from Scratch
* **Implementation:** i built a `KMeansScratch` class using pure **NumPy**.
* **Logic:** i manually implemented the iterative loop of calculating Euclidean distances, assigning points to the nearest centroid, and updating centroids to the mean of assigned points.
* **Validation:** I compared our scratch implementation against `sklearn.cluster.KMeans` using the **Silhouette Score** to ensure accuracy.

### B) Hierarchical Clustering
* **Dendrogram:** i used `scipy.cluster.hierarchy` to generate and plot a dendrogram, visualizing the merging process of data points.
* **Clustering:** i applied **Agglomerative Clustering** (bottom-up) on the "Moons" dataset to demonstrate how it handles structural data without a pre-defined $K$.

### C) Gaussian Mixture Models (GMM)
* **Data Generation:** i created a stretched (anisotropic) dataset to challenge standard K-Means.
* **Modeling:** i trained a `GaussianMixture` model to learn the probability distributions of the clusters.
* **Visualization:** i plotted **Confidence Ellipses** to visualize the covariance (shape) and orientation of the learned Gaussian distributions.

### D) DBSCAN (Density-Based)
* **Environment Fix:** i utilized `sklearn.cluster.DBSCAN` directly to avoid Python 3.12 incompatibility issues with PyCaret.
* **Setup:** i scaled the data using `StandardScaler` (critical for distance-based density).
* **Execution:** i ran the algorithm with `eps=0.3` and `min_samples=5` to successfully separate two interleaving half-circles ("Moons") and identify noise points.

### E) Anomaly Detection
* **Library:** i utilized the **PyOD** (Python Outlier Detection) library.
* **Method:** i trained a **k-Nearest Neighbors (KNN)** detector.
* **Output:** i visualized the decision boundaries, highlighting points that ire statistically distant from the dense regions of the training data as "outliers."

### F) Time Series Clustering
* **Metric:** i replaced standard Euclidean distance with **Soft-DTW (Dynamic Time Warping)** using the `tslearn` library.
* **Process:** i generated synthetic Random Walk data and clustered the series based on their shape and temporal alignment rather than just raw point-to-point distance.

### G) Document Clustering
* **Embeddings:** i used a pre-trained **BERT model** (`all-MiniLM-L6-v2`) via `sentence-transformers` to convert raw text sentences into dense 384-dimensional vectors.
* **Clustering:** i applied standard K-Means on these semantic vectors.
* **Dim-Reduction:** i used **PCA** to reduce the vectors to 2D for visualization.

### H) Image Clustering
* **Model:** i loaded OpenAI's **CLIP** model (`ViT-B/32`).
* **Processing:** i downloaded images from the ib, passed them through the CLIP vision encoder to get semantic embeddings, and normalized them.
* **Result:** i clustered these embeddings using K-Means, grouping images by concept (e.g., Space vs. Cats) rather than pixel color.

### I) Audio Clustering

* **Feature Extraction:** i used `librosa` to extract **MFCCs (Mel-Frequency Cepstral Coefficients)**, converting audio waves into numerical features representing timbre.
* **Clustering:** i grouped the audio files based on these acoustic features.