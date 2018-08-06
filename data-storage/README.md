# data-storage

Data Retention Policy
To protect against data loss, you must understand the NREL HPC Data Retention Policy.

File storage areas on Peregrine and Gyrfalcon are either user-centric:

/home/<username>
/scratch/<username>
/mss/users/<username>
or project-centric:

/projects/<project-id>  
/mss/projects/<project-id>
Project-Centric Data
Project data on Peregrine (in /projects/<project-id>) will be retained for 3 months after the project allocation ends to allow project members time to move data either to local resources or to /mss/<project-id>. Project members will be notified of the need to move their files when their project ends. The PI will be notified again at the end of this 3 month period.

Project data in /mss will be retained for 15 months after the project allocation ends, which is 1 year after the 3 month period during which project data is retained on the /projects filesystem. After this retention period, we reserve the right to delete files if we need to reclaim storage.  We can make special arrangements for permanent storage, if needed.

User-Centric Data
Users accounts that are associated only with expired projects will be deactivated 3 months after the last project they are associated with ends. The retention period for files in /home/<username> is 3 months after the last project ends.  During this retention period, the user may log in to transfer data to external storage or to their/mss directories.  User files in /mss/users/<username> will be retained for 1 year, after which we reserve the right to delete files to reclaim tape storage.

User accounts are locked and access to files is lost when the AUP (Appropriate Use Policy) period expires or contractual arrangements with NREL end. This may occur during an allocation period (depending on when the AUP period began).  The typical AUP period for external users (non-NREL employee) is one year.  Users will be warned about AUP expiration before the expiration date.

User accounts will be deactivated if they are inactive (no logins) for 6 months.  Files in /home/<username> will be retained for 3 months after account deactivation. Users may request that accounts be reactivated during this time to enable files to be moved.  Files in /mss/users/<username> will be retained for 1 year, after which we reserve the right to delete files to reclaim tape storage.

Files in /scratch/<username> are subject to purging to prevent the file system from filling up. Files are removed based on the last access time, with the least recently accessed files removed first. Files that haven’t been accessed in 28 days are eligible for deletion.



