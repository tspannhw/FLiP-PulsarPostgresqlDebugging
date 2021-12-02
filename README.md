# FLiP-PulsarPostgresqlDebugging

on the docker node
````

    3  bin/pulsar-admin schemas upload pulsar-postgres-jdbc-sink-topic -f ./connectors/avro-schema
    4  bin/pulsar-admin schemas get pulsar-postgres-jdbc-sink-topic
    5  bin/pulsar-admin sinks create --archive ./connectors/pulsar-io-jdbc-postgres-2.8.1.nar --inputs pulsar-postgres-jdbc-sink-topic --name pulsar-postgres-jdbc-sink --sink-config-file ./connectors/pulsar-postgres-jdbc-sink.yaml --parallelism 1
    6  bin/pulsar-admin sinks stop --tenant public --namespace default --name pulsar-postgres-jdbc-sink
    7  bin/pulsar-admin sinks delete --tenant public --namespace default --name pulsar-postgres-jdbc-sink
    8  bin/pulsar-admin sinks create --archive ./connectors/pulsar-io-jdbc-postgres-2.8.1.nar --inputs pulsar-postgres-jdbc-sink-topic --name pulsar-postgres-jdbc-sink --sink-config-file ./connectors/pulsar-postgres-jdbc-sink.yaml --parallelism 1
    9  bin/pulsar-admin sinks get --tenant public --namespace default --name pulsar-postgres-jdbc-sink
   10  bin/pulsar-admin sinks status --tenant public --namespace default --name pulsar-postgres-jdbc-sink
   11  ls -lt
   12  chmod 777 avro-tools-1.11.0.jar
   13  java -jar avro-tools-1.11.0.jar
   14  bin/pulsar-client produce
   15  ls -lt
   16  bin/pulsar-client produce -f testrows.avro pulsar-postgres-jdbc-sink-topic
   17  ls -lt logs
   18  ls -lt logs/functions/public/default/pulsar-postgres-jdbc-sink/pulsar-postgres-jdbc-sink-0.log
   19  cat logs/functions/public/default/pulsar-postgres-jdbc-sink/pulsar-postgres-jdbc-sink-0.log
   20  ls
   21  ls -lt
   22  ls -lt connectors/
   23  vi connectors/pulsar-postgres-jdbc-sink.yaml
   24  cat connectors/pulsar-postgres-jdbc-sink.yaml
   25  bin/pulsar-admin sinks stop --tenant public --namespace default --name pulsar-postgres-jdbc-sink
   26  bin/pulsar-admin sinks delete --tenant public --namespace default --name pulsar-postgres-jdbc-sink
   27  bin/pulsar-admin sinks create --archive ./connectors/pulsar-io-jdbc-postgres-2.8.1.nar --inputs pulsar-postgres-jdbc-sink-topic --name pulsar-postgres-jdbc-sink --sink-config-file ./connectors/pulsar-postgres-jdbc-sink.yaml --parallelism 1
   28  cat ./connectors/pulsar-postgres-jdbc-sink.yaml
   29  history
   30  bin/pulsar-client produce -f testrows.avro pulsar-postgres-jdbc-sink-topic
   
   docker exec -it pulsar /pulsar/bin/pulsar-client consume "persistent://public/default/pulsar-postgres-jdbc-sink-topic" -s "tim" -n 0
   docker cp pulsar/connectors/avro-schema pulsar:/pulsar/connectors
docker cp pulsar/connectors/pulsar-postgres-jdbc-sink.yaml pulsar:/pulsar/connectors
docker cp avro-tools-1.11.0.jar pulsar:/pulsar
docker cp testrows.avro pulsar:/pulsar


   docker exec -it pulsar /bin/bash
   
   ````
