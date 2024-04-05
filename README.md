# Julia
All code for this project is written in Julia v1.8.
The language can be downloaded [here](https://julialang.org/).

# Initialization

Before running any benchmarks, ensure that the package is instantiated.

` julia `

` using Pkg`

` Pkg.activate("examples") `

` Pkg.precompile() `

# Running the models

The following models are available: crpyt4, drone-4-1, drone-4-2, gridavoid4, gridavoid10, gridavoid20, nrp8, refuel06, refuel08, refuel20, rocks12

To run all the benchmarks, run the bash script

` ./benchmark.sh `

You can also run each model benchmark separately. For example, to run nrp8, run

` julia examples/run_nrp8.jl `

# Results

## Q1

|         | SARSOP              |                      |                      |                     |                    |                    | Ours                |
|---------|---------------------|----------------------|----------------------|---------------------|--------------------|--------------------|---------------------|
| Grid4   | [0.76, 0.76]  <1s   | [0.86, 0.86] <1s     | [0.92, 0.92] <1s     | [0.923, 0.923] <1s  | [0.928, 0.928] <1s | [0.928, 0.928] <1s | [0.928, 0.928] <1s  |
| Grid20  | [0.028, 0.049] -    | [0.155, 0.212] -     | [0.332, 0.38] -      | [0.709, 0.721] -    | [0.781, 0.782] <1s | [0, 1] -           | [0.782, 0.783] <33s |
| Refuel6 | [0.21, 0.21] <1s    | [0.32, 0.33] <1s     | [0.39, 0.39] 3.62s   | [0.63, 0.63] 200s   | [0.2, 0.98] -      | [0.18, 0.98] -     | [0.67, 0.67] 1.4s   |
| Refuel8 | [0.184, 0.184] 1.4s | [0.314, 0.314] 4.24s | [0.374, 0.375] 9.83s | [0.438, 0.439] 339s | [0.218, 0.987] -   | [0, 0.988] -       | [0.445, 0.445] 20s  |


## Q2/Q3

|                | PRISM                            | STORM                    | PAYNT       | SAYNT       | OURS                              | OVERAPP                  |
|----------------|----------------------------------|--------------------------|-------------|-------------|-----------------------------------|--------------------------|
| Grid-av 4-0.1  | [0.21, 1.0] <br> <1s, 15 beliefs      | 0.928 <br> 118s, 10M beliefs  | 0.928 <br> 158s  | 0.928 <br> 87.2s | [0.928, 0.928] <br> <1s, 194 beliefs   | 0.984 <br> 6.3s, 125K beliefs |
| Grid-av 10-0.3 | [0, 0.999] <br> 34s, 97 beliefs       | 0.513 <br> 75s, 5M beliefs    | 0.744 <br> 309s  | 0.773 <br> 337s  | [0.773, 0.774] <br> 8s, 8K beliefs     | 1.0 <br> <1s, 5K beliefs      |
| Grid-av 20-0.5 | TO/MO                            | 0.115 <br>77s, 5M beliefs    | 0.524 <br> 1156s | 0.667 <br> 1986s | [0.782, 0.783] <br> 33s, 12K beliefs   | 1.0 <br>  1.2s, 75K beliefs   |
| Drone 4-1      | TO/MO                            | 0.839 <br>210s, 6.5M beliefs | 0.869 <br> 2509s | 0.890 <br> 427s  | [0.884, 0.957] <br> -, 51K beliefs     | 0.942 <br> 1270s, 14M beliefs |
| Drone 4-2      | TO/MO                            | 0.953<br> 207s, 8.8M beliefs | 0.963 <br> 6815s | 0.971 <br> 733s  | [0.964, 0.976]  <br> -, 26K beliefs     | 0.974 <br> 44s, 762K beliefs  |
| Refuel6        | [0.67, 0.72] <br> 136s               | 0.67 <br>1.4s, 4.5K beliefs  | 0.67 <br> 77.8s  | 0.67 <br> 85s    | [0.67, 0.67] <br> 1.4s, 387 beliefs    | 0.69 <br> <1s, 48K beliefs    |
| Refuel8        | TO/MO                            | 0.439 <br>1.7s, 20K beliefs  | 0.445 <br> 494s  | 0.445 <br> 91s   | [0.445, 0.446] <br> 20s, 3.7K beliefs  | 0.509 <br> 410s, 11M beliefs  |
| Refuel20       | TO/MO                            | 0.144 <br>142s, 3.9M beliefs | 0.018 <br> 1666s | 0.204 <br> 937s  | [0.328, 0.999] <br> 1356s, 32K beliefs | 0.999 <br> 7.56s, 177K beliefs            |
| Crypt4         | [0.33, 0.77] <br> 33s, 312K beliefs   | 0.33 <br> <1s, 560 beliefs    | 0.33 <br> <1s    | 0.33 <br> <1s    | [0.33, 0.33] <br> 15.6s, 480 beliefs   | 0.33 <br> <1s, 560 beliefs    |
| Nrp8           | [0.125, 0.189]  <br>58s, 735K beliefs | 0.125 <br> <1s, 50 beliefs    | 0.125 <br> <1s   | 0.125 <br> <1s   | [0.125, 0.125] <br> <1s, 32 beliefs    | 0.125 <br> <1s, 50 beliefs    |
| Rocks12        | -                                | 0.63 <br> 1223s, 2M beliefs   | 0.75 <br> 5.7s   | 0.75 <br> 5.6s   | [0.75, 0.75] <br> 2.8s, 770 beliefs    | 0.75 <br> <1s, 2.5K beliefs   |

The results logs for each benchmark can be found in the original_results folder.

The results logs for each benchmark can be found in the original_results folder.

# Comparison algorithms

To reproduce results for SARSOP, run benchmark_sarsop.sh.

To reproduce results for STORM, PAYNT, SAYNT, and Overapp use the [toolbox artifact](https://doi.org/10.5281/zenodo.7874513) from the SAYNT paper. The experiment.py config is available in /original_results/config/experiments.py.

To reproduce the results for PRISM, use the [PRISM Model Checker](https://www.prismmodelchecker.org/download.php).
