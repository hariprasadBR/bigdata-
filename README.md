# bigdata-
![mapred](https://user-images.githubusercontent.com/84274712/140618883-73d4dd2b-1751-4de5-bc19-eeb9126e54ce.PNG)

### Introduction to MapReduce
MapReduce is a computational component of the Hadoop Framework for easily writing applications that process large amounts of data in-parallel and stored on large clusters of cheap commodity machines in a reliable and fault-tolerant manner. 

MapReduce can perform distributed and parallel computations using large datasets across a large number of nodes. A MapReduce job usually splits the input datasets and then process each of them independently by the Map tasks in a completely parallel manner. The output is then sorted and input to reduce tasks. Both job input and output are stored in file systems. Tasks are scheduled and monitored by the framework.

### How Does MapReduce Work?
MapReduce architecture contains two core components as Daemon services responsible for running mapper and reducer tasks, monitoring, and re-executing the tasks on failure. In Hadoop 2 onwards Resource Manager and Node Manager are the daemon services. When the job client submits a MapReduce job, these daemons come into action. They are also responsible for parallel processing and fault-tolerance features of MapReduce jobs.

In Hadoop 2 onwards resource management and job scheduling or monitoring functionalities are segregated by YARN (Yet Another Resource Negotiator) as different daemons. Compared to Hadoop 1 with Job Tracker and Task Tracker, Hadoop 2 contains a global Resource Manager (RM) and Application Masters (AM) for each application.

- Job Client submits the job to the Resource Manager.
- YARN Resource Manager’s scheduler is responsible for the coordination of resource allocation of the cluster among the running applications.
- The YARN Node Manager runs on each node and does node-level resource management, coordinating with the Resource manager. It launches and monitors the compute containers on the machine on the cluster.
- Application Master helps the resources from Resource Manager and use Node Manager to run and coordinate MapReduce tasks.
- HDFS is usually used to share the job files between other entities.
- ![mapreducer](https://user-images.githubusercontent.com/84274712/140618998-93b398c8-4c8e-4bd7-b398-97412a6bb879.PNG)
# Phases of the MapReduce model
MapReduce model has three major and one optional phase:

### 1. Mapper
It is the first phase of MapReduce programming and contains the coding logic of the mapper function.
The conditional logic is applied to the ‘n’ number of data blocks spread across various data nodes.
Mapper function accepts key-value pairs as input as (k, v), where the key represents the offset address of each record and the value represents the entire record content.
The output of the Mapper phase will also be in the key-value format as (k’, v’).
### 2. Shuffle and Sort
The output of various mappers (k’, v’), then goes into Shuffle and Sort phase.
All the duplicate values are removed, and different values are grouped together based on similar keys.
The output of the Shuffle and Sort phase will be key-value pairs again as key and array of values (k, v[]).
### 3. Reducer
The output of the Shuffle and Sort phase (k, v[]) will be the input of the Reducer phase.
In this phase reducer function’s logic is executed and all the values are aggregated against their corresponding keys.
Reducer consolidates outputs of various mappers and computes the final job output.
The final output is then written into a single file in an output directory of HDFS.
### 4. Combiner
It is an optional phase in the MapReduce model.
The combiner phase is used to optimize the performance of MapReduce jobs.
In this phase, various outputs of the mappers are locally reduced at the node level.
For example, if different mapper outputs (k, v) coming from a single node contains duplicates, then they get combined i.e. locally reduced as a single (k, v[]) output.
This phase makes the Shuffle and Sort phase work even quicker thereby enabling additional performance in MapReduce jobs.
