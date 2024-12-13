# Image Compression using SVD - Assignment

## Overview
This project demonstrates image compression using Singular Value Decomposition (SVD) on the ORL face dataset. The goal is to reconstruct images using a reduced set of singular values and compare the image quality and storage space required for different compression levels.

### Key Tasks:
1. **Load and Preprocess Data**: Load face images from a zipped dataset and preprocess them for compression.
2. **Apply SVD for Image Compression**: Use SVD to decompose the images and reconstruct them using different numbers of singular values.
3. **Evaluate Compression**: Visualize the original and compressed images for different compression levels and analyze storage space savings.
4. **Face Recognition**: Use principal components from PCA (via SVD) to match test images with the training set.

## Dataset
The dataset used in this assignment is the **ORL face database**. It contains 40 subjects, each with 10 images under different conditions (lighting, expressions, etc.).

The dataset can be found [here](https://www.cam-orl.co.uk/facedatabase.html).

### Dataset Structure:
- Images are of size 92x112 pixels.
- Images are stored in PGM format.
- Each subject has 10 images (stored in folders `s1`, `s2`, ..., `s40`).

## Steps Taken
### 1. **Data Preprocessing**:
   - The face images are loaded from the zipped dataset.
   - The images are reshaped into 1D vectors and stored in a matrix where each column corresponds to an image.

### 2. **Singular Value Decomposition (SVD)**:
   - SVD is performed on the matrix to decompose the images into three components: \( U \), \( \Sigma \), and \( V^T \).
   - Various numbers of singular values (from 1 to 92) are used to reconstruct the image.

### 3. **Compression and Visualization**:
   - For each \( k \) (number of singular values), the image is reconstructed and visualized.
   - The storage space used by each compressed image is calculated and compared to the original.

### 4. **Face Recognition**:
   - The test images are vectorized and centered.
   - Their projections onto the principal components are computed and compared to the training set to find the most similar face.

## Key Observations:
- The larger the number of singular values used, the better the image reconstruction. However, more singular values require more storage.
- The largest singular values capture the major features of the image (broad shapes, facial features), while the smallest singular values capture finer details and noise.
- Compression with fewer singular values results in significant storage savings but sacrifices image quality.

## Results:
For each compression level, the following were calculated:
- Image quality for different values of \( k \).
- Storage space used relative to the original image.

Example output:


## Files Included:
- `attface.zip`: The dataset of face images.
- `image_compression_svd.py`: Python script that implements the compression process, including SVD, image reconstruction, and face recognition.
- `README.md`: This file.

## Requirements:
- Python 3.x
- Libraries: `numpy`, `matplotlib`, `opencv`, `zipfile`

## How to Run:
1. **Download and unzip the dataset** (`attface.zip`) and place it in the same directory as the script.
2. **Run the script**: 
    ```bash
    python image_compression_svd.py
    ```
3. **Visualize the results**: The script will display the original and compressed images for each level of compression and print the storage savings.

## Conclusion:
This assignment demonstrates how SVD can be used for image compression, showing how the number of singular values affects both image quality and storage requirements. By using only the largest singular values, significant storage savings can be achieved without a major loss in image quality.

## References:
- Olivetti Research Laboratory (ORL) Face Database: [Link](https://www.cam-orl.co.uk/facedatabase.html)
- Singular Value Decomposition: [Link](https://en.wikipedia.org/wiki/Singular_value_decomposition)

