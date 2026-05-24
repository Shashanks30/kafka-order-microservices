# Kafka Order Microservices

Event-driven order processing system built with Apache Kafka 
and Spring Boot microservices.

## Architecture
customerApp (Producer) --[Kafka Topic]--> hotelApp (Consumer)

## Services

### customerApp (Producer)
- Exposes REST API to accept new orders
- Publishes Order events to Kafka topic using KafkaTemplate
- Order contains: id, name, price, email

### hotelApp (Consumer)
- Subscribes to Kafka topic via @KafkaListener
- Processes incoming order events in real-time
- Uses ConcurrentKafkaListenerContainerFactory

## Tech Stack
- Java 17
- Spring Boot
- Apache Kafka
- Spring Kafka
- Maven

## How to Run
1. Start Zookeeper
2. Start Kafka broker
3. Run customerApp (Producer) - mvn spring-boot:run
4. Run hotelApp (Consumer) - mvn spring-boot:run
5. Send POST request to customerApp with order details
