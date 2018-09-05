1. [Introduction to Using Linux Operating Systems](intro-to-linux)
2. [How to connect to Peregrine (and replacement system) from inside and remote](connecting-to-nrel-hpc)
3. [How to transfer files from one system to another, including GLOBUS](how-to-transfer-files)
5. [Running Jupyter notebooks and python on Peregrine (and replacement system)](Jupyterhub)
6. [Queueing systems and running jobs](queueing-systems-basics)
7. [Software environment basics - Conda, modules, EPEL, Docker containers, etc.](software-environment-basics)
8. [Building applications that use compiled languages](building-packages)
9. [Building applications that use MPI](building-mpi-applications)
10. [Running GUI applications on Peregrine (and replacement system)](running-graphical-applications)
11. [Visualization basics - what we have and how to use it](visualization-basics)
12. [Storing data - short term vs. long term, files, databases & objects, policies](data-storage)

---

# Outline draft:

- ## Introductory
    - ### How 2 Terminal/Linux
    - ### How to connect to Eagle/Peregrine
    - ### How to submit a job (PBS2Slurm table at bottom [needs updated])
- ## Intermediate
- ## Advanced


|                                         |                                                  |                                                       | 
|-----------------------------------------|--------------------------------------------------|-------------------------------------------------------| 
| User Command                            | PBS/Torque                                       | Slurm                                                 | 
| Job submission                          | qsub [script_file]                               | sbatch [script_file]                                  | 
| Job deletion                            | qdel [job_id]                                    | scancel [job_id]                                      | 
| Job status (by job)                     | qstat [job_id]                                   | squeue [job_id]                                       | 
| Job status (by user)                    | qstat -u [user_name]                             | squeue -u [user_name]                                 | 
| Job hold                                | qhold [job_id]                                   | scontrol hold [job_id]                                | 
| Job release                             | qrls [job_id]                                    | scontrol release [job_id]                             | 
| Queue list                              | qstat -Q                                         | squeue                                                | 
| Node list                               | pbsnodes -l                                      | sinfo -N OR scontrol show nodes                       | 
| Cluster status                          | qstat -a                                         | sinfo                                                 | 
| GUI                                     | xpbsmon                                          | sview                                                 | 
|                                         |                                                  |                                                       | 
| Environment                             | PBS/Torque                                       | Slurm                                                 | 
| Job ID                                  | $PBS_JOBID                                       | $SLURM_JOBID                                          | 
| Submit Directory                        | $PBS_O_WORKDIR                                   | $SLURM_SUBMIT_DIR                                     | 
| Submit Host                             | $PBS_O_HOST                                      | $SLURM_SUBMIT_HOST                                    | 
| Node list                               | $PBS_NODEFILE                                    | $SLURM_JOB_NODELIST                                   | 
| Job Array Index                         | $PBS_ARRAYID                                     | $SLURM_ARRAY_TASK_ID                                  | 
|                                         |                                                  |                                                       | 
| Job Specification                       | PBS/Torque                                       | Slurm                                                 | 
| Script directive                        | #PBS                                             | #SBATCH                                               | 
| Queue                                   | -q [queue]                                       | -p [queue]                                            | 
| Node Count                              | -l nodes=[count]                                 | -N [min[-max]]                                        | 
| CPU Count                               | -l ppn=[count] OR -l mppwidth=[PE_count]         | -n [count]                                            | 
| Wall Clock Limit                        | -l walltime=[hh:mm:ss]                           | -t [min] OR -t [days-hh:mm:ss]                        | 
| Standard Output File                    | -o [file_name]                                   | -o [file_name]                                        | 
| Standard Error File                     | -e [file_name]                                   | e [file_name]                                         | 
| Combine Stdout/err                      | -j oe (both to stdout) OR -j eo (both to stderr) | (use -o without -e)                                   | 
| Copy Environment                        | -V                                               | --export=[ALL | NONE | variables]                     | 
| Event Notification                      | -m abe                                           | --mail-type=[events]                                  | 
| Email Address                           | -M [address]                                     | --mail-user=[address]                                 | 
| Job Name                                | -N [name]                                        | --job-name=[name]                                     | 
| Job Restart                             | -r [y|n]                                         | --requeue OR --no-requeue (NOTE:configurable default) | 
| Working Directory                       | N/A                                              | --workdir=[dir_name]                                  | 
| Resource Sharing                        | -l naccesspolicy=singlejob                       | --exclusive OR--shared                                | 
| Memory Size                             | -l mem=[MB]                                      | --mem=[mem][M|G|T] OR --mem-per-cpu=[mem][M|G|T]      | 
| Account to charge                       | -W group_list=[account]                          | --account=[account]                                   | 
| Tasks Per Node                          | -l mppnppn [PEs_per_node]                        | --tasks-per-node=[count]                              | 
| CPU's Per Task                          |                                                  | --cpus-per-task=[count]                               | 
| Job Dependency                          | -d [job_id]                                      | --depend=[state:job_id]                               | 
| Job Project                             |                                                  | --wckey=[name]                                        | 
| Job host preference                     |                                                  | --nodelist=[nodes] AND/OR --exclude=[nodes]           | 
| Quality Of Service                      | -l qos=[name]                                    | --qos=[name]                                          | 
| Job arrays                              | -t [array_spec]                                  | --array=[array_spec]  (Slurm version 2.6+)            | 
| Resources                               | -l other=[resource_spec]                         | --gres=[resource_spec]                                | 
| Licenses                                |                                                  | --licenses=[license_spec]                             | 
| Begin Time,"-a ""YYYY-MM-DD HH:MM:SS""" | --begin=YYYY-MM-DD[THH:MM[:SS]]                  |                                                       | 

