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

## Example Question

```
{
    "problem": "Prove that $n \\sin(2n! e \\pi)$ converges to $2\\pi$ as $n \\to \\infty$.",
    "problem_type": "Sequences and Limits",
    "solution": "Let $r_n$ and $\\epsilon_n$ be the integral and fractional parts of the number $n! e$ respectively. Using the expansion\n$$\ne = 1 + \\frac{1}{1!} + \\frac{1}{2!} + \\frac{1}{3!} + \\cdots,\n$$\nwe have\n$$\n\\begin{cases}\nr_n = n! \\left( 1 + \\frac{1}{1!} + \\frac{1}{2!} + \\cdots + \\frac{1}{n!} \\right) \\\\\n\\epsilon_n = \\frac{1}{n+1} + \\frac{1}{(n+1)(n+2)} + \\cdots,\n\\end{cases}\n$$\nsince\n$$\n\\frac{1}{n+1} < \\epsilon_n < \\frac{1}{n+1} + \\frac{1}{(n+1)^2} + \\cdots = \\frac{1}{n}.\n$$\n\nThus $\\sin(2n! e \\pi) = \\sin(2\\pi \\epsilon_n)$. Note that this implies the irrationality of $e$.\n\nSince $n \\epsilon_n$ converges to $1$ as $n \\to \\infty$, we have\n$$\n\\lim_{n \\to \\infty} n \\sin(2\\pi \\epsilon_n) = \\lim_{n \\to \\infty} \\frac{\\sin(2\\pi \\epsilon_n)}{\\epsilon_n} = 2\\pi.\n$$\n\nHence $n \\sin(2n! e \\pi)$ converges to $2\\pi$ as $n \\to \\infty$."
}
```


## Repository Structure

The repository contains both the full dataset and a divided version for distinct pretraining and benchmark sets.

```
DEMI-MathAnalysis   
├─ divided
│ ├─ pretraining
│ │ └─ ... (files for pretraining split) 
│ ├─ benchmark
│ │ └─ ... (files for benchmark split) 
│ ├─ pretraining_data.csv 
│ └─ benchmark_data.csv 
├─ all 
│ └─ ... (complete dataset files in a single directory) 
├─ all.csv 
├─ all.xlsx 
└─ README.md
```

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
@book{demidovich1964problems,
    title={Problems in Mathematical Analysis. Edited by B. Demidovich. Translated From the Russian by G. Yankovsky},
    author={Demidovich, B.P.},
    series={Russian Monographs and Texts on Advanced Mathematics and Physics},
    url={https://books.google.com/books?id=XdmpwgEACAAJ},
    year={1964},
    publisher = {Mir Publishers}  
}

@book{hata2007problems,
  title={Problems and Solutions in Real Analysis},
  author={Hata, M.},
  isbn={9789812776013},
  lccn={2008295629},
  series={Series on number theory and its applications},
  url={https://books.google.com/books?id=vSxkRgQe0AcC},
  year={2007},
  publisher={World Scientific}
}
```
