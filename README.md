# Approximate Inference in Graphical Models using Neural Networks

## Overview

This repository implements and compares three methods for approximating marginal probabilities in binary Markov Random Fields (MRFs):

1. **GraphTransformerGNN**

   - A graph neural network with dynamic edge updates and transformer-style attention.
   - Learns message-passing to predict node marginals.

2. **MLP Baseline**

   - A structure-agnostic multilayer perceptron that vectorizes the graph.
   - Trained to regress marginals from node biases and edge weights.

3. **Gibbs Sampling**

   - Classical MCMC approach (5,000 iterations with 1,000 burn-in).
   - Provides a near-exact inference reference.

## Repository Structure
```
.
├── data/                # Optional synthetic data scripts
├── outputs/             # Generated plots and figures
│   ├── inference_comparison.png
│   ├── gnn_loss.png
│   └── mlp_loss.png
├── notebooks/           # Jupyter notebooks
│   └── ggmtermprojectv2.ipynb
├── src/                 # Source code modules
│   ├── data_generation.py
│   ├── models.py
│   ├── train.py
│   └── utils.py
├── references.bib       # BibTeX references
├── literature_review.tex # LaTeX literature review section
├── results_discussion.tex # LaTeX results & discussion section
├── README.md            # Project README (this file)
└── requirements.txt     # Python dependencies
```

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/Salil8/Approximate-Inference-in-Graphical-Models-using-Neural-Networks.git
   cd Approximate-Inference-in-Graphical-Models-using-Neural-Networks
   ```
2. Create and activate a virtual environment, then install dependencies:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   pip install -r requirements.txt
   ```

## Usage

### Notebook

Open and run the Jupyter notebook to reproduce experiments and plots:

```bash
jupyter notebook notebooks/ggmtermprojectv2.ipynb
```

### Command-Line

Train and evaluate models via the script:

```bash
python src/train.py \
  --num-nodes 10 \
  --edge-prob 0.5 \
  --num-train 500 \
  --num-test 100 \
  --epochs-gnn 100 \
  --epochs-mlp 200 \
  --output-dir outputs/
```

## Results

- **GraphTransformerGNN Test MSE:** 0.0341
- **Gibbs Sampling Test MSE:** 0.0098 (≈48× slower)
- **MLP Baseline Test MSE:** 0.0706



## Citation

If you use this work, please cite:

```bibtex
@inproceedings{yoon2018gnn,
  author    = {Yoon, Hyunjik and Schwing, Alexander G.},
  title     = {Learning to Infer and Execute 3D Shape Programs},
  booktitle = {ICML},
  year      = {2018},
}

@article{zammit2024amortized,
  author  = {Zammit‐Mangion, Andrew and Prangle, David and Hu, Teng},
  title   = {Neural Amortized Inference for Simulation‐Based Models},
  journal = {Journal of Computational and Graphical Statistics},
  year    = {2024},
}
```


