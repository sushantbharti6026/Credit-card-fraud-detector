* start cassandra server 
cassandra -f
crtl+shift+t
*connect to cassandra server
cqlsh

*create db and table in cassandra(copy creditcard.sql and run on console)

*Dashboard webserver
(in fraud-alert-dashboard) Run FraudAlertDashboard.java

*Access Dashboard UI(ifconfig)
http//192.168.43.135:8080/

* Start zookeper server
cd /usr/local/kafka
zookeeper-server-start etc/kafka/zookeeper.properties
ctrl+shift+t

*Start Kafka server

kafka-server-start etc/kafka/server.properties

ctrl+shift+t

kafka-topics --zookeeper localhost:2181 --create --topic creditcardTransaction --replication-factor 1 --partition 3

*Run Initialimporttocassandra

*Run frauddetectiontraining

*Run dstreamfrauddetection

src/main/resources/application-local.conf

*Run transactionproducer












*******************************clean up********************

*stop transactionProducer

*stop alertdashboardserver

*stop dstreamtransation

kafka-server-stop (created topic creditcardTransaction)

zookeeper-server-stop(shutdown-completed)

rm -rf /tmp/kafka-logs(usr/local/kafka)
rm -rf /tmp/zookeeper
rm -rf /tmp/hs

TRUNCATE customer;
TRUNCATE fraud_transaction;
TRUNCATE non_fraud_transaction;
TRUNCATE kafka_offset;

* ctrl+c in cassandra terminal

delete trained model


