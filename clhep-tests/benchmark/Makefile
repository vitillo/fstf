CC=g++
CXXFLAGS=-O2 -fopenmp -g -mavx -march=native -I/opt/intel/composerxe/mkl/include/ -I/opt/intel/composerxe/ipp/include -Iinclude -Iinclude/eigen3 -Iinclude/root -Wall
LDFLAGS = -L/opt/intel/composerxe/compiler/lib/intel64/ -L/opt/intel/composerxe/mkl/lib/intel64/ -L/opt/intel/composerxe/ipp/lib/intel64/ -lgomp -lipps -lippm -lmkl_core -lmkl_intel_lp64 -lmkl_gnu_thread -lmkl_avx -L./lib -lgomp -lCLHEP

all: main.o testAVX.o testAVX.h testTransformCLHEP testTransformEigen
	$(CC) $(LDFLAGS) testAVX.o main.o -o kernel

testTransformCLHEP: testTransformCLHEP.cpp
	$(CC) $(CXXFLAGS) $(LDFLAGS) testTransformCLHEP.cpp -o testTransformCLHEP

testTransformEigen: testTransformEigen.cpp
	$(CC) $(CXXFLAGS) $(LDFLAGS) testTransformEigen.cpp -o testTransformEigen

testAVX.o: testAVX.cpp testAVX.h
	$(CC) $(CXXFLAGS) -c testAVX.cpp

main.o: main.cpp testAVX.h
	$(CC) $(CXXFLAGS) -c main.cpp

clean:
	-rm -rf *.o kernel
