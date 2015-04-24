#Introduce the concept of Shared Resources
*Note: As of right now this document is only meant to describe the problem to to be solved and gather requirements, not to design potential solutions* 

#Proposal
Introduce the concept of Shared Resources.

#Problem Statement:
Multiple frameworks or roles want access to shared resources, including disk, in the DCOS. One example is that Spark and Hadoop may want access to the same persistent resources. Another example is Chronos and Marathon who need access.

##Use Cases:
As a use case, Hadoop and Spark may want to access the same data set stored as a volume in the data center operating system. Chronos and Cassandra may want to access the same disk resources (possibly using Cassandra as a backup for Chronos jobs). Chronos and Marathon may want to use some of the same disk resources for deploying applications as well as jobs. Also, within the same framework, multiple tasks may want to use the same disk resources as well.

#Challenges:
- Currently, in Mesos, a task accepts an offer and then the offer is in use and cannot be used by other tasks. With persistent primitives and reservations, the model is that a specific volume may be reserved for a certain role. This does not allow us to share disk resources, for example, between roles.
- Lifetime of data/Ownership
	When a task writes data into the DFS, 
Same as Task Lifetime -> normal Filesystem
Same as Framework lifetime 
Exceeding framework lifetime (i.e. to be reused by other frameworks)
 What does that it mean to have persisted volumes on top of DFS? Dynamic reservations?
