# Dominant Feature Masking (DFM)

**Artem Pilzak & Jean-Philippe Thivierge**
*University of Ottawa, ComBiNe Lab*
📄 [Official Publication in Pattern Analysis and Applications (2025)]([https://doi.org/10.1007/s10044-025-01474-1])

---

## Overview

Dominant Feature Masking (DFM) is a novel data augmentation technique designed to improve **out-of-distribution (OOD) generalization** in convolutional neural networks (CNNs). Inspired by holistic processing in human vision, DFM suppresses the **most salient features** in an image—identified through Grad-CAM—and compels the network to rely on **secondary, complementary cues**. This encourages broader feature utilization, improving robustness when facing unfamiliar test distributions.

This repository contains:

* The full implementation of DFM
* The **Versatile Evaluation Benchmark (VEB)**: A comprehensive test suite for OOD generalization on three structured datasets

---

## Key Contributions

* ✅ **DFM: A Simple Yet Effective OOD Augmentation**
  Suppresses dominant visual features in training samples to prevent fixated learning, enabling better feature diversity.

* ✅ **VEB Benchmark**
  Includes three custom-designed evaluation tracks:

  1. **Transformed MNIST** – tests robustness to corruptions (crop, rotation, noise)
  2. **Fruits & Veggies (Intra-class Novelty)** – unseen objects within known classes
  3. **Cats vs. Dogs (Adversarial Confusion)** – synthetic DALL·E images with mixed class features

* ✅ **No Label Modification**
  Unlike MixUp, CutMix, or RICAP, DFM retains original labels to preserve strong associations with secondary features.

* ✅ **Interpretable Feature Suppression**
  Visualizes masked regions using Grad-CAM, avoiding black-box behavior common in other feature suppression methods.

---

## Repository Structure

```
DFM/
├── dfm_core/                # DFM implementation & Grad-CAM masking
├── veb_datasets/            # Processed MNIST, Fruits/Veggies, Cats/Dogs
├── experiments/             # Training and evaluation scripts
├── models/                  # Custom CNN and ResNet-50 training configurations
├── utils/                   # Helper scripts: plotting, masking, evaluation
├── results/                 # Evaluation results and figures
└── README.md                # This file
```

---

## Requirements

* Python 3.10+
* TensorFlow 2.10+
* OpenCV, NumPy, Matplotlib
* (Optional) CUDA-compatible GPU

---

## Getting Started

```bash
git clone https://github.com/DeepVisionary/DFM.git
cd DFM
pip install -r requirements.txt
```

To run a DFM training on the Fruits & Veggies dataset:

```bash
python experiments/train_dfm_fruits.py --alpha 0.6
```

---

## Citation

If you use DFM or VEB in your research, please cite:

```bibtex
@article{pilzak2024dfm,
  title={Enhancing Out-of-Distribution Learning in Computer Vision through Dominant Feature Masking},
  author={Pilzak, Artem and Thivierge, Jean-Philippe},
  journal={Pattern Analysis and Applications},
  year={2024},
  publisher={Springer}
}
```

---

## License

MIT License — see `LICENSE` file for details.


