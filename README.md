# mmtf-pyspark-benchmarks

Benchmarks mmtf-pyspark methods as function of the number of logical cores.

## Local Installation

[Install Anaconda](https://www.anaconda.com/download)

#### Open a terminal window

#### Clone this repository

```git clone https://github.com/sbl-sdsc/mmtf-pyspark-benchmarks.git```

#### Create a conda environment

```cd mmtf-pyspark-benchmarks```

```conda env create -f environment.yml```

#### Activate the conda environment

```conda activate benchmark```

#### Launch Jupyter Notebook

```jupyter notebook```

#### After you are finished, deactivate the conda environment

```conda deactivate```

Anytime you want to use the environment, activate it again and start Jupyter Notebook

#### To permanently remove the benchmark environment

```conda remove --name benchmark --all```


## Run Benchmarks

The benchmarks compare:
1. Reading the whole PDB from a Hadoop Sequence File (baseline benchmark)
2. Finding Zinc interactions in the PDB comparing two methods, one that uses loops and Python data structures and one that uses Numpy vectorized array methods.

The benchmarks are run on 1, 2, 3, 4xn (n = 1, maxcores/4). maxcores is the maximum number of logical cores on a machine. The number of physical cores may be less if hyperthreading is enabled.

1. [DownloadFiles.ipynb](notebooks/DownloadFiles.ipynb) (download PDB Hadoop Sequence file and setup directories)
2. [BenchmarkRead.ipynb](notebooks/BenchmarkRead.ipynb) (read PDB Hadoop Sequence file)
3. [BenchmarkInteractionsVec.ipynb](notebooks/BenchmarkInteractionsVec.ipynb) (find Zinc interactions using a Numpy vectorized array implementation)
4. [BenchmarkInteractions.ipynb](notebooks/BenchmarkInteractions.ipynb) (find Zinc interactions using a Python implementation)
5. [PlotResults.ipynb](notebooks/PlotResults.ipynb) (plot results)
