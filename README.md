# Atena

![Atena](Atena.png "Atena Logo")

![CI/CD Docker](https://github.com/mchl-labs/atena/workflows/Docker/badge.svg)

### Atena DB is easy to use db equipped with everything you need, don't waste time with boring and endless config, think to develop! Atena will take care of the rest.

## Data Structures K/V

Atena provides only strings as data key/value type. This makes it extremely versatile and all-purpose oriented.

> 💡: With strings we can serialize every data structure into a string with JSON or Protobuf and then store it in Atena.

## 3 DB Engines available

We provide engines for every need:

* [Atena default DB Engine]()
* [Atena RB Tree Engine]()
* [Atena HT Engine]()

## Database

With AtenaDb you can create more than one DB to keep things seprated. Every DB except the `DefaultDB` "Atena", which is always available to Admin, must be called with `AtenaAdmin` before to use it.
- Log System:
    
    Every DB has its own logs. Logs are serialized with ProtoBuf by Google.

## Users

Atenadb is multi-user and support more than one user. We thought you would like to keep things separated.
The default user is `Admin`, and his default password is `Admin`. Not a so safe password right?

> ⚠️: So once you have logged in, we recommend to change your default Admin password immediately.

Users and password have some naming conventions.

They can contains:

* letters
* numbers
* underscores

## Automatic crash recovery

Losing data, even cache records, can be a problem. If something bad happens to your system there is no problem. Atena takes care of it. Atena recovers your data using a fast non-blocking checkpointing technique that lets applications trade-off performance for commit latency and a consistent recovery algorithm. No action needed.

## Metrics and Performance monitoring

Atena provides built-in metrics and management support and everything just works. 😉 We built some amazing dashboards for you, so you can keep everything under control. Take a look at [ the metrics and monitoring section]()

### Built-in Prometheus and Grafana configuration for monitoring.

Atena Metrics are exposed at :5000/metrics.

### Follow these little step to see all your dashboards

1. Go to Grafana login at yourlocation:3000/login. `yourlocation` usually is localhost.
> ⚠️: With k8s `yourlocation` may be different see your services and or ingress
2. In Grafana login with admin credentials (user: admin, password: pass ) and add a datasource. Add Prometheus URL:"http://prometheus:9090" and then import "Prometheus Stats" Dashboard.
3. After that import the 10427 e 10915 dashboards.
4. Finally import a new dashboard from JSON using the file [Grafana Dashboard.json](https://github.com/mchl-labs/atenadb-docker-setup/blob/master/Grafana%20Dashboard.json) that you find in your cloned repo.

## Drivers

### Programming Languages supported:

* [C#](develop/dotnet) : Driver Library Atena DB. Released as a Nuget package `Atena`
* [Go](develop/go)     : Driver Module Atena DB for Golang. Released as Go Module `atena/atenadb`
* [Node.js](develop/nodejs)

From C# and Go you can completly manage Atena. Atena is written in C# (.NET core) and provides full support for the C# language thanks to its library which allows you to connect with Atena. The driver is powered by the gRPC framework to offer very fast transactions and queries as well as an ultra-fast response time.

New languages support soon!

## Atena engines options

### In-memory DB - RBTree

CRUD operations and transactions on DB are made in `log` time (`O(log n)`). Atena is based on an RedBlack Tree implementation in C#.

### LFU and on-disk persistence

LFU and on-disk persistence features can be enabled for any DB from the C# connector at the DB connect time. LFU is powered by a smart algorithm to keep under control the memory usage by the DB. LFU enables when the records exceed half one million and the number of get requests are around 800000. At every optimization the counters which manage the LFU are randomly setted.

> **Note:** LFU works very fine with on-disk persistence enabled because working together they avoid data loss, optimizing the response time and space usage of Atena.

## Security

Atena DB is secure :lock:

Atena DB Client Library provides TLS encryption and HTTP2 using `https` by default in order to communicate with Atena DB.
Users information are stored encrypted and hashed to provide the best security possible.

## Releasing

Releases are built by manteiners.

Atena DB is cross-platform and is available in:

* Docker
* K8s
* Windows
* Linux
* macOS
* ARM

## Next Features - Coming Soon :dart:

- Distributed DB with HA ( High Availability ) as Cluster
