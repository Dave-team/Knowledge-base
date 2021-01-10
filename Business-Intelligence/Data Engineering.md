# Data engineering
## Definition
Data engineering is about working with backend data and preparing this data in a format that can then be used by analysts as well as data scientists. Key characteristics:
- Often involves big data: data too large for traditional processing systems 
- Often involves ETL 
- Deep knowledge of cloud computing is required 
- Batch processing: where the processing happens of blocks of data that have already been stored over a period of time.
- Stream processing: process data in real time as they arrive
- Messaging services 
- Scheduling services: to schedule jobs on a schedule – often defined within a DAG 
- Parallel processing – run different tasks in parallel to complete tasks on time  

## General
Three important concerns in software systems:
1. Reliability: the system should work correctly
2. Scalability: As the system grows, there should be reasonable ways of dealing with that growth
3. Maintainability: Over time, multiple people will work on /with the system and they should be able to do so productively 

Fault: one component of the system deviating from its spec
Failure: when the system as a whole stops providing the required service to the user 
Reliability: make systems work correctly, even when faults occur. 
Scalability: system’s ability to cope with increased load 
It is impossible to reduce the probability of a fault to zero; therefore it is usually best to design fault-tolerance mechanisms that prevent faults from causing failures

Data distribution is either done using replication (keeping a copy of the same data on different nodes) or partitioning (splitting a big database into subsets called partitions so that different sets can be assigned to different nodes)

## Transactions
Transactions is a way for an application to group several reads and writes into a logical unit. This allows for easier error handling as we don’t have to worry about partial failure. The safety guarantees are often described as ACID: 
- Atomicity: the entire transaction fails when part of it fails
- Consistency: the database is in a good state and certain principles always hold true (e.g. a balance sheet must balance)
- Isolation: concurrently executing transactions are isolated from each other 
- Durability: once a transaction has completed successfully, any data that is has written to it will not be lost 

## Reliable systems design
How do we make our systems reliable, in spite of unreliable humans? The best systems combine several approaches:
- Design systems in a way that minimizes opportunities for error. For example, well-designed abstractions, APIs, and admin interfaces make it easy to do “the right thing” and discourage “the wrong thing.” However, if the interfaces are too restrictive people will work around them, negating their benefit, so this is a tricky balance to get right.
- Decouple the places where people make the most mistakes from the places where they can cause failures. In particular, provide fully featured non-production sandbox environments where people can explore and experiment safely, using real data, without affecting real users.
- Test thoroughly at all levels, from unit tests to whole-system integration tests and manual tests [3]. Automated testing is widely used, well understood, and especially valuable for covering corner cases that rarely arise in normal operation.
- Allow quick and easy recovery from human errors, to minimize the impact in the case of a failure. For example, make it fast to roll back configuration changes, roll out new code gradually (so that any unexpected bugs affect only a small subset of users), and provide tools to recompute data (in case it turns out that the old computation was incorrect).
- Set up detailed and clear monitoring, such as performance metrics and error rates. In other engineering disciplines this is referred to as telemetry. (Once a rocket has left the ground, telemetry is essential for tracking what is happening, and for understanding failures [14].) Monitoring can show us early warning signals and allow us to check whether any assumptions or constraints are being violated. When a problem occurs, metrics can be invaluable in diagnosing the issue.
- Implement good management practices and training—a complex and important aspect, and beyond the scope of this book.

## Design principles
To avoid expensive maintenance in the future, focus on these design principles: 
- Operability: Make it easy for operations teams to keep the system running smoothly. This includes good visibility in the system’s health and having effective ways to manage it 
- Simplicity: Make it easy for new engineers to understand the system, by removing as much complexity as possible from the system. (Note this is not the same as simplicity of the user interface.)
- Evolvability: Make it easy for engineers to make changes to the system in the future, adapting it for unanticipated use cases as requirements change. Also known as extensibility, modifiability, or plasticity.

## Key terms 
**Idempotence**
Simply put, this is the idea that running a task in your dataflow with the same input more than once will have the same effect as running it exactly once.
Why would you want this? Say a later stage of your ETL process breaks so you have to rerun the whole thing and earlier stages that did run successfully are run again. Or the pipeline is triggered twice with the same input for some reason. If the jobs are idempotent you won't get nasty side effects, such as primary key errors throwing errors the second time around, or ending up with duplicated entries.
Practically, this could mean using upserts instead inserts, or checking to see if the stage has been applied on an input already, so that if it has, it won't run again. (more on this below)

**DAGs**
Directed Acyclic Graphs. This is the idea that you structure your dataflows as a series of tasks, each of which has one concern. On top of that, yout task scheduler is aware of dependencies between them. So a later stage of the pipeline will only kick off once all of the input dependencies for that task are met. This graph of tasks is directed because the dependency relation is one way, and acyclic because the there are no cycles in the graph of dependencies. It's a useful abstraction to be able to map out your tasks in terms of, for example: A relies on B, which itself relies of C & D.

**Results caching**
Relating to both of the above, a really useful idea is that of serializing your intermediate steps. By that I mean saving the results of each stage of your pipeline. You can use it enforce idempotence. ie. when processing an input, you can see if there already exists an output for that input, ala memoization. In those cases, you can shortcut to just returning the precomputed result, rather than reprocessing the input file. This is also faster, and allows for efficient rerunning of your pipeline if a later stage breaks. Finally, you can also inspect the contents of intermediate results to check the health of your pipeline and look for processing errors.

**Distribute across multiple machines**
You will most likely want to distribute a database across multiple machines: 
- Scalability
If your data volume, read load, or write load grows bigger than a single machine can handle, you can potentially spread the load across multiple machines.
- Fault tolerance/high availability
If your application needs to continue working even if one machine (or several machines, or the network, or an entire datacenter) goes down, you can use multiple machines to give you redundancy. When one fails, another one can take over.
- Latency
If you have users around the world, you might want to have servers at various locations worldwide so that each user can be served from a datacenter that is geographically close to them. That avoids the users having to wait for network packets to travel halfway around the world.

## Tools
- Kafka - stream processing 
- Spark - collection of open source software for big data
- Hadoop - collection of open source software for big data 
- Databricks - unified analytics framework
- Pyspark – to work with tabular data in Python. Much like pandas, but Pyspark is for when pandas becomes too slow as a data manipulation framework in python
- Other option for engineering is SQLLite in combination with Dask. Dask is very similar to Pyspark - used to work with tabular datasets in Python
- Papermill - for executing Jupyter notebooks
- AWS Glue - for running ETL jobs within the AWS environment 
- Hive – it’s a SQL like interface that allows querying on databases that integrate with Hadoop 
- Airflow – to schedule jobs using a DAG. Can be set up on EC2 but better would be managed services

Airflow is complex. Use lambda or step functions instead. 