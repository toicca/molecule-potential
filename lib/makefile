
FC = nvfortran
CC = nvcc
FCFLAGS = -shared -O3 -fPIC -gpu=ccall -cuda -cudalib=cufft
CCFLAGS = -shared -O3 -rdc=true --gpu-architecture=sm_60 --compiler-options '-fPIC'
LFLAGS  = -lm -lc -Mcudalib=cufft
TARGET = libqmtools.so
OBJS = $(addsuffix .o,$(basename $(SRC))) 
SRC = vectors.cu basisset.cu molecule.cu kernel-qube.cu kernel-hartree.cu qmtools.cu \
	potential.cuf ftypes.cuf

#$^ references all the prerequisites
#$@ is the target and $< is the (first) prerequisite

$(TARGET) : $(OBJS) link.o
	$(FC) -Mcuda -shared -o $@ $^ $(LFLAGS)
%.o: %.cu
	$(CC) $(CCFLAGS) --device-c $< --output-file $@ 
link.o: vectors.o basisset.o molecule.o kernel-qube.o kernel-hartree.o automaton.o qmtools.o
	$(CC) $(CCFLAGS) --device-link $^ --output-file $@
%.o: %.cuf
	$(FC) -c -fPIC ftypes.cuf
	$(FC) -c $(FCFLAGS) -o $@ $^ 

clean:
	rm -f *.o *.mod



