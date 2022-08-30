---
source: md
title: "Data annotation"
---

# Data annotation 

## Installation of the needed environment in the cluste (Duke University)

I have already installed `Conda` with the `miniconda` version inside the cluster in the next directory:

~~~
$ /hpc/group/bio1/diego/miniconda3
~~~
{: .language-bash}

Then, it is needed to add the channels where most of the biological-usage packages are located. Otherwise, at the moment we 
try to search for some packages we will obtain that the search got no results:

~~~
$ conda config --add channels conda-forge
$ conda config --add channels bioconda
~~~
{: .language-bash}


We can procced to install [`mamba`](https://mamba.readthedocs.io/en/latest/user_guide/mamba.html), a tool that will help me to 
get compatible dependencies for each of the packages that I am going to install.

~~~
$ conda install -c conda-forge mamba
~~~
{: .language-bash}

This set up will allow me to make a new environment where I will install `Prokka` and `Antismash`, I will call this 
environment `gmining` from genome mining:

~~~

~~~
{: .language-bash}

~~~

~~~
{: .language-bash}

~~~

~~~
{: .language-bash}

## Prokka annotation

By taking a random bin of hte ones that Carlos share with me, I was able to annotate them using `Prokka`. There was a problem using 
the deafult behaviour of this problem. The `.gbk` file that was generated merged the contig name and the contig lenght. That 
generates a error in the parsing process in programs as `antismash`. I foun that you can use the `--compliant` flag to 
make the locus layout comply to the NCBI expected layout. The next line is an example with one of the bins:

~~~
$ prokka --prefix P2039_bin.23 --outdir P2039_bin.23 --kingdom Bacteria --genus Nostoc \
--strain P2039_bin.23 --usegenus --addgenes --metagenome --compliant --cpus 12 carlos-bins/P2039_bin.23.fa
~~~
{: .language-bash}


## Antismash annotation

Having this correct annotation, we can now take the next step and use `Antismash` to annotate the secondary metabolism of the bins 
provided.

~~~
$ antismash --minimal P2039_bin.23/P2039_bin.23.gbk --output-dir P2039_bin-antis
~~~
{: .language-bash}



~~~

~~~
{: .language-bash}
