# Image Reconstruction with pPCA and Autoencoders

This project was *completed as part of AIML232* at Te Herenga Waka — Victoria University of Wellington.

## Objective
Compress and reconstruct images using probabilistic PCA (pPCA), a linear autoencoder, and a ReLU autoencoder. Then analyse reconstruction quality and latent space structure.

## Data
- `X.npy` – Grayscale images of shape (34, 48).
Ensure this is in the working directory when running the notebooks.

## Methods
- **pPCA (Probabilistic PCA):**
  - Compresses images to 50 dimensions using the EM algorithm. Handles missing values robustly and assumes a Gaussian latent space.

- **Linear Autoencoder:**
  - Fully connected linear layers compress images to 2 dimensions. Captures only linear relationships.

- **ReLU Autoencoder:**
  - Fully connected layers with ReLU activation compress images to 2 dimensions. Captures nonlinear patterns due to ReLU activation.
 
## Results

| Method           | Latent Dim | Final Loss / MSE | Latent Space Structure                 |
|-----------------|------------|-----------------|---------------------------------------|
| pPCA            | 50         | ≈ 276           | Oval (Gaussian, linear)               |
| Linear Autoencoder | 2        | ≈ 1744          | Linear line                             |
| ReLU Autoencoder  | 2        | ≈ 1114          | Curved, nonlinear       |

**Insights:**
- pPCA retains the most information due to higher latent dimensionality (50D).  
- The linear autoencoder is limited to linear relationships, resulting in higher reconstruction loss.  
- The ReLU autoencoder captures nonlinear patterns in 2D, reducing loss compared to the linear autoencoder. 
- Extreme dimensionality reduction (to 2D) increases reconstruction error relative to higher-dimensional methods.

## Visualisations

### Latent Space
- [pPCA latent space](principalComponents.png) – 2D scatterplot shows an oval shape consistent with Gaussian assumptions.  
- [Linear Autoencoder latent space](linearEncodedDimensions.png) – Linear structure in 2D.  
- [ReLU Autoencoder latent space](reluEncodedDimensions.png) – Curved, nonlinear structure.

### Reconstruction Examples
- [pPCA reconstructions](pPCA_reconstructions.png)  
- [Linear Autoencoder reconstructions](Linear_reconstructions.png)  
- [ReLU Autoencoder reconstructions](ReLU_reconstructions.png)

## How to Run

  
