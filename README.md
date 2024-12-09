# DEMI-MathAnalysis Dataset

The **DEMI-MathAnalysis** dataset is a curated collection of proof-oriented mathematical analysis problems designed to train and benchmark Large Language Models (LLMs). Unlike many mathematical datasets that focus on computational exercises, DEMI-MathAnalysis emphasizes rigorous reasoning, formal definitions, and step-by-step proofs. It serves as a critical resource for advancing LLM capabilities in formal mathematical reasoning and bridging gaps previously left unexplored in AI-driven mathematics.

## Overview

Mathematical analysis requires precise formulations, definitions, and proofs. This dataset addresses the need for rigor in AI-driven mathematics by providing problems sourced from authoritative real analysis texts, focusing on:

- **Sequences and Limits**
- **Infinite Series**
- **Continuous Functions**
- **Differentiation**
- **Integration and Improper Integrals**
- **Series of Functions**
- **Approximation by Polynomials**
- **Convex Functions**

By training on DEMI-MathAnalysis, LLMs can move beyond heuristic approximations and learn to produce logically complete, formally justified solutions.

## Repository Structure

The repository contains both the full dataset and a divided version for distinct pretraining and benchmark sets.


### Key Files and Directories

- **`all/`**: Contains the complete dataset without any split, providing a single source of all problems.
- **`all.csv` and `all.xlsx`**: Consolidated files containing the entire dataset. These may include metadata such as problem statements, solutions, and classification labels.
- **`divided/`**:  
  - **`pretraining/`**: Directory holding files used to train LLMs. Problems here are intended for model fine-tuning and do not overlap with the testing material.  
  - **`benchmark/`**: Directory containing files reserved for evaluation. By using these problems as a benchmark, you can assess the generalization and rigor of LLM solutions without risking overfitting.
  - **`pretraining_data.csv`**: A CSV file listing the training subset of the dataset.  
  - **`benchmark_data.csv`**: A CSV file listing the benchmark subset of the dataset.

## Dataset Format

Each entry in the CSV or XLSX files typically includes:
- **Problem Statement**: A proof-oriented problem from mathematical analysis.
- **Topic/Classification**: The field of analysis (e.g., Sequences, Infinite Series) the problem belongs to.
- **Metadata**: Additional information such as difficulty level, source references, and problem ID.
  
The benchmark and pretraining splits are curated to ensure that the testing problems differ in nature or topic range from training problems, allowing for more robust and reliable evaluation of an LLM’s true reasoning capabilities.

## How to Use the Dataset

1. **Pretraining**:  
   Use `pretraining_data.csv` (or files in `divided/pretraining/`) to fine-tune an LLM. This step helps the model learn reasoning patterns, definitions, and proof structures characteristic of real analysis problems.

2. **Benchmarking**:  
   After fine-tuning, test the model on `benchmark_data.csv` (or files in `divided/benchmark/`) to evaluate how well it has learned to reason rigorously. Scores obtained on these problems provide insights into the model’s ability to generalize and produce logically coherent proofs.

3. **Full Dataset Exploration**:  
   For research that does not require separate training and benchmark sets, the complete dataset in `all/`, `all.csv`, or `all.xlsx` may be used. This is useful for exploratory analysis, dataset augmentation, or creating custom training/validation/test splits.

## License

This dataset is released under the [MIT License](LICENSE), allowing for both academic and commercial use. Users are encouraged to cite the dataset’s source if it contributes to their research or publications.

## Citation

If you find DEMI-MathAnalysis useful in your research, please consider citing our work:

```bibtex
@misc{yourwork2024demimathanalysis,
  title={DEMI-MathAnalysis: A Dataset for Rigorous Proof-Based Reasoning in Mathematical Analysis},
  author={Your Name and Collaborators},
  year={2024},
  howpublished={\url{https://github.com/yourusername/DEMI-MathAnalysis}}
}
