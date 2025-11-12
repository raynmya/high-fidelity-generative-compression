# Installation Guide
This repo is a version bump for [high-fidelity-generative-compression](https://github.com/Justin-Tan/high-fidelity-generative-compression) repo to support the latest CUDA and PyTorch (as well as ARM64 architecture), and has been tested on DGX Spark. Here is a detailed installation guide.

Version overview:
 - Python: 3.12
 - CUDA: 12.8
 - PyTorch: 2.9.0

## 1. Conda environment setup
```bash
conda create --name hific python=3.12
conda activate hific
```

## 2. Install CUDA Toolkit
```bash
conda install cuda-toolkit
```

To check it's version:
```bash
nvcc --version
```

```
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2025 NVIDIA Corporation
Built on Fri_Feb_21_20:26:18_PST_2025
Cuda compilation tools, release 12.8, V12.8.93
Build cuda_12.8.r12.8/compiler.35583870_0
```

## 3. Install the CUDA corresponding PyTorch
Visit the [PyTorch](https://pytorch.org/get-started/locally/) website and find the correct installation command for your CUDA version. For example:
```bash
pip3 install torch torchvision --index-url https://download.pytorch.org/whl/cu128
```

## 4. Install other dependency
```bash
pip install autograd pandas tables scipy scikit-image tqdm
```

## 5. Download pretrained models
- [HIFIC-low](https://drive.google.com/open?id=1hfFTkZbs_VOBmXQ-M4bYEPejrD76lAY9)
- [HIFIC-med](https://drive.google.com/open?id=1QNoX0AGKTBkthMJGPfQI0dT0_tnysYUb)
- [HIFIC-high](https://drive.google.com/open?id=1BFYpvhVIA_Ek2QsHBbKnaBE8wn1GhFyA)

## 6. Test environment
Run the following command to verify your environment:
```bash
python -m src.model
```
Or
```bash
python compress.py \
  --ckpt_path ./models/hific_hi.pt \
  --image_dir ./assets/originals \
  --output_dir ./assets/test_out \
  --metrics
```
