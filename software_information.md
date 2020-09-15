# Software

## Software RNA-seq pipeline uses for data processing

### Ubuntu 16.04

The pipeline docker image is based on [Ubuntu base image](https://hub.docker.com/_/ubuntu/) version `16.04`.

### Python 3.5.2

Python parts of the pipeline are run using [Python 3.5.2](https://www.python.org/download/releases/3.5.2/).

### R 3.2.3

MAD QC is run using R version 3.2.3 (2015-12-10) -- "Wooden Christmas-Tree".

### STAR 2.5.1b

Alignment is done using [STAR 2.5.1b](https://github.com/alexdobin/STAR/releases/tag/2.5.1b). For detailed description of the software see [Article by Dobin et al](https://www.ncbi.nlm.nih.gov/pubmed/23104886). Multiple versions of the software have been released since writing the article.

### RSEM 1.2.31

Quantification is done using [RSEM v1.2.31](https://github.com/deweylab/RSEM/releases/tag/v1.2.31). For detailed description of the software see [Article by Bo Li and Colin N Dewey](https://bmcbioinformatics.biomedcentral.com/articles/10.1186/1471-2105-12-323). Multiple versions of the software have been released since writing the article.

### Kallisto 0.44.0

Additional quantification is calculated using [Kallisto v0.44.0](https://github.com/pachterlab/kallisto/releases/tag/v0.44.0). For detailed description of the software see [Article by Bray et al.](https://www.nature.com/articles/nbt.3519).

### Samtools 1.9

Samtools flagstats are calculated using [Samtools 1.9](https://github.com/samtools/samtools/releases/tag/1.9). For original publication describing the software, see [Article by Li H et al](https://www.ncbi.nlm.nih.gov/pubmed/19505943). Multiple versions of the software have been released since writing the article.

### bedGraphToBigWig and bedSort

[bedGraphToBigWig kent source version 371](http://hgdownload.soe.ucsc.edu/admin/exe/linux.x86_64/bedGraphToBigWig) and [bedSort](http://hgdownload.soe.ucsc.edu/admin/exe/linux.x86_64/bedSort) (no version information available) are used in signal track generation. Source code is downloadable [here](http://hgdownload.soe.ucsc.edu/admin/exe/userApps.v371.src.tgz).

## Software we are using to run the RNA-seq pipeline

### Cromwell

Scientific workflow engine [Cromwell](https://github.com/broadinstitute/cromwell) is used execute workflows written in WDL. Behind the scenes Cromwell takes care of spinning up machines that process the data, and moving the needed data between storage and machines.

### Caper

Tool developed by [Jin Lee](https://github.com/leepc12) at ENCODE-DCC. [Caper](https://github.com/ENCODE-DCC/caper) provides a simple interface to Cromwell, and takes care of most of the configuration for you.

### Croo
Tool developed by [Jin Lee](https://github.com/leepc12) at ENCODE-DCC. [Croo](https://github.com/ENCODE-DCC/croo) simplifies Cromwell output directory structure, and makes it easy to look at the pipeline outputs, and visualize the results. 
