# Kafka Samples

## Kafka Producer

When creating a Kafka Producer application client we need an object to represent
the configuration properties of Kafka needed to start up a producer.
Three properties are required: 

- bootstrap.servers
- key.serializer
- value.serializer

### Kafka Properties

`bootstrap.servers` - Cluster membership: partition leaders, etc.

`key and value serializers` - Classes used for message serialization and deserialization.

Example: 
```java
Properties props = new Properties();
properties.put("bootstrap.servers", "BROKER-1:9092", "BROKER-2:9093");
properties.put("key.serializer", "org.apache.kafka.common.serialization.StringSerializer");
properties.put("value.serializer", "org.apache.kafka.common.serialization.StringSerializer");
```

For more configurations you can look at: 
http://kafka.apache.org/documentation/#producerconfigs

With these properties we can actually instantiate our Kafka object to with the basic required properties we've set above to 
an entry point in our application. An Example is below:

```java
public static void main(String[] args){
    Properties props = new Properties();
    properties.put("bootstrap.servers", "BROKER-1:9092", "BROKER-2:9093");
    properties.put("key.serializer", "org.apache.kafka.common.serialization.StringSerializer");
    properties.put("value.serializer", "org.apache.kafka.common.serialization.StringSerializer");

    KafkaProducer myProducer = new KafkaProducer(props);
}
```

### Producer Record

In order for our Kafka Producer to send messeges to Kakfa, it uses a `Producer Record`.
A Producer Record only requires a minimum of two fields to be set which are:
- Topic - The topic to send messages to.
- Value - The message you want to send to the specified topic.

Example:

```java
properties.put("value.serializer", "org.apache.kafka.common.serialization.StringSerializer");
ProducerRecord record = new ProducerRecord("my_topic", "My Message 1");
```