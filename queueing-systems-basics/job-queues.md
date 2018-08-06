
# Job Queues
The following table summarizes the node types and limits associated with each queue:

| Queue name	 |debug|  short	  |  batch	|  batch-h	| long  	|  bigmem	| data-transfer| feature |
--------------|-------|---------|---------|-----------|---------|---------|--------------|---|
|Max wall time	 |1 hour|	4 hours |	2 days	| 2 days	  | 10 days |	10 days	| 5 days	   |  |
|Minimum # nodesper job| 	1	|1 |1	|1	|1	|1	| 1| |
|Maximum # nodes per job |	2	| 8	| 288 |	576 |	120	|46	| 1	|  |
|# of 24 core 64 GB Haswell nodes |	2 |	8 |	0	|1228 |	0 |	0	| 0	| haswell | |
|# of 24core 32 GB nodes |	2	|16	| 576 |	0 |	126	| 0	| 0	| 24core | |
|# of 16core 32 GB nodes|2	|8	|195|	0	|162	|0	| 5 |	16core | |
|# of 24core 64 GB nodes |	2	|8	 |198 |	0	| 0	|80	| 0	|64GB | |
|# of 16core 256 GB nodes	|2	|2	|0	|0	|0	|52	| 0	| 256GB| |
|Total # nodes	|10	|42 |	969 |	1228 |	291 |	132	| 5	|  |


Use the option -q queue-name on the qsub command or in your job script to specify what queue your job should go to with #PBS -q queue-name. Sample job scripts and the syntax for specifying the queue are available on the sample job scripts page.

Note that the debug, short, batch and long queues all have more than one node type available. If a particular node type is desired and the queue you are submitting your job to includes that node type, you should ask for it by feature. If you ask for a node with a feature and there are no nodes of that type in that queue, you job may get stuck, so it is recommended that you don't ask for a specific feature unless you need it.

The large queue is intended for jobs that need a large number of nodes. Jobs that run in this queue must use at least 16 nodes. The run time limit in this queue is 1 day, to reduce the wait time for jobs that need a large number of nodes.

The long and bigmem queues are now open to ALL users.


# Job Scheduling Policies
The intent of the debug queue is to provide rapid access to nodes for code development, testing and debugging. Production runs are not permitted in the debug queue. User accounts are subject to suspension if they are determined to be using the debug queue for production computing.

A user can have a maximum of 1000 queued jobs (running/active, eligible/idle, blocked).

Learn how jobs are prioritized [here](https://www.nrel.gov/hpc/peregrine-job-priorities.html).

