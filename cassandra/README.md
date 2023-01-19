# Cassandra <img src="../documentation/images/cassandra-logo.png" alt="cassandra logo" width="70"/>

Apache Cassandra is an open source distributed database management system designed to handle large amounts of data across many commodity servers, providing high availability with no single point of failure.

Cassandra is a [NoSQL database](../documentation/NOSQL.md).

## Docker images

- [cassandra](https://hub.docker.com/_/cassandra):4.1.0

## Ports

| Service       | Port |
| :------------ | :--- |
| cassandra     | 7000 |

## Usage

Place yourself in this folder, configure your environment variables in [docker-compose.yml](./docker-compose.yml) and run

```bash
docker-compose up -d
```

## Cassandra environment variables

`CASSANDRA_SEEDS` environment variable is used to tell each node where the first one is.

Best way to configure Cassandra is to edit [custom-cassandra.yaml](./custom-cassandra.yaml) and to uncomment line 7 and 9 in [docker-compose.yml](./docker-compose.yml)

## Tips

### Persist data

If you want to persist data on filesystem, uncomment the `volumes` section line 7 and 8.

## Resources

- [Apache Cassandra - Wikipedia](https://en.wikipedia.org/wiki/Apache_Cassandra)
- [Apache Cassandra configuration file](https://github.com/apache/cassandra/blob/trunk/conf/cassandra.yaml)
- [How the world caught up with Apache Cassandra](https://techcrunch.com/sponsor/datastax/how-the-world-caught-up-with-apache-cassandra/)