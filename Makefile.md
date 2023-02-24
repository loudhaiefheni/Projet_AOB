CC=gcc
CFLAGS=-march=native -g3 -Ofast -mavx
OFLAGS=-Ofast -fopenmp -funroll-loops -ffast-math -fopt-info-vec-all=nbody.gcc.optrpt -flto -march=native -fuse-linker-plugin

all: nbody3D_OPT_1 nbody3D_OPT_2 nbody3D_OPT_3 nbody3D_OPT_4  nbody3D_NOT_OPT

nbody3D_OPT_1: nbody.c
        $(CC) $(CFLAGS) $(OFLAGS) -D OPT_1 $< -o $@ -lm

nbody3D_OPT_2: nbody.c
        $(CC) $(CFLAGS) $(OFLAGS) -D OPT_2 $< -o $@ -lm

nbody3D_OPT_3: nbody.c
        $(CC) $(CFLAGS) $(OFLAGS) -D OPT_3 $< -o $@ -lm

nbody3D_OPT_4: nbody.c
        $(CC) $(CFLAGS) $(OFLAGS) -D OPT_4 $< -o $@ -lm

nbody3D_NOT_OPT: nbody.c
        $(CC) $(CFLAGS) $(OFLAGS) -D NOT_OPT $< -o $@ -lm

clean:
        rm -Rf *~ nbody3D_OPT_1 nbody3D_OPT_2 nbody3D_OPT_3 nbody3D_OPT_4 nbody3D_NOT_OPT *.optrpt
