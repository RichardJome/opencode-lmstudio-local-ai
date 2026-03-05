---
name: deep-learning-setup
description: Set up deep learning environment with PyTorch, TensorFlow, CUDA
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: ml-setup
---

## What I do

- Set up PyTorch with CUDA support
- Configure TensorFlow GPU
- Verify GPU availability
- Install necessary libraries

## When to use me

Use this when setting up a new deep learning environment or troubleshooting GPU issues.

## Quick Commands

```bash
# Check CUDA
nvidia-smi

# PyTorch GPU test
python -c "import torch; print(torch.cuda.is_available())"

# Install PyTorch
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121

# TensorFlow
pip install tensorflow
```
