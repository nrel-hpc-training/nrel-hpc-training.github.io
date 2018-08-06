# Sample Batch Scripts for Running Jobs on the Peregrine System

Here are some sample batch scripts for running jobs on Peregrine.

Useful Environment Variables for Use Inside a Job
PBS_O_WORKDIR is set to the location the job was submitted from. Jobs should be run in the users /scratch directory, not in their /home directory.

PBS_NODEFILE points to a file containing a list of nodes allocated to the job.

Sample batch script for a serial job in the debug queue
```bash
#!/bin/bash
#PBS -lnodes=1:ppn=1,walltime=500

#PBS -N test1
#PBS -j oe
#PBS -A CSC001
#PBS -q debug

cd /scratch/<userid>/my_directory
./a.out
```


Sample batch script for a serial job in the default(batch) queue
```bash
#!/bin/bash
#PBS -l walltime=4:00:00           # WALLTIME limit
#PBS -l nodes=1                    # one node
#PBS -N test1                      # Name of job
#PBS -A CSC001                     # project handle

cd $PBS_O_WORKDIR
./a.out
```

Sample batch script for an MPI job using the short queue

This job requests 4 nodes with 24 processes per node using nodes in the short queue.
```bash
#!/bin/bash
#PBS -l walltime=24:00:00 # WALLTIME limit
#PBS -q short                        # short queue
#PBS -l nodes=4:ppn=24               # Number of nodes, put 24 processes on each
#PBS -N test                         # Name of job
#PBS -A CSC001                       # Project handle

cd $PBS_O_WORKDIR
mpirun -np 96 /path/to/executable
```

Sample batch script for high priority job using the short queue

```bash
#!/bin/bash
#PBS -j oe
#PBS -l nodes=2:ppn=2
#PBS -q short
#PBS -l qos=high # Ask for high priority
#PBS -A CSC001
#PBS -l walltime=0:10:00

mpirun -np 4 ./hello_mpi
```
