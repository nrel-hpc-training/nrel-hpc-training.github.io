# queueing-systems-basics

Peregrine uses the Moab workload manager/job scheduler and the Torque resource manager. These tools have commands for job submission, job monitoring, and job control (hold, delete, and resource request modification).

A "job" contains a list of required consumable resources (such as nodes), a list of job constraints (when, where and how the job should run) and an execution environment, which includes things like an executable, input and output files).

Both interactive jobs (you are given a shell on one or more compute nodes) and regular "batch" jobs are supported.

All compute nodes are scheduled so that only one job may use a node at a time.

To run a job on Peregrine, you must have a project resource allocation.

Each project has a project handle associated with it, which was specified in the project request document. Jobs submitted without a valid project handle will be rejected with an error message.  Please note that this project identifier is referred to as an allocation handle in error messages and as an account string in system man pages.  The project handle may be included with the -A option either on the command line or within the batch script.  After usage exceeds the node hour allocation for a project, jobs will run at very low priority.


# Submitting Jobs
To submit jobs on Peregrine, the Torque qsub command should be used. This can be used to start an interactive job or to run a job involving a script that is run by Torque.

```bash
% qsub -A <project-handle> <script>
% qsub -A <project-handle> -I
```
If you are doing automated job submissions, please limit the submission rate to no more than 20 jobs per second.

# For More Information


* [Learn how to view your job's prioritiy and request high priority for a job.](..hpc-training/queueing-systems-basics/job-priorities.md)
* [Learn about job queues and scheduling policies.](..hpc-training/queueing-systems-basics/job-queues.md)
* [Learn how to run batch jobs.](..hpc-training/queueing-systems-basics/batch-jobs.md)
* [Learn commands to monitor and control jobs.](hpc-training/queueing-systems-basics/monitor-jobs.md)
* [Learn how to run interactive jobs.](hpc-training/queueing-systems-basics/running-interactive-jobs.md)
* [Learn how to run multiple sub-jobs with one job script.](hpc-training/queueing-systems-basics/multiple-sub-jobs.md)
* [Learn sample batch scripts for running jobs.](hpc-training/queueing-systems-basics/sample-batch-scripts.md)
* [Learn how to request different node types when submitting jobs.](hpc-training/queueing-systems-basics/request-different-node-type.md)
