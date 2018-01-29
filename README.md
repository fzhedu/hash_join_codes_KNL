# hash_join_codes_KNL
Vectorized implementations of hash join algorithms on Intel Xeon Phi (KNL)

## Overview
Advanced processor architectures have been driving new designs, implementations and optimizations of main-memory hash join algorithms recently. The newly released Intel Xeon Phi many-core processor of the Knights Landing architecture (KNL) embraces interesting hardware features such as many low-frequency out-of-order cores connected on a 2D mesh, and high-bandwidth multi-channel memory (MCDRAM). 

In these implementations, we experimentally revisit the state-of-the-art main-memory hash join algorithms to study how the new hardware features of KNL affect the algorithmic design and tuning as well as to identify the opportunities for further performance improvement on KNL. In detail, we implement the state-of-the-art simple hash joni, partitioned hash join (with and without NUMA-aware optimizations).  Our experiments show that, although many existing optimizations are still valid on KNL with proper tuning, even the state-of-the-art algorithms have severely underutilized the memory bandwidth and other hardware resources. 

## Prerequisites

### Hardware

* Intel Xeon Phi Many-core processor of the Knights Landing Architecture 

### Software

* Linux 
* Intel C/C++ 17.0.2 20170213
* The [memkind library](https://github.com/memkind/memkind)

## Build
```
make npj
make phj
make cpra
```

## Generate input relations
```
make write
./write [#threads] [size of the outer relation] [size of the input relation] 
```

## Run hash joins
```
./npj [#threads] [size of the outer relation] [size of the input relation]
./phj [#threads] [size of the outer relation] [size of the input relation]
./cpra [#threads] [size of the outer relation] [size of the input relation]
```
