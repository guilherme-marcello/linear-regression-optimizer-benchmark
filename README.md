# Benchmark Results: Optimization Algorithms for Linear Regression

This repository contains the raw execution data from a comparative study on various optimization algorithms applied to multi-dimensional linear least-squares regression. The experiments were conducted as part of the analysis presented in the paper.

## Overview

The goal of this study was to empirically evaluate the performance, convergence speed, and trade-offs of the following optimization methods:

* **Analytical Solution**
* **Steepest Descent (SD)**
* **Stochastic Gradient Descent (SGD)**
* **Newton's Method (NM)**
* **Limited-memory BFGS (L-BFGS)**

These algorithms were tested on two distinct datasets to assess their performance in different scenarios:
1.  **ICVL Hand Tracking Dataset**: A high-dimensional regression problem ($n=2048$ features, $m=63$ targets).
2.  **Student Habits and Performance Dataset**: A low-dimensional regression problem ($n=7$ features, $m=2$ targets).

All experiments were executed on a machine with an Apple M1 processor and 16GB of memory.

## Execution Results

The complete, raw results from all experimental runs are available in the `results.json` file in this repository.

### Data Structure

The `results.json` file contains a list of two primary objects, one for each dataset. Each object has the following structure:

```json
{
    "dataset_info": {
        "dataset_name": "Name of the dataset",
        "n_features": Integer,
        "n_targets": Integer,
        "n_train_samples": Integer,
        "n_test_samples": Integer
    },
    "optimizer_results": [
        {
            "optimizer_name": "Algorithm+Initialization (e.g., 'L-BFGS+zeros')",
            "test_mse": Float,
            "total_optimization_time_s": Float,
            "num_iterations_run": Integer,
            "W_final_norm": Float,
            "iterations_data": [
                {
                    "iter": Integer,
                    "objective": Float,
                    "time_s": Float,
                    "memory_rss_bytes": Integer,
                    "step_size": Float
                },
                ...
            ]
        },
        ...
    ]
}
