# OPUS-Design: A 3D Convolutional Approach for Protein Sequence Design Targeting Complex Spatial Microenvironments

Complex three-dimensional (3D) protein environments, including monomers, oligomers, and ligand-bound small-molecule complexes, form a canonical class of biological systems. Protein sequence design based on backbone structure, commonly referred to as protein inverse folding, is central to modeling these intricate systems, as it seeks to uncover the intrinsic link between 3D structural topology and target amino acid sequences within complex spatial microenvironments. State-of-the-art methods for this task are dominated by graph-based models such as ProteinMPNN and ESM-IF, which deliver strong performance. However, 3D convolutional neural networks (3DCNNs) offer a promising alternative. These networks feature inherent rotation invariance and excel at capturing dense local spatial contexts in complex protein microenvironments, yet their full potential for protein inverse folding remains underexplored. Here, we introduce ***OPUS-Design, a two-stage 3DCNN-based framework for protein sequence design***. Tested on CASP15 and CAMEO targets spanning monomers, oligomers, and ligand-bound complexes, OPUS-Design matches or outperforms top graph-based methods in sequence recovery. These findings validate the efficacy of 3DCNN for protein inverse folding and suggest its potential for broader applications in related structural prediction tasks.

<img src="./images/figure.png" width="50%" height="50%"/>

## Usage

### Dependencies

```
Python 3.7
TensorFlow 2.4
ESM-2 (install via `pip install esm`; see [facebookresearch/esm](https://github.com/facebookresearch/esm) for details)
```

### Step-by-Step Instructions

#### 1. Generate Backbone-Only PDB Structure
Run `to_bb.py` to produce a PDB file containing only backbone coordinates.  
- Retain backbone atoms from protein chains.  
- Keep all atoms from ligands.

#### 2. Mask Residue Types to "UNK"
Run `to_unk.py` to set all residue type information in the PDB file to "UNK".  
- This step prevents data leakage by removing residue identity information.

#### 3. Run OPUS-Design Prediction
Execute `run_opus_design.py` to generate the final results.  
- Outputs are saved in the `predictions` folder.  
- `*_tmp.fasta`: intermediate results from the first stage (3DCNN feature extraction only).  
- `*.fasta`: final results after both 3DCNN feature extraction and feature aggregation modules.

### Download

- **Standalone version**: The OPUS-Design standalone package, including model weights, can be downloaded [Here](xxx).  
- **Test datasets**: Preprocessed datasets (CAMEO, CAMEO-oligomer, CASP15, and PXM‑2025) are available [Here](https://github.com/thuxugang/opus_design/blob/main/testset.zip).

## Reference

