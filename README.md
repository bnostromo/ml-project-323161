# ml-project-323161


## Team Members


## 1. Introduction

PatternMind is a project focused on exploring the structure of visual concepts within a large
image collection. Instead of performing object classification, our goal is to analyze patterns in
the feature space, discover clusters, examine category relationships, and understand where
different visual groups overlap or diverge.
The dataset contains many labeled images from various categories (e.g., butterflies, rocks,
planes, etc.). We extract interpretable features (HOG + color histograms) and apply
dimensionality reduction and clustering methods to uncover the underlying organization of the
visual space.
The final goal is insight, not accuracy — understanding what themes emerge, how categories
relate, and where ambiguity exists.


## 2. Methods

2.1 Environment

Dependencies used:
numpy, pandas
scikit-image
scikit-learn
matplotlib, seaborn

2.2 Feature Extraction

The file PatternMind_Feature_Extraction.py performs the following steps:
Walks through all dataset subfolders (each folder = one label).
Reads images and resizes them to 128×128.
Converts all images to consistent 3-channel RGB.
Extracts:
HOG features (shape, texture)
Color histograms (24-dim)
Saves all features + labels into a single CSV file:
patternmind_features.csv
This creates a numerical feature representation that can be used for clustering and exploration.


2.3 Analysis Pipeline

The second script PatternMind_Analysis.py performs:
1. Exploratory Data Analysis (EDA)
Label distribution
Feature stats
Sample visualization
2. Preprocessing + PCA
Standardize features
Apply PCA (2 components) for visualization
Save PCA scatter plot
3. Clustering Algorithms
K-Means (tested across several k values)
Agglomerative Clustering (ward/average/complete)
Gaussian Mixture Models (GMM)
4. Evaluation Metrics
Silhouette Score
Davies–Bouldin Score
Adjusted Rand Index (ARI) (cluster vs label overlap)
Normalized Mutual Information (NMI)

2.4 System Flowchart (Simple Placeholder)

Raw Images → Preprocessing → HOG + Color Hist Extraction
                   ↓
          patternmind_features.csv
                   ↓
Scaling → PCA → Clustering → Interpretation 



## 3. Experimental Design
 
The main idea behind our experiments was to understand how the PatternMind images naturally group together once they are turned into numerical features. Since our goal is exploration rather than classification, we designed experiments that help reveal the structure of the visual space and how different categories relate to one another.

Approach-

We began by extracting HOG and color histogram features from all images and standardizing them. Before running any clustering, we applied PCA to reduce the feature space to two components. This gave us a simple visual baseline of how the dataset is organized without any algorithmic influence

Clustering Experiments-

We then tested several clustering algorithms, each chosen to give a different perspective on the structure of the data:

K-Means:
We experimented with multiple values of k to see how the dataset behaves when forced into different numbers of groups. This helped us understand whether the visual categories naturally form a certain number of clusters.

Agglomerative Clustering:
Using different linkage methods (ward, complete, average), we explored how the images merge into groups step-by-step. This method gave us insight into hierarchical relationships and which categories are closer or farther apart in feature space.

Gaussian Mixture Models (GMM):
Because not all images belong cleanly to a single category, we included GMM to allow for “soft” cluster assignments. This approach is useful when two categories have overlapping visual characteristics.

Evaluation Strategy-

To understand how well each method captured the dataset’s structure, we used several evaluation metrics:

Silhouette Score – measures how well images fit within their assigned cluster
Davies–Bouldin Score – indicates overall cluster quality
Adjusted Rand Index (ARI) – checks how closely clusters align with the original labels
Normalized Mutual Information (NMI) – measures shared information between labels and clusters

Together, these evaluations helped us compare models and understand the strengths and weaknesses of each clustering approach.

## 4. Results


## 5. Conclusions

PatternMind allowed us to explore how visual categories are structured in feature space. The
combination of HOG + color histograms, PCA visualization, and clustering algorithms showed
that some categories form distinct visual groups, while others blend together, revealing natural
ambiguity in the dataset.
The project highlighted that “understanding structure” is more meaningful here than
classification accuracy — we gained insight into patterns, visual similarity, and category
relationships.
