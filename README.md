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

#### Download MMTF Hadoop Sequence File
Download the entire PDB as an [MMTF Hadoop Sequence File](http://mmtf.rcsb.org/download.html)

```curl -O https://mmtf.rcsb.org/v1.0/hadoopfiles/full.tar```

```tar -xvf full.tar```

Then set the MMTF_FULL environment variable

```export MMTF_FULL=<path>/full```

#### Set Spark Options 
When running PySpark on many cores, it may run out of memory on the Spark Driver (default 1GB). If necessary, set the environmental variable in the .bashrc (Linux) or .bash_profile (Mac) file.


```export SPARK_DRIVER_MEMORY=16G```

## Run Benchmarks

The benchmarks compare:
1. Reading the whole PDB from an MMTF Hadoop Sequence File (baseline benchmark)
2. Tabulating zinc interactions in the PDB 
3. Tabulating salt-bridge interactions in the PDB 

To run the benchmark, set the number of cores in cell 3 of RunBenchmarks.ipynb, e.g. on 24 cores: 

```
cores = [24, 20, 16, 12, 8, 4, 2, 1]
```

The benchmarks are typically run on 1, 2, 4xn (n = 1, maxcores/4). maxcores is the maximum number of logical cores on a machine. The number of physical cores may be less if hyperthreading is enabled.

1. [PrintSettings.ipynb](notebooks/PrintSettings.ipynb) (prints Spark settings, e.g., SPARK_DRIVER_MEMORY)
2. [RunBenchmarks.ipynb](notebooks/RunBenchmarks.ipynb) (runs all benchmarks)
4. [PlotReadResults.ipynb](notebooks/PlotReadResults.ipynb) (plots benchmark results for reading MMTF Hadoop Sequence Files)
5. [PlotCalculation.ipynb](notebooks/PlotCalculationResults.ipynb) (plots benchmark results for performing calculations using MMTF Hadoop Sequence Files)
