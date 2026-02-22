# Deep Learning Cheatsheet

## Architectures

| Architecture | Best For | Key Idea |
|-------------|----------|----------|
| MLP | Tabular data | Fully connected layers |
| CNN | Images, spatial data | Convolutional filters detect local patterns |
| RNN / LSTM | Sequences (old approach) | Hidden state carries temporal info |
| Transformer | Text, sequences, everything | Self-attention, parallel processing |
| ResNet | Deep image models | Skip connections solve vanishing gradients |
| U-Net | Image segmentation | Encoder-decoder with skip connections |
| GAN | Image generation | Generator vs discriminator adversarial training |
| VAE | Generation + latent space | Encode to distribution, decode back |
| Diffusion | Image generation (SOTA) | Iterative denoising process |

## Activation Functions

| Function | Formula | Use Case |
|----------|---------|----------|
| ReLU | max(0, x) | Default for hidden layers |
| LeakyReLU | max(0.01x, x) | Avoids dead neurons |
| GELU | x * CDF(x) | Transformers (smooth ReLU) |
| Sigmoid | 1/(1+e^-x) | Binary output, gates |
| Tanh | (e^x - e^-x)/(e^x + e^-x) | Output in [-1, 1] |
| Softmax | e^xi / sum(e^xj) | Multi-class output |
| SiLU/Swish | x * sigmoid(x) | Modern architectures |

## Loss Functions

| Loss | Use Case |
|------|----------|
| MSE | Regression |
| Cross-Entropy | Classification |
| Binary Cross-Entropy | Binary classification |
| Focal Loss | Imbalanced classification |
| Huber Loss | Regression (robust to outliers) |
| Contrastive Loss | Similarity learning |
| Triplet Loss | Face recognition, embeddings |

## Optimizers

| Optimizer | When to use |
|-----------|-------------|
| SGD + Momentum | Computer vision, well-tuned models |
| Adam | Default choice, works well most of the time |
| AdamW | Default for Transformers |
| LAMB | Large batch training |

## Regularization Techniques

- **Dropout**: Randomly zero activations (p=0.1-0.5)
- **Weight Decay**: L2 penalty on weights (AdamW)
- **Batch Normalization**: Normalize activations per mini-batch
- **Layer Normalization**: Normalize per sample (Transformers)
- **Data Augmentation**: Random crops, flips, color jitter
- **Label Smoothing**: Soften one-hot labels (0.9 instead of 1.0)
- **Early Stopping**: Monitor validation loss
- **Gradient Clipping**: Prevent exploding gradients

## Learning Rate Schedules

| Schedule | Description |
|----------|-------------|
| Constant | Fixed LR throughout |
| Step Decay | Reduce by factor every N epochs |
| Cosine Annealing | Smooth decay following cosine curve |
| Warmup + Decay | Linear warmup then cosine/linear decay |
| OneCycleLR | Increase then decrease (super-convergence) |
| ReduceLROnPlateau | Reduce when metric stops improving |

## Common Hyperparameters

| Parameter | Typical Range |
|-----------|---------------|
| Learning rate | 1e-5 to 1e-2 |
| Batch size | 16, 32, 64, 128, 256 |
| Hidden dim | 64, 128, 256, 512, 1024 |
| Dropout | 0.1 to 0.5 |
| Weight decay | 1e-4 to 1e-1 |
| Epochs | 10 to 300 (with early stopping) |
