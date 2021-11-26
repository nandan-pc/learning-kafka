learning-kafka
==============
[100 Days of Code with Apache Kafka®](https://developer.confluent.io/100-days-of-code/)

-------
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**

- [Day 1: Setting up confluent cloud](#day-1-setting-up-confluent-cloud)
- [Day 2: Events](#day-2-events)
- [Day 3: Topics](#day-3-topics)
- [Day 4: Log and Partitions](#day-4-log-and-partitions)
  - [The Log: What every software engineer should know about real-time data's unifying abstraction](#the-log-what-every-software-engineer-should-know-about-real-time-datas-unifying-abstraction)
  - [Partitions](#partitions)
- [Day 5: Brokers](#day-5-brokers)
- [Day 6: Producers](#day-6-producers)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

------
### Day 1: Setting up confluent cloud 
------
  - Set up simple Kafka Cluster in [Confluent Cloud](https://developer.confluent.io/quickstart/kafka-on-confluent-cloud/) , created a topic, and produced and consumed hello world message! 
  - Set up [python client](https://github.com/confluentinc/confluent-kafka-python) on local complete and ran basic producer and consumer program.  
  
--------  
### Day 2: Events
--------
  - [Events](https://developer.confluent.io/learn-kafka/apache-kafka/events/)
    - What is an event ? 
    - Event structure in Kafka i.e. Key/Value pair

--------
### Day 3: Topics
--------
  - [Topics](https://developer.confluent.io/learn-kafka/apache-kafka/topics/) 
    - Topic is fundamental unit of organization of events
    - A topic is a log of events.
    - Logs are simple datastructures with following symantics
      - They are append only When you write a new message into a log, it always goes on the end.
      - They can only be read by seeking an arbitrary offset in the log, then by scanning sequential log entries
      - events in the log are immutable i.e. once something has happened, it is exceedingly difficult to make it un-happen.  
    - Topic is not same as Queue. In Topic data is retained(possibly indefinately). Where as in Queue it is not.(deque operation)  

--------
### Day 4: Log and Partitions
--------
#### [The Log: What every software engineer should know about real-time data's unifying abstraction](https://engineering.linkedin.com/distributed-systems/log-what-every-software-engineer-should-know-about-real-time-datas-unifying) 
  - Part 1: 
      - What is a log ? 
      - Logs in Database : Write ahead log (for Durability - ACID)
      - Logs in Distributed System
        - "State Machine Replication Principle: If two identical, deterministic processes begin in the same state and get the same inputs in the same order, they will produce the same output and end in the same state." 
        - state machine model: Active-Active mode of usage of log
        - primary-backup model: Active-Passive mode of usage of log      
#### [Partitions](https://developer.confluent.io/learn-kafka/apache-kafka/partitions/)
- What is partitioning of a topic ? 
- How events are distributed among partition for a topic ?  
      - Round robin method for events with no key
      - Hashing for events with key
- [How to choose the number of topics/partitions in a Kafka cluster?](https://www.confluent.io/blog/how-choose-number-topics-partitions-kafka-cluster/)    

---------
### Day 5: Brokers 
---------
- [Brokers](https://developer.confluent.io/learn-kafka/apache-kafka/brokers/) 
  - At physical infrastructure standpoint, Kafka is composed of network of machines called borkers 
  - They are independent machines each running Kafka broker process. 
  - Each broker hosts
    - hosts some set of partitions 
    - handles incoming requests to write new events to partitions or read events from them 
    - handles replications of partitions
  - [Broker Documentation](https://docs.confluent.io/platform/current/control-center/brokers.html)
    - Interesting concepts: 
        - [Active Controller]( https://docs.confluent.io/platform/current/control-center/brokers.html):  
            In a Kafka cluster, one of the brokers serves as the controller, which is responsible for managing the states of partitions and replicas and for performing administrative tasks like reassigning partitions. At any given time there is only one controller broker in your cluster. 
        - [Self-Balancing Clusters](https://docs.confluent.io/platform/current/kafka/sbc/index.html#what-are-sbc-long)
           - Confluent Platform deployments can run hundreds of brokers, manage thousands of topics and produce billions of messages per hour. Every day brokers die, new topics are created and deleted, and partitions must be reassigned to balance the workload. This can overload teams tasked with managing Confluent Platform runtime operations.
           - Self-Balancing automates your resource workload balancing, provides failure detection and self-healing, and allows you to add or decommission brokers as needed, with no manual tuning required.     
        - [Self-Balancing vs. Auto Data Balancer](https://docs.confluent.io/platform/current/kafka/sbc/index.html#what-are-sbc-long)
        - [Tiered Storage](https://docs.confluent.io/platform/current/kafka/tiered-storage.html#tiered-storage) 
            - [What is tiered storage ?](https://searchstorage.techtarget.com/definition/tiered-storage)
              - Tiered storage is a method for assigning different categories of data to various types of storage media to reduce overall storage costs and improve the performance and availability of mission-critical applications.  
            - Tiered Storage makes storing huge volumes of data in Kafka manageable by reducing operational burden and cost. The fundamental idea is to separate the concerns of data storage from the concerns of data processing, allowing each to scale independently. With Tiered Storage, you can send [warm data](https://techchannel.com/SMB/9/2012/storage-groups-hot-warm-cold) to cost-effective object storage, and scale brokers only when you need more compute resources.
---------
### Day 6: Producers 
---------  
- [Producers](https://developer.confluent.io/learn-kafka/apache-kafka/producers/)

