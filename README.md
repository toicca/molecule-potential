This is a project done during my time at Aalto University as a research assistant. The aim of the project is to produce the electrostatic potential of a molecule from the molecules electron densities calculated with coupled clusters method.

All C/C++ code (electron density part) in this repository was developed by Dr. Filippo Leonida Federici Canova of Nanolayers Ltd. He also created the initial Python library part. My contribution can be seen as functions in the Python library qmtools.py and as code developed in Fortran.



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
