# hash-join-mce

This is the source code for the VLDB 2020 paper titled "Manycore Clique Enumeration with Fast Set Intersections"

This project is a collaborative effort between IBM Research Europe - Zurich and EPFL, partly funded by SNSF (http://p3.snf.ch/Project-172610)

The contact email address: jov@zurich.ibm.com

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
To access other command line options use `./mce -h`

The file containing the input graph contains the list of edges, one edge per line. Each edge is represented with the identifiers of the two vertices that it connects. 
Optionally, the first row might contain three numbers in format `n n m`, where `n` is the number of vertices and `m` number of edges. 
Graph dataset can be obtained from Network Data Repository https://networkrepository.com/ and SNAP https://snap.stanford.edu/data/.

The sample input graph:
```
6 6 7
1 2
1 5
2 3
2 5
3 4
4 5
4 6
```

An example of running our code:
```
./mce -f ../data/simple.mtx -p -o
```

Which outputs the following clique histogram:
```
# Number of maximal cliques: 5
# Clique histogram:
# clique_size, num_of_cliques
2, 4
3, 1
```
