# Optimizing K in K-means: A Visual and Quantitative Exploration  

This project explores the application of **K-means clustering** for **color compression in images** and **high-dimensional synthetic data**, demonstrating how to determine the optimal number of clusters (*k*) using both visual and quantitative evaluation methods. The goal is to understand how K-means groups similar data points, assess clustering performance, and apply these techniques to real-world scenarios where visual validation is not possible.  

## **Project Overview**  

The project aims to:  

- **Demonstrate K-means Clustering**: Apply K-means to perform **color compression** on a photograph of tulips, visualizing RGB distributions in 3D space.  
- **Evaluate Optimal Cluster Count**: Use **inertia** (within-cluster sum of squares) and **silhouette scores** to determine the best *k* for synthetic data.  
- **Compare Visual vs. Quantitative Methods**: Highlight how clustering evaluation shifts from intuitive inspection to metric-driven analysis as data dimensionality increases.  
- **Support Real-World Applications**: Showcase K-means’ utility in fields like **computer vision, customer segmentation, and anomaly detection**.  

## **Dataset Structure**  

### **Tulip Image Dataset**  
- **Shape**: (320, 240, 3) — 76,800 pixels, each with **Red (R), Green (G), Blue (B)** values (0–255).  
- **Preprocessing**: Reshaped into a 76,800 × 3 matrix for clustering, where each row is a pixel and columns are R, G, B intensities.  

### **Synthetic Dataset**  
- **Samples**: 1,000  
- **Features**: 6 continuous variables, standardized (mean=0, std=1).  
- **Clusters**: Randomly generated (3–6 hidden clusters) using `make_blobs`.  

## **Methodology & Key Steps**  

### **1. Color Compression with K-means**  
- **Reshaped Image Data**: Converted the tulip photo into a pixel-RGB matrix for clustering.  
- **3D Visualization**: Plotted RGB values in 3D space to observe color distribution and cluster behavior.  
- **Iterative Clustering**: Applied K-means with *k* ranging from 2 to 10, replacing pixel colors with centroid values.  
- **Visual Evaluation**: Compared compressed images to assess how cluster count affects quality.  

### **2. Quantitative Evaluation for High-Dimensional Data**  
- **Data Scaling**: Standardized synthetic data using `StandardScaler` to ensure fair distance calculations.  
- **Inertia Analysis**: Plotted the "elbow curve" to identify the point of diminishing returns in variance reduction.  
- **Silhouette Scores**: Measured cluster cohesion and separation, with higher scores (closer to 1) indicating better-defined clusters.  
- **Validation**: Confirmed optimal *k* against ground truth labels (hidden synthetic clusters).  

### **3. Model Interpretation & Deployment**  
- **Centroid Analysis**: Examined RGB centroids for image compression and feature means for synthetic data.  
- **Predictions on New Data**: Demonstrated how to assign new observations to clusters and calculate centroid distances.  
- **Downstream Applications**: Discussed using cluster labels and distances as features in supervised learning.  

## **Key Insights**  

### **Visual Clustering (Image Data)**  
- **K-means Effectively Reduces Colors**: Even with *k=3*, the compressed image retained essential structures (red tulips, green stems).  
- **Limitations with Non-Globular Data**: Elongated color gradients in RGB space highlighted K-means’ bias toward spherical clusters.  

### **Quantitative Clustering (Synthetic Data)**  
- **Inertia vs. Silhouette**: Inertia decreased monotonically with higher *k*, while silhouette scores peaked at *k=5*—aligning with the true cluster count.  
- **Scaled Data is Critical**: Unscaled features skewed distance metrics, emphasizing the need for standardization.  

### **Practical Takeaways**  
- **Trade-offs in Choosing *k***: Higher *k* improves granularity but risks overfitting; metrics like silhouette scores help balance this.  
- **Beyond K-means**: For non-globular clusters, algorithms like DBSCAN or GMMs may outperform K-means.  

## **Project Highlights**  
- **Dual Approach**: Combined visual intuition (image compression) with mathematical rigor (synthetic data).  
- **Reproducible Pipeline**: Standardized data → fit K-means → evaluate metrics → validate → predict.  
- **Real-World Readiness**: Demonstrated clustering for both exploration (images) and production (new data assignments).  

## **Future Work**  
- **Algorithm Comparisons**: Test DBSCAN or hierarchical clustering on non-globular data.  
- **Dimensionality Reduction**: Use PCA/t-SNE to visualize high-dimensional clusters.  
- **Supervised Integration**: Incorporate cluster labels as features in classification tasks.  
- **Anomaly Detection**: Leverage centroid distances to identify outliers in new data.  

This project bridges **theoretical clustering concepts** and **practical implementation**, offering a template for optimizing K-means in diverse applications—from art to analytics.  
