# learning-kafka
[100 Days of Code with Apache Kafka®](https://developer.confluent.io/100-days-of-code/)


Day 1: 
  - Set up simple Kafka Cluster in [Confluent Cloud](https://developer.confluent.io/quickstart/kafka-on-confluent-cloud/) , created a topic, and produced and consumed hello world message! 
  - Set up [python client](https://github.com/confluentinc/confluent-kafka-python) on local complete and ran basic producer and consumer program.  
  
Day 2: 
  - [Events](https://developer.confluent.io/learn-kafka/apache-kafka/events/)
    - What is an event ? 
    - Event structure in Kafka i.e. Key/Value pair


Day 3: 
  - [Topics](https://developer.confluent.io/learn-kafka/apache-kafka/topics/) 
    - Topic is fundamental unit of organization of events
    - A topic is a log of events.
    - Logs are simple datastructures with following symantics
      - They are append only When you write a new message into a log, it always goes on the end.
      - They can only be read by seeking an arbitrary offset in the log, then by scanning sequential log entries
      - events in the log are immutable i.e. once something has happened, it is exceedingly difficult to make it un-happen.  
    - Topic is not same as Queue. In Topic data is retained(possibly indefinately). Where as in Queue it is not.(deque operation)     
