# Requesting Different Nodes Types When Submitting Jobs on the Peregrine System
To request a specific type of node, you may use the "feature" option on your resource request. Options available include:

|qsub Option	|Nodes in Peregrine	|Node Description	|
|------------ |-------------------|-----------------|
|-l feature=16core	|432	|16-core 'SandyBridge' nodes	| 
|-l feature=64GB	|288	|24-core, 64GB 'IvyBridge' nodes	| 
|-l feature=256GB	|56	|16-core, 256 GB 'SandyBridge' nodes	| 
|-l feature=24core	|1008	|24-core, 32GB 'IvyBridge' nodes.	 |
|-l feature=haswell	|1238	|24-core, 64GB 'Haswell' nodes	 |

If no features are specified, the job will run on first available node type in the queue requested. If no queue is requested the job will be assigned to batch. All nodes assigned to a single job are of the same type. Learn more about queues and scheduling policies.
