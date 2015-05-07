# Introduce the concept of *clusterwide resources*.
*Note: As of right now this document is only meant to describe the problem to to be solved and gather requirements, not to design potential solutions* 

#Proposal
Introduce the concept of clusterwide resources into Mesos.

#Problem Statement:
There are resources which are not provided by a single node. Consider for example a external Network Bandwidth of a cluster. Being a limited resource it makes sense for Mesos to manage it but still it is not a ressource being offered by a single node.

##Use Cases:
1. Network Bandwidth
2. IP Addresses
2. Distributed File System Storage
3. Software Licences


#Challenges:
- [ ] Zombie Tasks: Task running on a non-reachable slave, but still consuming clusterwide resources.
- - [ ] What is the semantic of reservations on top of clusterwide resources?.

<!---
#Potential Solutions:
- introduce a virtual node representing the cluster and offering these clusterwide resources. 
-->
