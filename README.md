# 🚀 Real-Time Kafka Streaming ETL Pipeline (Kafka → PostgreSQL)

## 📌 Overview
This project demonstrates a real-time streaming ETL pipeline using Apache Kafka and PostgreSQL. It simulates financial transaction events, streams them through Kafka, and persists processed data into a relational database using a Python consumer.

The project focuses on event-driven architecture, real-time data processing, and distributed system fundamentals.

---

## ⚙️ Architecture

Producer → Kafka Topic → Consumer → PostgreSQL

---

## 🧱 Tech Stack
- Apache Kafka (KRaft mode)
- Python (kafka-python, psycopg2)
- PostgreSQL
- Windows Environment
- JSON message serialization

---

## 📊 Features
- Real-time event streaming
- Kafka producer generating transaction events
- Kafka consumer processing streaming data
- PostgreSQL data persistence
- Fault-tolerant retry handling
- Schema-aligned data pipeline

---

## 🏗️ System Design

1. **Producer**
   - Generates synthetic customer transaction events
   - Sends JSON messages to Kafka topic `customer_events`

2. **Kafka Broker**
   - Handles message streaming and buffering
   - Ensures durability and ordering of events

3. **Consumer**
   - Reads messages from Kafka
   - Parses JSON payload
   - Inserts records into PostgreSQL

4. **PostgreSQL**
   - Stores structured transaction records
   - Enables querying and analytics

---

## 🗄️ Database Schema

```sql
CREATE TABLE customer_events (
    id SERIAL PRIMARY KEY,
    customer VARCHAR(100),
    amount NUMERIC(10,2),
    currency VARCHAR(10),
    status VARCHAR(20),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

▶️ How to Run
1. Start Kafka (KRaft mode)
kafka-server-start.bat config\kraft\server.properties
2. Start Consumer
python consumer.py
3. Start Producer
python producer.py
📈 Output Example
Received: {'customer': 'Mary', 'amount': 144.92, 'currency': 'NGN', 'status': 'success'}
Inserted into PostgreSQL
🚧 Challenges Solved
Kafka installation and environment setup on Windows
Transition from ZooKeeper to KRaft mode
Topic mismatch debugging
Consumer offset handling
PostgreSQL schema alignment
Missing commit handling in consumer logic
End-to-end streaming pipeline debugging
🎯 Key Learnings
Real-time data streaming architecture
Kafka producer-consumer model
Event-driven system design
ETL pipeline construction
Debugging distributed systems
📌 Author

Built as a Data Engineering learning project focused on real-time streaming systems.
