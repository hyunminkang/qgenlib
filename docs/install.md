# Installing qgenlib

## Directory structure

Before installing `qgenlib`, it is recommended to install
[htslib](https://github.com/samtools/htslib) in the same directory you
want to install `qgenlib' (i.e. `qgenlib` and `htslib` should be
siblings directories). 

To visualize the directory structure of the installation, it should look like this: 

```sh
/path/to/install
|-- htslib
|   `-- libhts.a
|-- qgenlib
```

## Installing qgenlib

After installing `htslib`, you can clone the current snapshot of this repository to install as follows

```sh
## clone the current snapshot of this repository
$ git clone https://github.com/hyunminkang/qgenlib.git

## move to the qgenlib directory
$ cd qgenlib

## create a build directory
$ mkdir build

## move to the build directory
$ cd build

## run cmake to configure the build
$ cmake ..
```

If `cmake` is not found, you need to install [cmake](https://cmake.org/) in your system.

## (Optional) Customized specification of the library path

In case any required libraries is missing, you may specify customized installing path by replacing "cmake .." with the following options:


```sh
## If htslib is missing or installed in a different directory
$ cmake -DHTS_INCLUDE_DIRS=/htslib_absolute_path/include/  \
        -DHTS_LIBRARIES=/htslib_absolute_path/lib/libhts.a ..

## If bzip2 is missing or installed in a different directory
$ cmake -DBZIP2_INCLUDE_DIRS=/bzip2_absolute_path/include/ \
        -DBZIP2_LIBRARIES=/bzip2_absolute_path/lib/libbz2.a ..

## If lzma is missing or installed in a different directory
$ cmake -DLZMA_INCLUDE_DIRS=/lzma_absolute_path/include/ \
        -DLZMA_LIBRARIES=/lzma_absolute_path/lib/liblzma.a ..

## You may combine the multiples options above if needed.
## Other missing libraries can be handled in a similar way.
```

## Building the library

Once `cmake` is run successfully without errors, you can build the library by typing:

```sh
## Current directory: /path/to/install/qgenlib/build
$ make
```

To test whether build was successful, you can run the following command:

```sh
## Current directory: /path/to/install/qgenlib/build
$ ../bin/testqgen --tsv ../test/dummy.dat
```