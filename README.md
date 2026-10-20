# Awesome-Distributed-Key-Value-Stores

## Top Distributed Key-Value Stores Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on Consensus Protocols, Service Discovery & Distributed Configuration*  

**Last updated: October 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Distributed Key-Value Stores**. These tools enable distributed systems to store and retrieve small amounts of critical metadata—cluster configuration, service registries, leader election state, and distributed locks—with strong consistency guarantees across multiple nodes.



**Examples** include etcd, Apache ZooKeeper, HashiCorp Consul, Redis, Hazelcast, Apache Curator, CoreDNS, and Eureka (the category leaders).



**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, consensus protocols, and open service discovery—ideal for platform engineers, SREs, and organizations seeking transparent, vendor-independent distributed infrastructure.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **Redis Enterprise**

  **Commercial version of Redis** with active-active geo-distribution, built-in CRDTs, and enterprise support. **Free tier**: **Redis Cloud Free** provides 30MB storage with limited connections; **Fixed plans start at $5/month** for 250MB. **Typical cost**: ~$1,500–$3,500/month for 50GB with high availability . **Best for**: organizations wanting Redis with commercial support and multi-region replication.



- **HashiCorp Consul Enterprise**

  **Commercial Consul** with multi-tenancy, FIPS 140-3 compliance, and multi-runtime support. **Pricing**: custom quote-only; Standard tier includes service discovery, Premium adds service mesh . **Free trial**: **$500 credit** on HashiCorp Cloud Platform . **Best for**: enterprises needing supported Consul with advanced governance.



- **Hazelcast Enterprise**

  **Commercial in-memory data grid** with CP subsystem, WAN replication, and support. **Pricing**: custom quote-only; **Cloud Serverless** tier available for managed deployment . **Free tier**: **Hazelcast Platform (OSS)** is free with community support . **Best for**: teams needing distributed data structures with enterprise support.



## Open-Source GitHub Projects



- **etcd**

  **Distributed reliable key-value store for the most critical data of a distributed system** (Apache-2.0) — **the Kubernetes standard** . **The primary datastore for Kubernetes**—every cluster state write flows through etcd. **Raft consensus** with **linearizable reads**, **multi-version concurrency control (MVCC)**, **transactions**, **leases**, and **reliable watches** that never silently drop events . **v3.7.0 GA** (July 2026) adds **RangeStream** for large read workloads, **keys-only Range optimization**, and protobuf refactoring . **Maximum reliable database size**: several gigabytes—tuned for metadata, not bulk data . **The reference implementation for distributed configuration**—**choose when you need strong consistency and the Kubernetes ecosystem**.



- **Apache ZooKeeper**

  **Centralized service for maintaining configuration information, naming, providing distributed synchronization, and providing group services** (Apache-2.0) — **the battle-tested veteran** . **Zab consensus protocol** (Paxos variant) with **hierarchical znodes** (like a filesystem), **ephemeral nodes** for session-bound state, and **watches** for change notification . **ZooKeeper 3.9.6** is the current release; 3.7 reached end-of-life February 2024 . **The trade-offs**: **Jute RPC protocol** limits language bindings compared to etcd's gRPC ; **no linearizable reads**—watches can be stale ; **coordination recipes live in Apache Curator**, not the core . **The reference implementation for mature consensus and coordination**—**choose when you need proven leader election and locks in Java-heavy environments**.



- **HashiCorp Consul**

  **Service networking platform** (BSL 1.1 since 1.17) — **the service discovery choice** . **Features**: **DNS or HTTP API service discovery**, **health checking**, **KV store**, **intentions for authorization**, and **multi-datacenter federation** . **Consul 2.0** adds **multi-port service mesh support** (Enterprise), **global RPC rate limiting**, **CyberArk Workload Identity Manager as external CA**, and **opt-in telemetry** . **The trade-offs**: **KV store doesn't scale as well as etcd or ZooKeeper**—millions of keys cause high latency and memory pressure ; **missing multi-version keys, conditional transactions, and reliable streaming watches** . **Best for**: service discovery and health checking—**not a general-purpose coordination store** .



- **Redis**

  **In-memory data structure store** (BSD-3-Clause for open source) — **the lightweight coordination choice** . **Use cases**: **distributed locks via Redlock**, **leader election**, **rate limiting**, and **pub/sub**. **The trade-offs**: **asynchronous replication means failover can lose writes**—Redlock provides a best-effort lock, not a guarantee . **Best for**: teams already using Redis who need lightweight coordination without a dedicated cluster.



- **Apache Curator**

  **Java/JVM client for ZooKeeper with high-level recipes** (Apache-2.0) — **the ZooKeeper coordination layer** . **Recipes**: **leader election**, **distributed locks**, **barriers**, **counters**, and **caches** . **The missing piece** that makes ZooKeeper usable for coordination without writing raw znode logic . **Best for**: Java teams using ZooKeeper who want proven coordination patterns.



- **Hazelcast**

  **In-memory data grid and distributed computing platform** (Apache-2.0 for open source) — **the distributed compute choice** . **Features**: **distributed maps, queues, and locks**, **near-cache**, **distributed executor**, and **CP subsystem** based on Raft . **Best for**: teams needing distributed data structures alongside coordination.



### Additional Strong Open-Source Options



- **CoreDNS** — **DNS server that chains plugins** (Apache-2.0) — **the Kubernetes DNS standard**. **Best for**: DNS-based service discovery with a plugin ecosystem.

- **Eureka** — **REST-based service discovery** (Apache-2.0) — **the Spring Cloud registry** . **Note**: **not actively developed**—Spring Cloud doesn't recommend for new projects . **Best for**: legacy Spring Cloud applications only.

- **Kuma** — **Universal service mesh** (Apache-2.0) — **the mesh-native coordination choice**. **Best for**: teams wanting coordination as part of a service mesh.

- **Raft** — **Reference implementation of the Raft consensus algorithm** (Apache-2.0) — **the foundation beneath etcd, Consul, and Hazelcast CP**.

- Community **n8n** workflows for cluster alerting and leader election notification.



**Frameworks for building custom systems**: Combine **etcd** for Kubernetes-native configuration with **Consul** for service discovery, **ZooKeeper + Curator** for mature coordination primitives, **Redis** for lightweight locks, and **CoreDNS** for DNS-based discovery—creating a comprehensive distributed KV stack.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Distributed key-value stores handling cluster state must follow security best practices, including TLS, authentication, and backup procedures.

- **The "coordination store vs. service discovery" distinction matters.** **etcd and ZooKeeper** are **coordination stores**—linearizable reads, transactions, and reliable watches for leader election and locks  . **Consul and CoreDNS** are **service discovery systems**—finding services by name with health checking . **Redis and Hazelcast** provide **lightweight primitives** with weaker consistency guarantees . **Most production stacks use more than one**—Kubernetes runs on etcd, services discover each other via CoreDNS, and application-level locks might use Redis.

- **etcd vs. ZooKeeper: the choice is often made for you.** **If you run Kubernetes, you run etcd**—it's the backing store  . **If you run Kafka, HBase, or Solr, you may still need ZooKeeper**—those products don't speak etcd's protocol  . **The technical differences matter less than the ecosystem you're already in.**

- **etcd's technical advantages over ZooKeeper are real.** **Dynamic cluster membership**, **stable read/write under high load**, **MVCC**, **reliable watches**, **lease primitives**, and **gRPC with broad language bindings**  . **ZooKeeper's counter**: **mature Curator recipes**, **hierarchical znodes**, and **decades of production use**  .

- **Consul is not a ZooKeeper replacement.** **Its KV store doesn't scale to millions of keys**, and it's **missing conditional transactions and reliable streaming watches**  . **Use Consul for service discovery; use etcd or ZooKeeper for coordination.**

- **Redis is not a consensus system.** **Asynchronous replication means failover can lose writes**—Redlock is best-effort . **If you need linearizable coordination, choose etcd, ZooKeeper, or Consul. If you need a fast lock for a non-critical path, Redis is fine.**

- Self-hosted open-source solutions require proper cluster management, backup strategies, and ongoing maintenance. **KV stores are the source of truth for cluster state**—losing them means losing consistency.



---



**Made for platform engineers, SREs, and organizations building transparent distributed key-value store solutions.**  

Let's make Distributed Key-Value Stores more open, data-driven, and consistent.
