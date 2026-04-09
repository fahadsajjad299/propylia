# PROPYLIA 🔬

> A comprehensive Python-based toolkit for computing protein sequence descriptors

![Python](https://img.shields.io/badge/Python-3.7%2B-blue?style=flat-square&logo=python)
![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)

---

## Overview

**PROPYLIA** is an offline, standalone bioinformatics toolkit designed for researchers working with protein sequences. It provides a rich set of sequence-based descriptors that are widely used in machine learning models for protein classification, structure prediction, and functional annotation — all without requiring an internet connection.

---

## Features

| Descriptor | Description | Output Size |
|---|---|---|
| Amino Acid Composition (AAC) | Relative frequency of each of the 20 standard amino acids | 20 features |
| Dipeptide Composition (DPC) | Frequency of all possible dipeptide pairs | 400 features |
| Tripeptide Composition (TPC) | Frequency of all possible tripeptide combinations | 8,000 features |
| Pseudo Amino Acid Composition (PAAC) | Extends AAC with sequence-order autocorrelation | Variable |
| Amphiphilic PAAC (APAAC) | Captures hydrophobicity and hydrophilicity patterns | Variable |
| CTD | Composition, Transition & Distribution of 7 physicochemical properties | 147 features |
| Autocorrelation (Moran's I) | Captures periodic trends and sequence-order effects | Variable |
| Molecular Weight | Total molecular weight of the protein sequence | 1 feature |

---

## Descriptor Details

### 1. Amino Acid Composition (AAC)
Calculates the relative frequency of each of the 20 standard amino acids in a protein sequence. Widely used as a baseline feature in protein classification and structure prediction tasks.

### 2. Dipeptide Composition (DPC)
Computes the frequency of all 400 possible dipeptides (pairs of two consecutive amino acids). Captures local sequence order and short-range interactions between residues.

### 3. Tripeptide Composition (TPC)
Extends dipeptide analysis to triplets, generating 8,000 features. Provides highly detailed local sequence descriptors useful for fine-grained classification.

### 4. Pseudo Amino Acid Composition (PAAC)
An extension of AAC that incorporates sequence-order information via autocorrelation of physicochemical properties (e.g., hydrophobicity, hydrophilicity, side-chain mass). Reduces information loss compared to plain AAC.

### 5. Amphiphilic Pseudo Amino Acid Composition (APAAC)
A variant of PAAC focused on capturing hydrophobic and hydrophilic distribution patterns along the sequence. Particularly useful for membrane protein analysis and amphipathic helix detection.

### 6. CTD — Composition, Transition & Distribution
Analyzes 7 key physicochemical properties of a protein sequence. Generates 147 diverse features reflecting how these properties are distributed and transition across the sequence. Commonly used in subcellular localization and functional site prediction.

### 7. Autocorrelation (Moran's I Index)
Computes Moran's autocorrelation coefficient along the sequence based on physicochemical properties. Effective at capturing periodic trends, repeating motifs, and long-range sequence-order effects.

### 8. Molecular Weight
Calculates the total molecular weight of a protein from its amino acid sequence using standard residue masses. A fundamental feature for protein characterization and filtering.

---

## Requirements

```
Python 3.7 or higher
numpy
pandas
```

Install dependencies with:

```bash
pip install numpy pandas
```

---

## Installation

```bash
# Clone the repository
git clone https://github.com/your-username/PROPYLIA.git

# Navigate into the folder
cd PROPYLIA

# Install dependencies
pip install -r requirements.txt
```

---

## Usage

```bash
# Run the tool on a FASTA file
python propylia.py --input your_sequences.fasta --descriptor AAC

# Run all descriptors at once
python propylia.py --input your_sequences.fasta --descriptor ALL

# Save output to a CSV file
python propylia.py --input your_sequences.fasta --descriptor DPC --output results.csv
```

---

## Input Format

PROPYLIA accepts standard **FASTA format** files:

```
>Protein_1
MKTAYIAKQRQISFVKSHFSRQLEERLGLIEVQAPILSRVGDGTQDNLSGAEKAVQVKVKALPDAQFEVVHSLAKWKRQTLGQHDFSAGEGLYTHMKALRPDEDRLSPLHSVYVDQWDWERVMGDGERQFSTLKSTVEAIWAGIKATEAAVSEEFGLAPFLPDQIHFVHSQELLSRYPDLDAKGRERAIAKDLGAVFLVGIGGKLSDGHRHDVRAPDYDDWSTPSELGHAGLNGDILVWNPVLEDAFELSSMGIRVDADTLKHQLALTGDEDRLELEWHQALLRGEMPQTIGGGIGQSRLTMLLLQLPHIGQVQAGVWPAAVRESVPSLL
```

---

## Output

Results are saved as a `.csv` file where each row corresponds to a protein and each column corresponds to a computed feature.

| Protein_ID | A | C | D | ... | Feature_N |
|---|---|---|---|---|---|
| Protein_1 | 0.042 | 0.018 | 0.031 | ... | 0.009 |

---

## Citation

If you use PROPYLIA in your research, please cite:

```
Author(s) (2025). PROPYLIA: A Python toolkit for protein sequence descriptor computation.
GitHub. https://github.com/your-username/PROPYLIA
```

---

## Author

**Fahad Sajjad**

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## Acknowledgements

Descriptor formulations are based on established methods in the bioinformatics literature, including those implemented in tools such as iFeature and Propy3.
