# Running Batch Jobs on Peregrine
Batch jobs are run on Peregrine by submitting a job script to the scheduler. The script contains the commands needed to set up your environment and run your application.

Users typically create or edit job scripts using a text editor such as vi, emacs or nano.

To submit jobs on Peregrine, the Torque qsub command should be used:

```bash
% qsub <batch_file> -A <project-handle>
```
The job script may contain instructions for the job scheduler. These are preceeded with "#PBS". These may be used to specify resource limits such as wall clock time, number of nodes, etc. as well as what queue and what kind of nodes you want your job to run on.  The same options may be provided as options to the qsub command. If so, command line options to qsub take precedence over similar options in the batch script.

All jobs must specify a project handle that is associated with a project allocation. This may be done with the -A option to qsub or as an option within the script. Jobs submitted without a project handle will be rejected. This prevents jobs with an incorrect spelling of the project handle from sitting in the queue indefinitely.

Program executable files may reside in any file system but input and output files should be read from or written to the /scratch file system.
