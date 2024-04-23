# Seq2Phase

LLPS-related protein predictor from amino acid sequence


## Description

![Image](image.jpg)
### About Seq2Phase
- **Purpose**: Predicts LLPS client proteins from amino acid sequences.
- **Unique Focus**: Concentrates on client proteins in LLPS, which are proteins localizing in condensates but not essential for their formation.
- **Technology**: Utilizes large language model (LLM) embeddings and a range of machine learning (ML) models (SVM, RF, HGBC, NN).
- **Application**: Capable of proteome-wide analysis.
- **Utility**: Aids in identifying client protein candidates for deeper biological research.
- **Broad Applicability**: Effective across multiple species including humans, mice, yeast, and Arabidopsis thaliana.
- **Limitations**:
  - Not tested in prokaryotes.
  - Computations can be slow when run only on a CPU. For CPU usage, the `--less_data` option is recommended.

### About Liquid-Liquid Phase Separation (LLPS)
- **Function**: Facilitates intracellular compartmentalization without biological membranes.
- **Process**: Forms membraneless organelles like nucleoli and p-bodies.
- **Components**: Involves two types of proteins - scaffolds and clients.
  - **Scaffolds**: Essential for condensate formation.
  - **Clients**: Localize within condensates, performing various roles but not required for condensate formation.
- **Relevance**: Linked to cellular processes and various diseases, including neurodegenerative disorders.


## Installation

First install pixi, then let the configuration file handle the rest.

```
# installing on unix based systems, windows not supported
curl -fsSL https://pixi.sh/install.sh | bash
pixi install
pixi run build_train
```


## Usage

Run [`train_model.py`](https://github.com/IwasakiLab/Seq2Phase/blob/main/train_model.py) first, then [`seq2phase.py`](https://github.com/IwasakiLab/Seq2Phase/blob/main/seq2phase.py).
```bash
python train_model.py
python seq2phase.py -i input.fasta -o output.tsv
```

### Training the Model (`train_model.py`)
- **Initial Setup**: Run `train_model.py` once before using `seq2phase.py`. Once executed, `seq2phase.py` can be used multiple times.
- **For CPU Environments**: Using the `--less_data` option is recomended.

### Running Predictions (`seq2phase.py`)
- **Input**: The script takes an input file in FASTA format.
- **Output**: Generates an output file containing client and scaffold scores.
    - **Interpreting Scores**: If both scores of a protein are high (>0.5), it is considered a scaffold protein.

## How to cite Seq2Phase

Kazuki Miyata, Wataru Iwasaki, Seq2Phase: Language Model-based Accurate Prediction of Client Proteins in Liquid-Liquid Phase Separation, Bioinformatics Advances, 2023;, vbad189.

https://doi.org/10.1093/bioadv/vbad189

## Contact

Kazuki Miyata (The University of Tokyo) miyatakazuki381@g.ecc.u-tokyo.ac.jp
