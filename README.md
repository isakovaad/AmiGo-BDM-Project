# AmiGo Social App developed specially for international students and recident of Barcelona 

AmiGo can be defined as a new digital platform dedicated to enhancing social connections through
shared interests and location-based experiences. AmiGo aims to transform the way individuals
connect, fostering communities around diverse activities such as hiking, tennis, dining, and more.
By integrating with local events and businesses, AmiGo offers unique opportunities for real-world
interactions, moving beyond traditional online social networking.
Our idea is to create a platform that not only facilitates the meeting of like-minded individuals but
also promotes meaningful, lasting connections between people, and have new friends.
Then, AmiGo belongs to the technology sector, specifically within the internet and social media
sub-sectors. The startup, that we are presenting in this report, will be the owner of this platform,
and the one that will set the technical and financial resources so as to keep the platform running.


# joint_bdm
The BDM part of joint project

## Dataset Integration
The original dataset and codes to integrate dataset are in folder `/join_fact_table`.

## KPI
The code and the results for KPI analysis are in folder `/KPI`.

## Algo
The recommendation algorithm and sample output are in folder `/algo`.

## Stream Analysis
The stream analysis part are in folder `/stream_analysis`.
We use Kafka to stream the data. Kafka read data from csv and Spark read data from Kafka. Then Spark applied the trained algorithm on every batch. To run this part, make sure that Kafka is installed on the local environment.
For these command, they all run on Mac M1. Commands may change on different systems.

```bash
# open terminal 1, start zookeeper
zookeeper-server-start /opt/homebrew/etc/kafka/zookeeper.properties
# open terminal 2, start kafka server
kafka-server-start /opt/homebrew/etc/kafka/server.properties
# train the collaborative filtering model
python stream_analysis/rec_event_spark_train.py
# open terminal 3, Kafka read data from csv
python stream_analysis/rec_kafka_producer.py
# open terminal 4, Spark read data from Kafka
python stream_analysis/rec_kafka_producer.py
```

To check Kafka is working, you can also use

```bash
# open terminal 3, Kafka read data from csv
python stream_analysis/rec_kafka_producer.py
# open terminal 4, Spark read data from Kafka
stream_analysis/rec_kafka_consumer.py
```

If there is output, then Kafka works well.
