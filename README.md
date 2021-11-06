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
