Using:

"docker-compose up -d" 

Only to start certain services : "docker-compose up -d elasticsearch kibana"

Here's a brief summary of the services:
setup: 
• Initializes the environment, possibly related to Elastic Stack setup. 
• Builds from the setup/ context. 
• Uses volumes for state persistence. 
• Defines environment variables for passwords.

elasticsearch: 
• Builds Elasticsearch service. 
• Mounts Elasticsearch configuration and data volumes. 
• Exposes ports 9200 and 9300 for communication.
• Configures environment variables for Elasticsearch settings.

logstash: 
• Builds Logstash service. 
• Mounts Logstash configuration and pipeline volumes. 
• Exposes ports for Logstash communication. 
• Configures environment variables for Logstash settings. 
• Depends on Elasticsearch.

kibana: 
• Builds Kibana service. 
• Mounts Kibana configuration volume. 
• Exposes port 5601 for Kibana UI. 
• Configures environment variables for Kibana settings. 
• Depends on Elasticsearch.

zookeeper: 
• Uses Confluent's Zookeeper image. 
• Exposes port 22181 for Zookeeper.

kafka: 
• Uses Confluent's Kafka image. 
• Depends on Zookeeper. 
• Exposes port 29092 for Kafka communication.

kafka-ui: 
• Uses provectuslabs/kafka-ui image. 
• Depends on Kafka. • Exposes port 8090 for Kafka UI.

mongodb: 
• Uses the official MongoDB 6.0 image. 
• Sets up authentication. • Exposes port 37017 for MongoDB.

mqtt-broker: 
• Uses the eclipse-mosquitto image. 
• Sets up volumes for Mosquitto configuration, data, and logs. 
• Exposes ports 1883 and 9001 for MQTT communication. 
The networks section defines a bridge network named "project" for communication between services. 

Lastly, there are two volumes named "setup" and "project" for persistent storage. 
Remember to create necessary directories for mounting volumes and provide configuration files for each service if they are not present in the project directory.
