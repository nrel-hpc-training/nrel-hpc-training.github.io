# Running Multiple Sub-Jobs with One Job Script on the Peregrine System
If your workload consists of serial or modestly parallel programs, you can run multiple instances of your program at the same time using different processor cores on a single node. This will allow you to make better use of your allocation because it will use the resources on the node that would otherwise be idle.

Example
For illustration, we use a simple C code to calculate pi. The source code and instructions for building that program are provided below:

```bash
# pi.c: A sample C code calculating pi

cat << eof > pi.c
#include <stdio.h>

main() {
  double x,h,sum = 0;
  int i,N;
  scanf("%d",&N);
  h=1.0/(double) N;
 
  for (i=0; i<N; i++) {
   x=h*((double) i + 0.5);
   sum += 4.0*h/(1.0+x*x);
  }

  printf("\nN=%d, PI=%.15f\n", N,sum);
 }
 
 eof
 
 #Compile the code using the Intel C compiler
 module purge
 module load impi-intel
 icc -O2 pi.c -o pi_test
```

A sample batch job script file to run 8 copies of the pi_test program on a node with 24 processor cores is given below. This script creates 8 directories and starts 8 jobs, each in the background. It waits for all 8 jobs to complete before finishing.

```bash
#!/bin/bash
#PBS -l walltime=00:10:00   # WALLTIME limit
#PBS -l nodes=1:ppn=24         
#PBS -q short
#PBS -N wait_test
#PBS -o std.out
#PBS -e std.err
#PBS -A hpc-apps            # Account (replace with appropriate)

cd $PBS_O_WORKDIR

JOBNAME=waitTest

# Run 8 jobs (must be less than ppn)
N_JOB=8
 
for((i=1;i<=$N_JOB;i++))
do
mkdir $JOBNAME.run$i             # Make subdirectories for each job
cd $JOBNAME.run$i                # Go to job directory
echo 10*10^$i | bc > input       # Make input files
time ../pi_test < input > log &  # Run your executable, note the "&"
cd ..
done
 
#Wait for all
wait
 
echo
echo "All done. Checking results:"
grep "PI" $JOBNAME.*/log
```
To submit the batch script on Peregrine, the Torque qsub command should be used:

```bash
% qsub <batch_file> -A <project-handle>
```
