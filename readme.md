### Kafka commands 

## Topicleri listelemek için kullanılır.
kafka-topics --bootstrap-server broker:9092 --list

## Topic yaratmak için kullanılır. 
## Replikasyon faktör broker sayısından daha fazla olamayacağından dolayı 1 diyoruz.
kafka-topics --bootstrap-server broker:9092 --create --topic topic1 replication-factor 1 --partitions 3 

# Topic'in özelliklerini gösterir.
kafka-topics --bootstrap-server broker:9092 --describe --topic topic1

# Topic'i silmeye yarar.
kafka-topics --bootstrap-server broker:9092 --delete --topic topic1

# Kafka producer shell'ini açar.
kafka-console-producer --bootstrap-server broker:9092 --topic topic1

# Kafka consumer shell'ini açar.
kafka-console-consumer --bootstrap-server broker:9092 --topic topic1

# Kafka producerden key ve property kullanma
kafka-console-producer --bootstrap-server broker:9092 --topic topic1 --property parse.key=true --property key.separator=,

# Kafka consumerdan key ve property kullanama
kafka-console-producer --bootstrap-server broker:9092 --topic topic1 --property parse.key=true --property key.separator=,

# Kafka consumerlarını gruplama
kafka-console-consumer --bootstrap-server broker:9092 --topic topic1 --property parse.key=true --property key.separator=, --group group1

# Kafka grouplarını consume ederken lag'ile karşılaşıp karşılaşımadığının testi
kafka-consumer-groups --bootstrap-server broker:9092 --describe --group group1

# Kafka grouplarını key separator ile consume etme (consume edilen miktar kadar, topic create edilirken partitions'ta aynı sayı verilmeli)
kafka-console-consumer --bootstrap-server broker:9092 --topic topic1 --property parse.key=true --property print.key=true --group group1 


## Servisi ayağa kaldırma
docker-compose.yml -d up
