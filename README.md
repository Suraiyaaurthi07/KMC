##🎨 K-Means Color Quantization (KMC)

A machine learning project that applies K-Means Clustering to perform image color quantization — reducing the number of distinct colors in an image while preserving its visual structure.

## 📌 What is Color Quantization?

Color quantization is the process of reducing the number of colors used in an image.
Instead of storing thousands of unique RGB values, the image is represented using only
**K representative colors** (cluster centroids). This is useful for:

- Image compression
- Reducing memory usage
- Artistic stylization of images
- Palette-based rendering

🧠 Algorithm Overview

This project uses the K-Means Clustering algorithm applied to the RGB pixel values of an image.

How it works, step by step:

```
Input Image
     │
     ▼
Flatten pixels → shape: (H×W, 3)  ← each pixel becomes an (R, G, B) point
     │
     ▼
StandardScaler → normalize RGB values
     │
     ▼
Elbow Method → find optimal K (number of color clusters)
     │
     ▼
KMeans(K=8) → cluster pixels into 8 color groups
     │
     ▼
Replace each pixel with its cluster's centroid color
     │
     ▼
Quantized Output Image
```


    

Key Steps Explained:

| Step | Description |
|------|-------------|
| **Pixel Extraction** | Each pixel's `(R, G, B)` is reshaped into `(num_pixels, 3)` |
| **Scaling** | `StandardScaler` normalizes RGB so no channel dominates distance |
| **Elbow Method** | WCSS plotted for K=1–10 to find the optimal cluster count |
| **K-Means Fitting** | `KMeans(K=8)` trained on `kodim03.png` |
| **Quantization** | Each pixel replaced by its nearest centroid color |
| **Visualization** | Side-by-side comparison + 3D RGB scatter plot |

📂 Repository Structure

```
KMC/
├── 220152(KMC).ipynb       # Main Colab notebook with full pipeline
├── kodim03.png             # Training image (used to learn color clusters)
├── custom_img.jpeg         # Custom image to apply quantization on
├── color_quantizer.pkl     # Saved KMeans model
├── scaler.pkl              # Saved StandardScaler
├── screenshots/
│   ├── elbow method.png    # Elbow curve plot
│   └── 3D plot.png         # 3D RGB cluster scatter plot
└── README.md
```



![Elbow Curve](https://github.com/Suraiyaaurthi07/KMC/blob/323f3a072181f433ff3775e73456b51f3af0f231/screenshots/elbow%20method.png)
![Scatter Plot](https://github.com/Suraiyaaurthi07/KMC/blob/323f3a072181f433ff3775e73456b51f3af0f231/screenshots/3D%20plot.png)


Cluster Description:


**Cluster 0:** Contains observations with similar characteristics that differentiate them from the other groups. The data points within this cluster show a strong level of similarity and form a well-defined segment.

**Cluster 1:** Represents observations with balanced or average feature values. This cluster serves as the central group within the dataset and reflects common patterns among the data points.

**Cluster 2:** Includes observations with characteristics that are distinct from Clusters 0 and 1. The data points in this group share similar feature patterns, forming a separate and identifiable segment.



## 🛠️ Technologies Used

- Python 3
- Google Colab — runtime environment
- `Pillow (PIL)` — image loading and display
- `NumPy` — pixel array manipulation
- `Matplotlib` — plotting (2D and 3D)
- `scikit-learn` — `KMeans`, `StandardScaler`
- `joblib` — saving and loading trained models
- `pandas` — tabular display of cluster assignments


## 🎓 Key Concepts

- **K-Means Clustering:** An unsupervised algorithm that partitions data into K groups by minimizing intra-cluster variance.
- **WCSS (Inertia):** Sum of squared distances from each point to its cluster centroid — lower is better.
- **Elbow Method:** A heuristic to choose K by finding where WCSS reduction flattens out.
- **Color Quantization:** Replacing millions of pixel colors with a fixed palette of K colors.
