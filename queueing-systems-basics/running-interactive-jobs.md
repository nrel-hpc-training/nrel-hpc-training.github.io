# Running Interactive Jobs on Peregrine
Interactive jobs provide a shell prompt, which allows users to execute commands and scripts as they would on the login nodes.

Login nodes are primarily intended to be used for logging in, editing scripts and submitting batch jobs. Interactive work that involves substantial resources, either memory, CPU cycles or file system I/O, should be performed on the compute nodes rather than on login nodes.

This page provides instructions and examples of the Torque commands used to request interactive jobs.

Interactive jobs may be submitted to any queue and are subject to the same time and node limits as non-interactive jobs

# Requesting Interactive Access
The qsub –I command is used to start an interactive session on one or more compute nodes. When resources become available, interactive access is provided by a shell prompt. The user may then work interactively on the node for the time specified.

The job is held until the scheduler can allocate a node to you. You will see a message such as

qsub : waiting for job 12090.admin1 to start
When it has, you'll see a message such as

qsub: job 12090.admin1 ready
[user@n0416 ~]$
This indicates that node n0416 was allocated to the user.

You do NOT need to ssh to the node after it is assigned but if you requested more than one node, you may ssh to any of the nodes assigned to your job.

You may load modules, run applications, start GUIs etc. and the commands will execute on that node instead of on the login node. The -V option exports your environment variables to the interactive job.

Type exit when finished using the node.

Like any job, a valid project handle must be used when you start an interactive session.

Interactive jobs are useful for many tasks. For example, to debug a job script, users may submit a request to get a set of nodes for interactive use. When the job starts, the user "lands" on a compute node, with a shell prompt. Users may then run the script to be debugged many times without having to wait in the queue multiple times.

A "debug" queue allows a set of nodes to be available with shorter wait times when the system is heavily utilized. This is accomplished by limiting the run time for jobs in that queue to only 1 hour and limiting the maximum number of nodes to 4 per job. To use these nodes, submit your interactive job to the debug queue by adding the -q debug option to the qsub command.

# Sample Interactive Job Commands
The following command requests interactive access to one node for 20 minutes:

```bash
% qsub -I -l nodes=1 -l walltime=0:20:00 -A project-handle
```
If your job needs a GUI that uses X-windows, the least fragile mechanism is to acquire a node as above, then in a separate session set up X11 forwarding:

```bash
% qsub -I -l nodes=1 -l walltime=0:20:00 -A project-handle
...
% (your compute node n1234)
Then from your local workstation,
```

```bash
% ssh -Y peregrine.hpc.nrel.gov
...
% (a login node) ssh -Y n1234
...
% (your compute node n1234, now X11-capable)
% xterm (or another X11 GUI application)
```
The following command requests interactive access to two nodes from the debug queue for 10 minutes and exports environment variables to the session:

```bash
% qsub -V -I -l nodes=2:ppn=16,walltime=10:00 -A project-handle -q debug
```
