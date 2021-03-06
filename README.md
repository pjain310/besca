# BESCA (BEDA's Single Cell Analysis library)

The BESCA (BEDA’s single cell sequencing analysis) package contains many useful python functions to use for your single-cell analysis.

The package has been grouped into 3 categories:  

- preprocessing functions: this submodule contains all functions relevant to data preprocessing  
- plotting functions: additional plot types not available in the standard scanpy package  
- tools: contains additional tools to e.g. perform differential gene analysis or load/export data  

For more information please view the package documentation: https://bedapub.github.io/besca/

Please find our preprint posted on bioRxiv here: https://biorxiv.org/cgi/content/short/2020.08.11.245795v2

If you are interested in contributing you can check the repository wiki for helpful information on contributing: https://github.com/bedapub/besca/wiki

## Installation

If you are familiar with python packages simply install them using pip:  

```
pip install git+https://github.com/bedapub/besca.git
```

Besca comes with a binary called reformat written in C and was compiled in linux-64. Therefore, besca runs exclusively on linux-64.


### Set the executable flag to the binary file `reformat` <a name="binary"></a>

In some cases, the binary file needs to be made executable. To do so, run the following one-liner.

```bash
pip show besca | grep Location | cut -f 2 -d ":" | awk -v OFS="" '{print "chmod u+x" $0 "/besca/export/reformat"}' | bash
```

If you want to avoid piping to bash, or want to it step by step, here is how to. Show the location of the path and navigate to the besca package.  

```
pip show besca
cd Location/besca
```

Navigate in the directory containing the binary and make it executeable.  

```
cd export
chmod u+x reformat
```

### Python beginner guide

If you are not very familiar with python packages here is a detailed description.  

If you don't have a conda python installation download and install [miniconda](https://docs.conda.io/en/latest/miniconda.html). While installing we recommend accepting everything asked by the miniconda installation.  

As a next step, we create a separate environment for besca which is also called besca.  

```
conda create --name besca python=3.7.1
```  

We can activate this environment.  

```
conda activate besca
```

Within this environment, we can install besca using pip.  

```
pip install git+https://github.com/bedapub/besca.git
```

Now following the [instruction above](#binary) to set the executable flag to the binary file shipped with besca.

You should now have successfully installed besca.

In case you met any problems, please report an issue.


### R dependencies for additional methods

Although the standard workflow can be run without any R dependencies, BESCA can run a selection of performant methods developed in R. These additional methods are: 

- `isOutlier` from `scatter`: for outlier detection and filtering recommendations (coming soon). 
- `SCTransform`: one of the normalization methods proposed by the `Seurat` package (coming soon).
- `maxLikGlobalDimEst` from `intrinsicDimension`: for the estimation of the number of dimensions to use for clustering (coming soon).
- `deviance` and `VST`: for highly-variable genes selection (coming soon).
- `DSB`: for denoising ADT count data based on background noise. 

If you want to run one of these methods in the workflow, please install the required libraries by running the following command in the `besca` directory :

```
pip install rpy2
Rscript Rlibs.R your_R_library_path
 ```

## Running besca on an HPC with a SLURM workload manager  

If you have access to an HPC which uses SLURM as a workload manager you can run the jupyter notebooks coming with besca located in `workbooks/` with dedicated resources.  
To do so, start an interactive session on your HPC.  

```
interactive -c 8 -m 16G -t 180 # This allocates 8 CPUs, 16 GB of memory for 3 hours
```

If you have installed besca in a conda environment like explained above activate the environment.  

```
conda activate besca
```

Start a jupyter notebook.  

```
jupyter-notebook --ip=* --no-browser
```

You can now run the jupyter notebooks coming with besca.



## Datasets and Analysis notebooks


Besca run-examples and datasets annotation notebooks can be found in:


[https://github.com/bedapub/besca_publication_results](https://github.com/bedapub/besca_publication_results)


All processed datasets were uploaded to Zenodo, within the Besca community:

[https://zenodo.org/communities/besca/](https://zenodo.org/communities/besca/)






