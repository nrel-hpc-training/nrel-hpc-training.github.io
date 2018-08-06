# Job Priorities on Peregrine
On the Peregrine system, job priority is determined by queue wait time—the amount of time an eligible job has been waiting in the queue—and the size of the job—number of nodes requested. This enables larger jobs to run in the presence of back-fill scheduling. Larger jobs have a higher priority not because we like them better, but because it helps the scheduler more efficiently plan resources for larger jobs.

When projects reach their allocation limit, jobs associated with those projects will run at very low priority, which will ensure that these jobs run only when there are no jobs waiting for resources from projects that have not yet reached their allocation limit.

Learn about job queues and scheduling policies.

How to View Your Job's Priority
The showq -i command may be used to look at your job's priority or find out why it hasn't started. The showstart -e all <JOBID> can be helpful in estimating when a job will run.

The checkjob -v command can be useful in troubleshoot why a job is not starting.

# How to Get High Priority for a Job
You can submit your job to run at high priority or you can request a node reservation.

Running a Job at High Priority
If you've got a deadline coming up and you want to reduce the queue wait time for your jobs, you can run your jobs at high priority by submitting them with the –l qos=high option. This will provide a large priority boost, which will move the job to the top of the list of jobs waiting for resources.

Jobs that are run at high priority will be charged against the project's allocation at twice the normal rate. If your job would have taken 60 node hours to complete at normal priority, it will be charged 120 node hours against your allocation when run with qos=high.

Requesting a Node Reservation
If you are doing work that requires real time Peregrine access in conjunction with other ESIF user facility laboratory resources, you may request that nodes be reserved for specific time periods.

Your project allocation will be charged for the entire time you have the nodes reserved, whether you use them or not.


