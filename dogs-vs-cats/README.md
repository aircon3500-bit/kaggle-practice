# Dogs vs Cats

Image classification using EfficientNet-B3 and transfer learning.

## Results

| Version | Score (Log Loss) | Notes |
|---------|------------------|-------|
| V1 | 0.16418 | EfficientNet-B0, 3 epochs |
| V3 | 0.11243 | EfficientNet-B3, 300px, 10 epochs |

**Best Score: 0.11243** (31% improvement from baseline)

## Tech Stack

- PyTorch
- timm (EfficientNet-B3)
- Albumentations
- Kaggle Notebooks (GPU T4)

## What I Learned

- Transfer learning with pretrained models
- Image preprocessing and augmentation
- Learning rate scheduling (CosineAnnealing)
- Kaggle submission workflow
