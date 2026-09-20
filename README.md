# QTrust-PPO

**QTrust-PPO: Confidence-Aware Finite-Shot Policy Optimization for Variational Quantum Reinforcement Learning**

This repository contains the executable notebooks, processed statistical
results, figures, and table data used to evaluate QTrust-PPO.

The complete run-level experimental archive, including evaluation episodes,
update traces, and intermediate outputs, is maintained separately as an
archival research dataset.

## Contents

- `notebooks/01_QTrust_PPO_Core_Benchmark.ipynb`  
  Primary three-environment benchmark, finite-shot baselines, QTrust-PPO, controlled clipping-boundary reliability analysis, seed-level statistics, and artifact generation.

- `notebooks/02_QTrust_PPO_Ablations_Robustness_and_Analysis.ipynb`  
  Confidence and rollback ablations, output-noise robustness, VQC depth analysis, confidence-bound comparison, consolidated statistics, and integrity checks.

- `statistics/`  
  Seed-level paired analyses, diagnostic summaries, confidence-bound comparisons, and the statistical protocol.

- `figures/`  
  Vector PDF and high-resolution PNG exports. The main set is accompanied by two additional diagnostic figures for resource decomposition and controlled boundary reliability.

- `tables/`  
  Processed CSV tables for performance, inference, resource, runtime, ablation, noise, depth, and confidence-bound summaries.

## Reference execution environment

The completed experiments used:

- Python 3.12.13
- PyTorch 2.10.0+cu128
- PennyLane 0.45.1
- PennyLane-Lightning-GPU 0.45.0
- Gymnasium 1.2.0
- SciPy 1.16.3
- Two NVIDIA Tesla T4 GPUs for quantum simulation

The notebooks retain the original Kaggle workspace paths and execution logic used for the completed runs.

## Execution order

1. Run `01_QTrust_PPO_Core_Benchmark.ipynb` to create and verify the primary benchmark outputs.
2. Run `02_QTrust_PPO_Ablations_Robustness_and_Analysis.ipynb` after the primary benchmark workspace is available.
3. Use the included CSV outputs for statistical verification without rerunning the full GPU workload.

The distributed notebooks are stored without execution output. Processed
figures, tables, and statistical summaries are included in this repository.

## Statistical unit

The independent training seed is the inferential unit for reinforcement-learning comparisons. The 30 evaluation episodes associated with each trained seed are repeated measurements and are not treated as independent replicates.

## QTrust confidence rule

For a finite schedule of `K` measurement stages, QTrust uses exact one-sided Clopper-Pearson limits with per-tail level `delta/(4K)`. The four tails correspond to lower and upper bounds for the old and candidate action probabilities. The resulting ratio interval is evaluated only against the PPO clipping boundary relevant to the sign of the advantage.

## Integrity

`SHA256_MANIFEST.csv` records checksums for every distributed file other than the manifest itself.
