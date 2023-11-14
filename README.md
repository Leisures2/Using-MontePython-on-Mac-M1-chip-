# Using MontePython on Mac M1 chip
The total process of installing and using MontePython prepared for me to prevent forgetting.
The problems which are produced by `plc` are still not solved...(gcc doesn't support `x86-64` architechture however using `clang` still needs some libs of `gcc`, such as `libgfortran`. I try to install `ifort` later) Fortunately, the Planck data can't be added but the vast majority of what I need is the data from `BOSS` and `eBOSS` galaxy experiments.

# Import CLASS  
As https://github.com/lesgourg/class_public/issues/462#issuecomment-1013762091 instructed, we can't make `gcc` work for `x86_64` so we only use `clang`.
Commenting `OMPFLAG   = -fopenmp` in the Makefile and `extra_link_args=['-lgomp']` at the end of the file `pyhton/setup.py`.

We also can set an `arm64` python environment using `CONDA_SUBDIR=osx-arm64 conda create -n py39_native python=3.9 -c conda-forge --override-channels` then `conda env config vars set CONDA_SUBDIR=osx-arm64`. As authors of https://github.com/lesgourg/class_public/issues/384#issue-786806079 says, we can do all of the work on `arm64` if we have a total python environment including `numpy`. However, the python of `arm64` doesn't support some necessary packages of `intel-mkl` for `class` so we only choose `x86_64` and limit the ability of parallelising.

# MontePython setting
