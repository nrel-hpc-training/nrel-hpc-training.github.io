# Commands to Monitor and Control Jobs 

There are a variety of Moab commands to monitor and control jobs on Peregrine. Some handy commands are listed below. The -v option may be used on many commands to get verbose output. Using -v -v provides even more verbose output.

Please see man pages for more information on the commands listed below.


|command	|description|
|---------|-----------|
|checkjob <jobID>	|provide status report for specified job
|mjobctl	|controls various aspects of jobs and can display diagnostic info about each job
|canceljob <jobID>	|cancel specified job. Deprecated, use mjobctl -c <jobID> or mjobctl -F <jobID> instead
|mshow	|display diagnostic messages about the system and queues
|showstart	|shows estimated start time of idle jobs at the time the command is run
|showres	|displays state of all reservations in place within Moab, on a reservation-by-reservation basis.
|showq	|displays information about active, eligible, blocked, and/or recently completed jobs.
|shownodes |gives listing of queues and available nodes and features in those queues.



```bash
[someuser@login1 ~]$ showq
active jobs------------------------
JOBID             USERNAME     STATE  PROCS   REMAINING           STARTTIME
3500057           user1       Running  192  1:23:58:29    Wed Sep 6 11:19:27
3507177           user2       Running   24  1:23:58:29    Wed Sep 6 11:19:27
3487916           user3       Running   24   00:04:58     Mon Sep 4 11:25:56
3487920           user3       Running   24   00:04:58     Mon Sep 4 11:25:56
627 active jobs       53368 of 56464 processors in use by local jobs (94.52%)
                     2359 of 2494 nodes active     (94.59%)
eligible jobs----------------------
JOBID             USERNAME    STATE PROCS     WCLIMIT           QUEUETIME
3510119           user3       Idle   960   2:00:00:00    Wed Sep 6 07:23:00
3510167           user1       Idle   600   2:00:00:00    Wed Sep 6 08:42:13
3510176           user2       Idle   600   2:00:00:00    Wed Sep 6 08:43:38
623 eligible jobs  
blocked jobs-----------------------
JOBID             USERNAME     STATE PROCS     WCLIMIT           QUEUETIME
3500058           user3       Idle   128 2:00:00:00     Fri Sep 1 15:42:36
3500060           user4       Idle   128 2:00:00:00     Fri Sep 1 15:42:36
```


|Types of jobs include | Description |
------------------------|-------------|
|Active  |those that are running or starting and are consuming resources.|
|Eligible |those that are queued and eligible to be scheduled. Their state is Idle.|
|Blocked |those that are currently ineligible to be run or queued.|

Showq can also be used with flags to return more or less information. For example showq -u <USERID> will just give the specified users jobs, and showq -i will give only the queued jobs, but also show to which queue the jobs have been submitted.

Jobs are often blocked by the Moab scheduler for a variety of reasons. The user can view the reasons for the blocked jobs by issuing the following command:


```bash
% checkjob <job-id>
```
To estimate when your jobs will start to run, use the showstart command with the job id.  For example,

```bash
[someuser@login1 ~]$ showstart -e Priority 3510197
job 3510197 requires 1560 procs for 00:06:00 

Estimated Priority based start in           15:38:51 on Thu Sep 7 02:22:45
```
Estimated Priority based completion in     15:44:51 on Thu Sep 7 02:28:45Using the -v -v option on the checkjob command provides verbose output that will show why a job isn't running.

To get information about your job after it runs you may use the showhist.moab.pl script with the job id.  For example,

```bash
[someuser@login1 ~]$ /nopt/moab/tools/moab/showhist.moab.pl 180500
Job Id : 180500
Executable : /nopt/moab/spool/moab.job.iw15dV
User Name : user5
Group Name : user5-upg
Account Name : CSC000
Queue Name : batch
Node Count : 2
Processor Count : 48
Wallclock Duration: 00:01:11
Submit Time : Tue Oct 15 12:01:36 2013
Start Time : Tue Oct 15 12:02:08 2013
End Time : Tue Oct 15 12:03:19 2013
Exit Code : 0
Allocated Nodelist: n0893:n0894
```
This shows that job number 108500 ran on 2 nodes (n0893 and n0894) and took 1 minute 11 seconds.
