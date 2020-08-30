# hash-join-mce

This is the source code for the VLDB 2020 paper titled "Manycore Clique Enumeration with Fast Set Intersections"

This project is a collaborative effort between IBM Research Europe - Zurich and EPFL, partly funded by SNSF (http://p3.snf.ch/Project-172610)

### Building

Prerequisites for building our code:

Compiler: GCC version 7  
Intel Threading Building Blocks library available here: https://github.com/oneapi-src/oneTBB

Our code can be build using the following commands:

```
mkdir build
cd build
cmake .. -DCMAKE_C_COMPILER=`which gcc` -DCMAKE_CXX_COMPILER=`which g++` -DCMAKE_BUILD_TYPE=Release
make
```

### Executing

To run our code, simply execute:

`./mce -f <graph_path>`

The most important command line options are:

```
-f                Path to the input file graph
-p                Prints the resulting clique histogram, no argument
-n                Number of threads, default 256
-o                Turns on memory allocation grouping, no argument
```
To access other command line options use `./graph -h`

An example of running our code:
```
./mce -f ../data/simple.mtx -p -o
```
