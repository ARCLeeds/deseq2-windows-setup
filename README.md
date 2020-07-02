# Installing DESeq2 with a conda R setup

We've had some users report difficulties installing the [DESeq2](https://bioconductor.org/packages/release/bioc/html/DESeq2.html) R library on Windows so i've put together this small repo containing some instructions of how i've successfully managed to get this working.

This setup requires [Anaconda](https://www.anaconda.com/products/individual) and installs DESeq2 version 1.26.0 and along with R 3.6.1 and RStudio plus associated dependencies.

## Workflow

To get started we need to create a new environment using the .yml file included in this repo. In the Anaconda Navigator:

```{bash}
# either navigate the the directory containing the .yml file in this repo and run:
conda env create -f environment.yml

# or create without the yml file with the line
conda create --name deseq2-env -c conda-forge r-base=3.6.1 rstudio r-foreign
```

This will install R 3.6.1, RStudio and the R package foreign and dependencies which should allow for the installation of DESeq2.

Next open R either via RStudio or via the R IDE and use the following commands summarised in the `install_deseq2.R` file:

```{r}
install.packages("BiocManager")

BiocManager::install("DESeq2")
# you may be prompted to update some installed packages. We recommend selecting S (for some).

# test the install has succeeded 
library(DESeq2)
```