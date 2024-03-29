# AFSSH_spinBoson_NQE
Surface hopping codes for the spin-Boson model.

Please feel free to ask questions at amberj@iitb.ac.in or aarti.1@iitb.ac.in

****
Requires lapack subroutien dsyevr to diagonalize
TIP: LAPACK matrix multiplication subroutines give decent speedups too.
****

Look at makefile for compilation instructions.
Path for LAPACK and BLAS libraries need to be provided.

***
The code is entirely in mod_afssh.f90. The input file is in AFSSH.inp.
The potential subroutines are in compute_potential, and the potential parameters are set in setup_parameters. The dvr basis for the vibrational quantization are defined in setup_quantized_vib subroutine.

To compile, issue make. The makefile tells the compiling options.
After compiliing, ./aout can be issued to run the job on the current processor.

./run (together with sub.sh) is designed to run the codes on nodes on our cluster. It should be relatively easy to change to run on different environments. The first parameter in AFSSH.inp - iflow - directs how the code will be run. If iflow=1, it is run serially on a single node.
If iflow=2, trajectories are parallelized. For iflow=2, after all jobs are completed, set iflow=3 (in AFSSH.inp) and again issue ./run to generate the averaged file (from the various folders that will be created for iflow=2). These are also attached if needed.

The output is in the file pop.out. The columns are - time (fs), diabatic populations

The files starting with output are also generated, most of which are empty. Setting iwrite=1 in AFSSH.inp will generate individual trajectory information in these files.

