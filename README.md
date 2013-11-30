rodinia-benchmark
=================

Helper scripts for Rodinia, and patches to make test suites work on the Samsung Chromebook ARM, under [crouton](https://github.com/dnschneid/crouton).

Prerequisites
-------------

On x86:
 - OpenCL drivers for you GPU.

On the Samsung Chromebook ARM:
 - crouton, ARM Mali OpenCL driver and SDK. See the instructions on [this page](http://drinkcat.blogspot.sg/2013/11/opencl-on-samsung-chromebook-arm-under.html).

Instructions
------------

Download and extract this repository to `rodinia-benchmark`

Download Rodinia (https://www.cs.virginia.edu/~skadron/wiki/rodinia/index.php/Main_Page):
```
wget http://www.cs.virginia.edu/~kw5na/lava/Rodinia/Packages/Current/rodinia_2.4.tar.bz2
tar xf rodinia_2.4.tar.bz2
cd rodinia_2.4
cat ../rodinia-benchmark/patches/*.patch | patch -p1
```

On a x86 machine, if your graphics card is a bit dated, you can apply some patch to reduce the work size of some OpenCL benchmarks:
```
cat ../rodinia-benchmark/patches/x86/*.patch | patch -p1
```

On the Samsung ARM, you need to apply these patches:
```
cat ../rodinia-benchmark/patches/arm/*.patch | patch -p1
```

Compile the tests:
```
make -j3 OMP OPENCL
```

And finally run some selected benchmarks:
```
sh runall
```


