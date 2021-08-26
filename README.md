# Atena

![Atena](Atena.png "Atena Logo")

![CI/CD Docker](https://github.com/mchl-coder/atena/workflows/Docker/badge.svg)
### Atena DB is an in-memory K/V store, used as a database and cache. Atena has built-in LFU eviction powered by a smart algorithm which enable also on-disk persistence. Atena provide a real-time log system to minimize crash response time.

## Data Structures K/V

Atena provides only strings data structure. This makes it extremely versatile and all-purpose oriented.

> **Tip:** With strings we can serialize every data structure into a string with JSON or Protobuf and then store it in Atena.

## Database

Atena can handle max 5 DB per instance. This doesn't means that you can have just five DBs. Every DB except the `DefaultDB` "Atena", which is always available to Admin, must be called with `AtenaAdmin` before to use it.
- Log System:
    
    Every DB has its own logs. Logs are serialized with ProtoBuf by Google.

## LFU and on-disk persistence

LFU and on-disk persistence features can be enabled for any DB from the C# connector at the DB connect time. LFU is powered by a smart algorithm to keep under control the memory usage by the DB. LFU enables when the records exceed half one million and the number of get requests are around 800000. At every optimization the counters which manage the LFU are randomly setted.

> **Note:** LFU works very fine with on-disk persistence enabled because working together  they avoid data loss, optimizing the response time and space usage of Atena.

The `DefaultDB` "Atena" has LFU and on-disk persistence enable by default.

## Drivers

### Programming Languages supported:

* [C#](Atena) : Driver Library Atena DB. Released as a Nuget package `Atena`
* Go        : Driver Module Atena DB for Golang. Released as Go Module `atena/atenadb`

From C# you can completly manage Atena. Atena is written in C# (.NET core) and provides full support for the C# language thanks to its library which allows you to connect with Atena. The driver is powered by the gRPC framework to offer very fast transactions and queries as well as an ultra-fast response time.

New languages support soon!

Code examples are available in the [examples](examples) directory.

## In-memory DB - RBTree

CRUD operations and transactions on DB are made in `log` time (`O(log n)`). Atena is based on an RedBlack Tree implementation in C#.

## Security

Atena DB is secure :lock:

Atena DB Client Library provides TLS encryption using `https` by default in order to communicate with Atena DB.

## Releasing

Releases are built by manteiners.

Atena DB is cross-platform and is available in:

* Windows
* Linux
* macOS
* ARM

### Docker Support

#### Requirements:

:white_check_mark: Docker installed

:white_check_mark: Docker Compose installed

Then run Docker Compose: `docker-compose up`

## Metrics and Performance monitoring

Atena Metrics are exposed at /metrics.
Built-in Prometheus and Grafana configuration for monitoring.

In Grafana login with admin credentials ( password: pass ) and add a datasource. Add Prometheus URL:"http://prometheus:9090" and then import "Prometheus Stats" Dashboard.
After that import the 10427 e 10915
After that import a new dashboard from JSON using the file Grafana Dashboard.json

## Next Features - Coming Soon :dart:

- Distributed DB as Cluster
