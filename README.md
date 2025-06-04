# Image Compression with Truncated Singular Value Decomposition (TSVD)

This project demonstrates an implementation of **Truncated Singular Value Decomposition (TSVD)** from scratch and its application to image compression. The method is evaluated on two different RGB images by analyzing storage requirements, reconstruction quality, and visual outcomes at various compression levels. 

Project is prepared for BLG202E- Numerical Methods for Computer Engineering course at ITU. Report is also added. 

Compressed images are given below: 
 
 *Image 1: https://kovan.itu.edu.tr/index.php/s/IWoE01nkDH8rSFa*

 *Image 2: https://kovan.itu.edu.tr/index.php/s/Hv1ApVkyIHLDLGb*

## Overview

Truncated SVD is a dimensionality reduction technique where only the top *k* singular values and corresponding vectors are retained from the full SVD decomposition of a matrix. This allows us to approximate and compress the image while maintaining a controllable level of quality loss.

The project applies TSVD individually to each color channel (R, G, B) of an image and reconstructs compressed versions for varying rank values:  
**r = 2, 4, 8, 16, 32, 64**

---

## Techniques

- **SVD Decomposition**:  
  Decomposes a matrix `A` into `UΣVᵀ`, where `U` and `V` are orthogonal matrices, and `Σ` is a diagonal matrix of singular values.

- **Truncated SVD**:  
  Retains only the top-*k* singular values and vectors to form a low-rank approximation:  
  `Aₖ = UₖΣₖVₖᵀ`

- **Power Iteration**:  
  Used to compute the largest eigenvalues and corresponding vectors efficiently as part of the custom TSVD implementation.

---

## Image Compression Pipeline

1. Split the image into RGB channels.
2. Apply TSVD to each channel separately.
3. Reconstruct the image using varying ranks.
4. Analyze visual quality, MSE (Mean Squared Error), and storage requirements.

---

## Results

- **Brueghel Image**:
  - Shows a **U-shaped** MSE curve — best quality/compression tradeoff around **rank 16**.
  - Compression tends to overfit or introduce noise beyond this rank.

- **Mandrill Image**:
  - MSE **increases monotonically** with rank.
  - Lower ranks capture essential features better due to high contrast and distinct color regions.

- **Storage Requirements**:
  - Remain consistent across images for the same rank.
  - Linear decrease in size with lower rank.

---

## Graphs and Visuals

- MSE vs. Rank plots
- Storage vs. Rank plots
- Side-by-side comparisons of original and compressed images

---

## Observations

- Visual quality does not always correlate with MSE.
- Brueghel's smooth color transitions require mid-rank approximations.
- Mandrill retains visual features even at very low ranks.

---

## File Structure

```plaintext
├── tsvd_compression.py      # Main script for custom TSVD and compression
├── images/                  # Original and compressed image outputs
├── results/                 # Plots and analysis outputs
├── README.md                # Project documentation
```

---

## Dependencies

- `numpy`
- `matplotlib`
- `PIL` or `opencv-python` for image handling

---

## References

1. Strang, Gilbert. *Introduction to Linear Algebra*, 5th ed.
2. [scikit-learn: TruncatedSVD](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.TruncatedSVD.html)
3. [matplotlib.pyplot.plot](https://matplotlib.org/stable/api/asgen/matplotlib.pyplot.plot.html)

