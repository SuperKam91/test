FC = ifort -lmpi -g -xHost -O3 -align -ansi-alias -mcmodel=medium -traceback
CC = icc -lmpi -g -xHost -O3 -align -ansi-alias -mcmodel=medium -traceback
CXX = icpc -lmpi -g -xHost -O3 -align -ansi-alias -mcmodel=medium -traceback -restrict
LAPACKLIB = -mkl=sequential 
##FC = ifort -lmpi
##CC = icc -lmpi
##CXX = icpc -lmpi
##LAPACKLIB = -mkl=sequential
FFTWLIB = -lfftw3
EXTRAFLAGS = -openmp

export FC CC CXX LAPACKLIB EXTRAFLAGS FFTWLIB
 
.PHONY: multinest McAdam genCMBCM getdist
 
BINDIR = bin
 
all: multinest genCMBCM getdist
 
multinest: 
	gmake -C multinest all  
      
McAdam: 
	-rm McAdam 
	gmake -C src clean 
	gmake -C src McAdam
 
genCMBCM: 
	gmake -C src/genCovMat
 
getdist: 
	gmake -C src/getdist
 
clean: 
	gmake -C src clean 
	gmake -C multinest clean
	gmake -C src/genCovMat clean 
	gmake -C src/getdist clean 
	-rm McAdam 
 
