# Image Reconstruction with pPCA and Autoencoders

This project was *completed as part of AIML232* at Te Herenga Waka — Victoria University of Wellington.

## Objective
Compress and reconstruct images using probabilistic PCA (pPCA), a linear autoencoder, and a ReLU autoencoder. Then analyse reconstruction quality and latent space representations.

## Data
- `X.npy` – Grayscale images of shape (34, 48).

Ensure this is in the working directory when running the notebooks.

## Structure 
- `X.npy` - Dataset used by both notebooks.
- `ppca.ipynb` - Full pPCA implementation with inline results.
- `autoencoders.ipynb` - Full Linear and ReLU autoencoder implementations with inline results.
- `requirements.txt` - Python dependencies.

## Methods
- **pPCA (Probabilistic PCA):**
  - Compresses images to *50 dimensions* using the EM algorithm. Handles missing values robustly and assumes a Gaussian latent space.

- **Linear Autoencoder:**
  - Fully connected linear layers compress images to *2 dimensions*. Captures only linear relationships.

- **ReLU Autoencoder:**
  - Fully connected layers with ReLU activation compress images to *2 dimensions*. Captures nonlinear patterns due to ReLU activation.
 
## Results

| Method           | Latent Dim | Final Reconstruction MSE | Latent Space Structure                 |
|-----------------|------------|-----------------|---------------------------------------|
| pPCA            | 50         | ≈ 276           | Oval (Gaussian, linear)               |
| Linear Autoencoder | 2        | ≈ 1744          | Linear line                             |
| ReLU Autoencoder  | 2        | ≈ 1114          | Curved, nonlinear       |

*Note: MSE for pPCA is from the EM algorithm; for autoencoders, it is the training reconstruction error.*

### Visualisations

**Latent Space**

- [pPCA latent space](principalComponents.png) – 2D scatterplot shows an oval shape consistent with Gaussian assumptions.  
- [Linear Autoencoder latent space](linearEncodedDimensions.png) – Linear structure in 2D.  
- [ReLU Autoencoder latent space](reluEncodedDimensions.png) – Curved, nonlinear structure.

**Reconstruction Examples**

- [pPCA reconstructions](pPCA_reconstructions.png)  
- [Linear Autoencoder reconstructions](linear_reconstructions.png)  
- [ReLU Autoencoder reconstructions](ReLU_reconstructions.png)

**Insights:**
- pPCA retains the most information due to its higher latent dimensionality (50D).  
- The linear autoencoder is limited to linear relationships, resulting in higher reconstruction loss.  
- The ReLU autoencoder captures nonlinear patterns in 2D, reducing loss compared to the linear autoencoder. 
- Reducing dimensionality to 2D significantly increases reconstruction error relative to 50D pPCA.

**Takeaways:**
- pPCA is effective for high-dimensional latent representation.
- ReLU autoencoders are better than linear for extreme 2D compression.
- Linear autoencoders are limited in capturing complex patterns.

## How to Run
Python version: 3.9+

```bash
pip install -r requirements.txt
jupyter notebook
# Open ppca.ipynb or autoencoders.ipynb
```

## Notes
- Results may vary slightly between runs due to random initialisation.
- Axis values in scatter plots may differ between runs, but overall latent space shapes remain consistent.
  
