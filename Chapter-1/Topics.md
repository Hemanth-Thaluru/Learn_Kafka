## Kafka
 -  Multiple services can read from same stream of Data
 -  Data is kept ffor only limited time
 -  Kafka only accepts bytes as input from producers and sends bytes as outputs to consumers
 -  Murmur2 algorithm is used for key hashing which inturn decides which partitions to go thr

## Kafka Cluster
- Its Combination of Kafka Topics
  
## Topics
  - Its like Table in SQl Data base 
  - But we query Topics but we read and write topic
  - The sequece of msgs to topics are called `Data stream`
  - Name of the topic is identifier
  - Topics are further split to `Partitions`
  
## Partitions
- Message in each partition is ordered
- Msg in Partitions are `immutable`
- Each partitions is incremented by offset
- Data is assigned to partition randomly unless we mention a key for it 

## Producers
 -  It decides which partitions of the topic a new income msg should write to.
 -  It combines msg with key (if key= null then starts with 0 then 1 then 2)
 -  With key value we use HashingTechnique to assign a key to partition so when a msg combines with key then it     goes to particular partition
  
## Kafka Msg
key + value + COmpressionType + header + partition + Timestamp

## Consumers
 - People or system which reads the data from Kafka
 - Their may be group of customers like(Loaction dashboard, fuel consumer)
 - Their side they have deserializer which de-serialize the data coming from kafka
 - Kafka stores the data upto which level consumer has read the data i.e, Consumer Offset

## Kafka Brokers
 - A kafka Cluster consists of many brokers theya re like servers for partitions.
 - They handle service for different partitions since theya re assigned to different partitions
 - Replication factor where a partition is present on different broker so when down other will be available(ISR- In sync replica)

## Durability
 - For a replication factor of 3, topic durability is 2 which means it can withstand 2 broker loss

## Zoo Keeper
 - For selecting leader(partition) in broker, it also manages brokers
 - Incase of changes it send notifications to kafka
 - Not needed from kafka v4 before kafka v2 its mandatory
 - Zookeeper doesn't store consumer offset
 - Security issues with zookeeper alos scling issues when cluster have >100,000 partitions
 - Instead of zookeeper we integrated Quorom Controller(Kafka KRaft )
 - With KRaft there is increase in performance

  