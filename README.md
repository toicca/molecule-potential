# Description

This is a project done during my time at Aalto University as a research assistant in the group Surfaces and Interfaces at the Nanoscale (SIN). The aim of the project is to produce the electrostatic potential of a molecule from the molecules electron densities calculated with coupled clusters method.

All C/C++ code (electron density part) in this repository was developed by Dr. Filippo Leonida Federici Canova of Nanolayers Ltd. He also created the initial Python library part. My contribution can be seen as functions in the Python library qmtools.py and as code developed in Fortran. A serial implementation of these calculations was also done by Niko Oinonen of Aalto University's SIN group, these are the files poisson.py and poisson_extend.py. There are also various files for testing the library, but these should be ignored.

This repository is meant to be a showcase of work rather than something that can be taken and ran on a home computer. The installation and execution steps below are for Aalto University's HPC environment. The reader should thus look mostly at files qmtools.py, example.py, lib/ftypes.cuf and lib/potential.cuf.

A bachelors thesis was also developed from this project. The thesis can be read from the file bsc_thesis_nicotoikka.pdf, but it is rather extensive with some information quite loosely related to this project. Still, it should provide all the needed background information for this project and show my understanding of the topic.

# Installation

```
module load anaconda3 gcc cuda
module use /share/apps/spack/envs/fgci-centos7-haswell-dev/lmod/linux-centos7-x86_64/all
module load nvhpc/21.5
cd lib
make
```


# Execution

get an interactive session:

```
sinteractive -t 10 --gres=gpu:v100:1 --mem-per-cpu=2000
module load anaconda3 gcc cuda
module use /share/apps/spack/envs/fgci-centos7-haswell-dev/lmod/linux-centos7-x86_64/all
module load nvhpc/21.5

python test.py
```
