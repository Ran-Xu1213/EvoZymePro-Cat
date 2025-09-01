
# EvoZymePro-Cat
Protein-Ligand-Aware Deep Learning for Precision Enzyme Engineering
# EvoZymePro-Cat (EZPro-Cat)

**Protein-Ligand-Aware Deep Learning for Precision Enzyme Engineering**

## Overview

EvoZymePro-Cat is a deep learning framework designed for accurate prediction of enzyme mutant performance through comparative analysis. Unlike traditional methods that predict absolute activity values, our approach uses pairwise comparison to identify superior enzyme variants, eliminating systematic bias and providing actionable rankings for directed evolution.

## Key Features

- **Multimodal Integration**: Combines protein sequence, local structural context, and ligand information
- **Bilinear Attention Mechanism**: Captures complex protein-ligand interactions during catalysis
- **Comparative Prediction**: Ranks mutant superiority rather than predicting absolute values
- **Few-shot Learning**: Achieves high performance with limited training data (AUC: 0.908)
- **Cross-enzyme Generalization**: Works across diverse enzyme families (EC1-EC6)

## Architecture Components

### Protein Representation
- **Sequence Encoding**: ESM1b transformer model (1280-dimensional embeddings)
- **Local Structure**: k-NN graphs around mutation sites processed by Graph Convolutional Networks
- **Evolutionary Context**: Position-Specific Scoring Matrix (PSSM) integration

### Ligand Representation
- **Molecular Language Models**: MolT5 embeddings for semantic representation
- **Chemical Fingerprints**: MACCS keys for structural patterns
- **Dual Encoding**: Balances semantic understanding with concrete chemical properties

### Feature Fusion
- **BANLayer**: Bilinear attention network for protein-ligand interaction modeling
- **Cross-modal Integration**: Weighted fusion of multimodal features
- **Attention Maps**: Interpretable interaction visualization


## Requirements

- Python 3.8+
- PyTorch
- PyTorch Geometric
- transformers (for ESM models)
- RDKit (for molecular descriptors)
- BioPython
- NumPy, Pandas, Scikit-learn

## Installation

```bash
git clone https://github.com/your-repo/evozymepro-cat
cd evozymepro-cat
pip install -r requirements.txt
```

## Data Format

### Input Requirements
- **Protein sequences**: FASTA format with mutation annotations
- **Ligand information**: SMILES strings or molecular descriptors
- **Activity data**: Comparative labels (0/1) or continuous values
- **Structure files**: PDB format (optional, AlphaFold structures used by default)

### Dataset Organization
```
data/
├── sequences/
│   ├── wild_type.fasta
│   └── mutants.fasta
├── ligands/
│   └── substrates.smi
├── activities/
│   └── comparative_labels.csv
└── structures/
    └── alphafold_pdbs/
```

## Model Components

1. **Protein Encoder**: ESM1b-based sequence representation
2. **Structure Encoder**: GCN for local microenvironment analysis  
3. **Ligand Encoder**: MolT5 + MACCS fingerprint fusion
4. **Attention Module**: Bilinear attention for cross-modal interaction
5. **Classifier**: MLP for binary comparative prediction

## Applications

- **Directed Evolution**: Prioritize beneficial mutations for experimental validation
- **Enzyme Engineering**: Design improved biocatalysts for industrial applications
- **Protein Design**: Rational mutation selection based on structure-function relationships
- **Drug Discovery**: Optimize enzyme-inhibitor interactions

## Citation

If you use EvoZymePro-Cat in your research, please cite:

```bibtex
@article{xu2025evozymepro,
  title={EvoZymePro-Cat: Protein-Ligand-Aware Deep Learning for Precision Enzyme Engineering},
  author={Xu, Ran and Li, Xinkang and Sui, Jianan and Zheng, Liangzhen and Guo, Jingjing},
  journal={Journal Name},
  year={2024}
}
```


