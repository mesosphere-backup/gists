# Allow frameworks to deploy storage drivers on demand.
*Note: As of right now this document is only meant to describe the problem to to be solved and gather requirements, not to design potential solutions* 

#Proposal
Allow frameworks to deploy storage drivers on demand.

#Problem Statement:
Certain storage options require storage drivers to access them including HDFS driver, Quobyte client, Database driver, and so on.
When Tasks in Mesos require access to such storage they also need access to the respective driver on the node where they were scheduled to.
As it is not desirable to deploy the driver onto all nodes in the cluster, it would be good to deploy the driver on demand.

##Use Cases:
1. Fetcher Cache accessing ressources
2. Frameworks requiring access to HDFS/DFS
3. Databases requiring drivers


#Challenges:
- [ ] Fetc
- [ ] What is the semantic of reservations on top of clusterwide resources?.
- [ ] When can we remove the driver later?
- [ ] Influence on scheduling decision? Treat drivers as kind of special resource? 
- [ ] Different versions/sharing between frameworks?


