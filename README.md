# Kafka
**What is kafka**
- Kafka is a open-source distribute event streaming platfrom. which mean it creates real time stream and process real time stream.
- Sending the stream of continuous data to the kafka server is called creating or generating real time event stream of data
1. **Kafka Cluster**
   - A Kafka cluster is a distributed system or group of one or more Kafka brokers (servers)
   - **Components of a Kafka Cluster:**
     - **Kafka Brokers:**
       - Each broker is a Kafka server that stores and processes messages.
       - Brokers handle read and write requests and store message data on disk.
       - Multiple brokers form a cluster, ensuring fault tolerance and scalability.
    - **Topics:**
      - Topics are the categories or feeds where messages are stored.
      - Messages within a topic are distributed across partitions.
    - **partitions:**
      - A topic is divided into partitions, enabling parallelism.
      - Each partition is replicated across multiple brokers to ensure reliability.
      - Partitions are ordered, and each message has a unique offset.
    - **Producers:**
      - Producers publish data to topics.
      - They can decide which partition to send messages to, either manually or automatically based on keys.
    - **Consumers:**
      - Consumers subscribe to topics and read messages.
      - Kafka tracks which messages have been read by maintaining consumer group offsets.
    - **Zookeeper:**
      - Originally used for cluster metadata management,kafka health, leader election, and coordination.
      - Kafka is moving towards replacing Zookeeper with its internal Kafka Raft Consensus (KRaft) for simplicity and efficiency.
2. **Kafka Connect**
   - Kafka Connect is a framework for integrating Apache Kafka with other data systems (databases, key-value stores, search indices, etc.).
   - It simplifies data integration by providing pre-built connectors for common data sources and sinks, allowing developers to stream data into and out of a Kafka cluster without writing custom code.
   - **source connectors:**
     - Reads data from an external system (e.g., MySQL, PostgreSQL, or a file system).
     - Converts the data into Kafka-compatible records.
     - Publishes the records to a Kafka topic.
   - **Sink connectors:**
     - Reads messages from a Kafka topic.
     - Writes the messages to an external system (e.g., Elasticsearch, HDFS, or a database).
   - **Tasks:**
     - Kafka Connect splits work into tasks, where each task processes a subset of the data.
     - Tasks are managed and distributed by Kafka Connect workers.
   - **Workers:**
     - Workers are the processes running the Kafka Connect framework.
     - In distributed mode, workers share the workload and provide fault tolerance.
   - **Kafka Connect Modes:**
     - **Standalone Mode:**
       - Single worker process.
       - Suitable for development, testing, or small-scale production environments.
     - **Distributed Mode:**
       - Multiple worker processes on different nodes.
       - Offers scalability and fault tolerance.
       - Workers are coordinated using Kafka itself.
3. **Kafka Streams**
   - Kafka Streams is a powerful, lightweight stream processing library that is part of the Apache Kafka ecosystem.
   - It enables developers to build real-time applications and microservices that process data directly from Kafka topics and produce results back into Kafka.
   - Unlike Kafka Connect, which is used for data integration, Kafka Streams focuses on processing and transforming data streams in real time.
   - **How Kafka Streams Works:**
     - **Streams and Tables:**
       - A stream is an unbounded sequence of events (e.g., Kafka topic data).
       - A table is derived from streams and represents a snapshot or aggregation of data at a point in time.
     - **Stream Processing DSL**
       - Kafka Streams provides a high-level DSL (Domain-Specific Language) for defining processing pipelines:
       - ```filter()```, ```map()```, ```flatMap()```, ```groupBy()```, ```aggregate()```, etc.
     - **Topology:**
       - Kafka Streams applications define a topology, which is a directed graph of processing nodes that represent transformations.
     - **State Stores:**
       - For stateful operations (e.g., joins or aggregations), Kafka Streams maintains state stores to manage intermediate data.
