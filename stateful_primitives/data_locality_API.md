# Introduce a API offering Data-Locality Awareness
*Note: As of right now this document is only meant to describe the problem to to be solved and gather requirements, not to design potential solutions* 

#Proposal
Introduce a API offering Data-Locality Awareness.

#Problem Statement:
A number of frameworks (e.g. Hadoop or Spark) process data provided for example by a distributed filesystem or database system. We consider a task being data local if it is scheduled onto (or close to the) node holding the data it required.
In such cases the task processing task can avoid transfering large amounts of data through the network and hence significantly increase performance.


##Use Cases:
Spark/Hadoop on HDFS/DFS


#Challenges:
Common interface to access metadata:
Currently each framework schedulers implement data local against the specific metadata stores it wants to access in a data local aware fashion.
