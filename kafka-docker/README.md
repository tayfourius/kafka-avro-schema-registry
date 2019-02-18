[![Docker Pulls](https://img.shields.io/docker/pulls/wurstmeister/kafka.svg)](https://hub.docker.com/r/wurstmeister/kafka/)
[![Docker Stars](https://img.shields.io/docker/stars/wurstmeister/kafka.svg)](https://hub.docker.com/r/wurstmeister/kafka/)
[![](https://images.microbadger.com/badges/version/wurstmeister/kafka.svg)](https://microbadger.com/images/wurstmeister/kafka "Get your own version badge on microbadger.com")
[![](https://images.microbadger.com/badges/image/wurstmeister/kafka.svg)](https://microbadger.com/images/wurstmeister/kafka "Get your own image badge on microbadger.com")
[![Build Status](https://travis-ci.org/wurstmeister/kafka-docker.svg?branch=master)](https://travis-ci.org/wurstmeister/kafka-docker)

kafka-docker
============

Dockerfile for [Apache Kafka](http://kafka.apache.org/)

The image is available directly from [Docker Hub](https://hub.docker.com/r/wurstmeister/kafka/)

---



---


## Usage

Start a cluster:

- ```docker-compose up -d ```

Add more brokers:

- ```docker-compose scale kafka=3```

Destroy a cluster:

- ```docker-compose stop```

Start full stack kafka cluster: 
- ```docker-compose -f full-stack.yml up -d ```

## Note

full-stack.yml include : zookeeper, kafka, kafka-jmx-exporter, prometheus, grafana, graf-db, schema-registry, rest-proxy, kafdrop, schema-registry-ui,  kafka-topics-ui, zoonavigator-web, zoonavigator-api, kafka-manager



## Automatically create topics

If you want to have kafka-docker automatically create topics in Kafka during
creation, a ```KAFKA_CREATE_TOPICS``` environment variable can be
added in ```docker-compose.yml```.

Here is an example snippet from ```docker-compose.yml```:

        environment:
          KAFKA_CREATE_TOPICS: "Topic1:1:3,Topic2:1:1:compact"

```Topic 1``` will have 1 partition and 3 replicas, ```Topic 2``` will have 1 partition, 1 replica and a `cleanup.policy` set to `compact`. Also, see FAQ: [Topic compaction does not work](https://github.com/wurstmeister/kafka-docker/wiki#topic-compaction-does-not-work)

If you wish to use multi-line YAML or some other delimiter between your topic definitions, override the default `,` separator by specifying the `KAFKA_CREATE_TOPICS_SEPARATOR` environment variable.

For example, `KAFKA_CREATE_TOPICS_SEPARATOR: "$$'\n'"` would use a newline to split the topic definitions. Syntax has to follow docker-compose escaping rules, and [ANSI-C](https://www.gnu.org/software/bash/manual/html_node/ANSI_002dC-Quoting.html) quoting.



## Tutorial

[http://wurstmeister.github.io/kafka-docker/](http://wurstmeister.github.io/kafka-docker/)
