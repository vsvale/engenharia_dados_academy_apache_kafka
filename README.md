# engenharia_dados_academy_apache_kafka

### Create a topic
- kubectl get pods -n ingestion
- kubect exec -n ingestion -ti edh-kafka-0 -- bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 3 --partitions 6 --topic src-app-users-json-manual

### List topics
- kubectl get kafkatopics
- kubectl exec -n ingestion -ti edh-kafka-0 -- bin/kafka-topics.sh --list --bootstrap-server localhost:9092

### Count events
- kubectl exec -n ingestion -ti edh-kafka-0 -- bin/kafka-run-class.sh kafka.tools.GetOffsetShell --broker-list localhost:9092 --topic src-app-users-json-manual topicName:partitionID:offset

### read messages using kafkacat
- kafkacat -C -b localhost:9092 -t src-app-users-json-manual -J -o end
