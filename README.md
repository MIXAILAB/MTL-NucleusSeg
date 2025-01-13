# MTL-NucleusSeg
Revolutionizing multi-organ nucleus segmentation in histopathological images with a cutting-edge multi-task learning framework to effectively handle challenges like dense nuclei packing, overlapping structures, and staining variability.

This repository contains the implementation of a novel multi-organ nucleus segmentation framework

## Key Features
### 1. Pre-Processing for Standardization and Variability Reduction

This stage ensures consistent quality across histopathological datasets by addressing staining intensity variations and preparing reliable training data.

**Reference Selection:** Criteria to identify representative reference images for style transfer.

**Style Transfer:** Harmonization of visual characteristics across datasets.

**Label Crafting:** Preparation of high-quality training data to enhance model reliability.

### 2. Proposed Model Architecture
The framework employs a multi-task learning model with an encoder-decoder structure, integrating advanced techniques for effective segmentation Multi-Dilated Residual Block with Bottleneck Transformer:
Multi-dilated convolutions capture features at varying scales, improving segmentation in dense and overlapping regions. Bottleneck Transformer ensures long-range dependency modeling. Attention Gate Mechanisms: Focuses on relevant regions of interest, enhancing segmentation accuracy.

### Dual Output Heads:
**Distance Map (D ∈ RH×W):** Encodes spatial relationships to separate densely packed nuclei.

**Semantic Segmentation Map (S ∈ RH×W):** Classifies pixels as nucleus or background.

### 3. Augmentation for Generalization
To improve robustness and mitigate domain shifts:

### Reference-based style transfer standardizes staining.
Augmentation techniques like rotation and flipping increase dataset variability and diversity.

## Results

The proposed framework achieves state-of-the-art performance on several multi-organ segmentation benchmarks, including the MoNuSeg dataset, with:

**Average Jaccard Index (AJI): 0.77**



## Repository Structure

- **preprocessing/**  
  Contains scripts for reference selection, style transfer, and data augmentation.

- **training.ipynb**  
  Jupyter Notebook for training the multi-task learning model.

- **test.ipynb**  
  Jupyter Notebook for testing the multi-task learning model.

- **Saved_model/**  
  Pretrained models for both the NuInsSeg and MoNuSeg datasets.

- **evaluation/**  
  Scripts for calculating evaluation metrics such as Dice, IoU, AJI, and PQ.

- **datasets/**  
  Scripts for dataset preparation and implementing 5-fold cross-validation.

---

## Installation

Clone the repository:  
```bash
git clone https://github.com/eyob12/MTL-NucleusSeg.git  
cd MTL-NucleusSeg

Install dependencies:
```bash
pip install -r requirements.txt

# Usage

### Data Preprocessing
Use the provided scripts to apply style transfer and augmentations:

```bash
python preprocess.py --input_dir <path-to-dataset> --output_dir <path-to-output>

### Train the Model
Start training with:

```bash
python train.py --config config.yaml

### Evaluate the Model
Evaluate on test datasets with:

```bash
python evaluate.py --weights <path-to-weights>
