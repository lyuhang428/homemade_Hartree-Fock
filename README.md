# homemade restricted Hartree-Fock code

**[中文](README_zh.md)**

`python` + `Fortran` + `C/C++` hybrid restricted Hartree-Fock code, pretty easy to read and modify, but on the same machine it's \~20-fold slower than `Psi4`. 

Molecular integral calculations use `McMurchie-Davidson` algorithm (in principle supports arbitrary quantum angular number, but only tested up to `f` orbital); electron repulsion integral calculation also provides `Rys` quadrature algorithm (supports only up to `d` orbital). 

Molecular integral engine is written in `Fortran`, and provides `Python` interface via `f2py` module. 

`Fortran` code relies on `gsl` library for factorial and confluent hypergeometric function computation. If this library is not installed in the `PATH`, do `export LD_LIBRARY_PATH=/path/to/gsl`. 

Using `multiprocessing` module for parallel computation; ERI 8-fold symmetry is used to reduce computational cost. 
