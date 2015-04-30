#Expose Mount Tables
*Note: As of right now this document is only meant to describe the problem to to be solved and gather requirements, not to design potential solutions* 

#Proposal
Expose Mount Tables of part of the DCOS

#Problem Statement:
When there are multiple distributed filesystems connected to a Mesos cluster, clients (e.g. the Mesos fetcher, or a Mesos task) of those filesystems need a clear way to distinguish between them and Mesos needs a way to direct requests to the correct (distributed) filesystem.

##Use Cases:
 - Multiple HDFS clusters on the same Mesos cluster
 - Connecting HDFS, MapRFS, Ceph, Lustre, GlusterFS, S3, GCS, and other SAN/NAS to a Mesos cluster
 - The Mesos fetcher may want to pull from any of the above.
 - An executor or task may want to read or write to multiple filesystems, within the same process.

##Traditional Operating System Analogy:
Each line in Linux's fstab describes a different filesystem to mount into the root filesystem:

1. The device name or remote filesystem to be mounted.
2. The mount point, where the data is to be attached to the root file system.
3. The file system type or algorithm used to interpret the file system.
4. Options to be used when mounting (e.g. Read-Only).

What we need for each filesystem in the Mesos ecosystem:

1. The metadata server or dfs/san entrypoint host:port
2. Mount point, where this filesystem fits into the universal Mesos-accessible filesystem namespace.
3. The protocol to speak, perhaps acceptable URI prefixes.
4. Options, ACLs for which frameworks/principals can access a particular filesystem, and how.

#Challenges:
- Metadata servers may move around, failover.
- Different filesystems may want to mount themselves in the same place.
- Clients/drivers for a given protocol may not be installed accessible from a node/task.
- What ACLs are generic enough that they can apply to a filesystem as a whole, regardless of type?
