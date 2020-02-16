# ddos
The goal of this project was to read a file from local disk and write to a message system using Kafka and application that reads data from the message system and detects whether the attacker is part of the DDOS attack and once an attacker is found, the ip-address should be written to a results directory which could be used for further processing.

Prerequisite
kafka_2.13-2.4.0
Link: https://kafka.apache.org/downloads

Python 2.7
Link: https://www.python.org/ftp/python/2.7.17/

spark-2.4.4-bin-hadoop2.7
Link: https://spark.apache.org/downloads.html

Installation
Download Kafka and edit below two properties

server.properties ----------> log.dirs=C:\kafka_2.13-2.4.0\kafka-logs
zookeeper.properties ----------> dataDir=C:\kafka_2.13-2.4.0\data

Download Python and install kafka

pip install kafka

Download Spark and download JAR: spark-streaming-kafka-0-8-assembly_2.11-2.3.0.jar

Include the Jar in C:\spark-2.4.4-bin-hadoop2.7\jars\

=====================================================================================

Start Services
cd kafka_2.13-2.4.0\
.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties

.\bin\windows\kafka-server-start.bat .\config\server.properties

------------------------------------------------------------------------------------------
Submit Spark Streaming Job
cd users\srava\downloads
spark-submit --master local[*] --deploy-mode client --jars C:\spark-2.4.4-bin-hadoop2.7\jars\spark-streaming-kafka-0-8-assembly_2.11-2.3.0.jar Streaming.py

-----------------------------------------------------------------------------------------
Run Producer.py file
cd  users\srava\downloads
python Producer.py -i apache-access-log.txt
