# Autoencoder and Variational Autoencoder for Image Reconstruction

## Overview

This project implements an Autoencoder (AE) and a Variational Autoencoder (VAE) for image reconstruction and image generation using the MNIST handwritten digit dataset. It compares the models' reconstruction performance and demonstrates how a VAE can generate new digit-like images by sampling from its latent space.

## Objectives

- Implement and train a standard Autoencoder.
- Implement and train a Variational Autoencoder.
- Reconstruct handwritten digit images with both models.
- Generate new images using the VAE.
- Compare reconstruction performance using mean squared error (MSE) and visual inspection.

## Dataset

The project uses the MNIST handwritten digit dataset.

- Training set: 60,000 images
- Test set: 10,000 images
- Image dimensions: 28 × 28 pixels
- Image type: Grayscale
- Classes: Digits 0–9

The dataset is loaded automatically through TensorFlow. A separate manual download is not required when the runtime has internet access.

- Official dataset: https://yann.lecun.com/exdb/mnist/
- Kaggle dataset: https://www.kaggle.com/datasets/hojjatk/mnist-dataset

## Technologies

- Python
- TensorFlow and Keras
- NumPy
- Matplotlib

## Installation

Use Python 3.9 or newer. Install the required libraries:

```bash
pip install tensorflow numpy matplotlib
```

You can run the code in Jupyter Notebook or Google Colab. If using Colab, create a notebook and execute the implementation cells in sequence.

## Implementation

### 1. Data Preparation

The MNIST images are converted to floating-point values and normalized to the range [0, 1]. Each 28 × 28 image is flattened into a vector of 784 values for the fully connected networks used in this project.

### 2. Autoencoder

The Autoencoder consists of an encoder and a decoder.

- Encoder: Dense layers with 256 and 128 units, followed by a 32-dimensional latent representation.
- Decoder: Dense layers with 128 and 256 units, followed by a 784-unit sigmoid output layer.
- Optimizer: Adam.
- Reconstruction loss: Binary cross-entropy.

The model is trained to reconstruct each input image.

### 3. Variational Autoencoder

The VAE encoder estimates the mean and log-variance of a latent distribution. The reparameterization trick is used to sample a latent vector, which the decoder maps back to an image.

- Latent dimension: 32.
- Optimizer: Adam.
- Objective: Reconstruction loss plus KL-divergence loss.

The KL-divergence term regularizes the learned latent distribution toward a standard normal distribution, allowing the model to generate images by sampling latent vectors.

### 4. Evaluation and Generation

The project evaluates the models using the following methods:

- Visual comparison of original and reconstructed images.
- Test-set mean squared error (MSE).
- Training and validation loss plots for the Autoencoder.
- Total training-loss plot for the VAE.
- Generation of new images by sampling random vectors from a standard normal distribution and passing them through the VAE decoder.

## Running the Project

1. Install the dependencies.
2. Open the notebook in Jupyter Notebook or Google Colab.
3. Run the imports and dataset-loading code.
4. Build and train the Autoencoder.
5. Visualize its reconstructions.
6. Build and train the VAE.
7. Visualize VAE reconstructions and generate new images.
8. Calculate test-set MSE values and review the loss plots.
9. Record the actual metrics produced by your run.

## Results

The implementation produces:

- Original and Autoencoder-reconstructed image comparisons.
- Original and VAE-reconstructed image comparisons.
- A grid of newly generated VAE images.
- Test-set MSE values for both models.
- Training-loss visualizations.

Exact metric values and generated-image quality depend on training duration, model configuration, and runtime environment. Report the values obtained from your own run rather than assuming fixed results.

## Autoencoder vs. Variational Autoencoder

| Aspect | Autoencoder | Variational Autoencoder |
|---|---|---|
| Main purpose | Learn compact representations and reconstruct inputs | Reconstruct inputs and learn a sampleable latent distribution |
| Latent representation | Deterministic encoded vector | Distribution parameterized by mean and log-variance |
| Loss | Reconstruction loss | Reconstruction loss plus KL divergence |
| Image generation | Random sampling is not directly supported by the basic model | New samples can be generated from the latent space |
| Reconstruction appearance | Often preserves more input-specific detail | May produce smoother or blurrier images |

The model with the lower MSE has lower average squared pixel-level reconstruction error. MSE alone does not measure the quality or diversity of generated images, so visual inspection is also important.

## Project Structure

A suggested repository structure is:

```text
.
├── README.md
├── autoencoder_vae.ipynb
└── requirements.txt
```

Use the filenames that match the files you actually include in your repository.

## Troubleshooting

- **Dataset download fails:** Check the internet connection and run the dataset-loading cell again.
- **A library is missing:** Install the dependencies listed above.
- **Training is slow:** Reduce the number of epochs or use an available GPU runtime.
- **Generated images are unclear:** Try training for more epochs or adjusting the latent dimension and network architecture.

## Conclusion

This project demonstrates two approaches to learning image representations. The Autoencoder focuses on reconstructing its input, while the Variational Autoencoder adds latent-space regularization to support probabilistic sampling and image generation. Their reconstruction performance can be compared using test-set MSE and visual inspection.

## References

- MNIST Database of Handwritten Digits: https://yann.lecun.com/exdb/mnist/
- TensorFlow Documentation: https://www.tensorflow.org/
- Keras Documentation: https://keras.io/

---

Academic practical: No. 03 — Autoencoder and Variational Autoencoder for Image Reconstruction
