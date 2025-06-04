### System Design Main

<br>

##### Fundamentals

1. Scalability: Ability of a system to handle increased load by scaling vertically or horizontally.
2. Latency: Time taken to process a single request or operation.
3. Throughput: Number of requests a system can handle per unit time.
4. Availability: Percentage of time the system is operational and accessible.
5. Reliability: Ability of a system to function correctly over time without failure.
6. Maintainability: Ease with which a system can be modified or extended.
7. Fault Tolerance: System’s ability to remain functional despite failures.
8. Redundancy: Duplication of components to ensure availability in case of failure.
9. Load Balancing: Distributes incoming network traffic across multiple servers.
10. Caching: Temporarily storing data for faster access on repeated requests.
11. Data Partitioning (Sharding): Splitting data across multiple databases or nodes.
12. Replication: Copying data across multiple machines for fault tolerance and read scalability.
13. Consistency: Ensures every read returns the most recent write.
14. CAP Theorem: In distributed systems, you can only guarantee two of Consistency, Availability, and Partition Tolerance.
15. ACID: Atomicity, Consistency, Isolation, Durability; guarantees for database transactions.
16. BASE: Basically Available, Soft state, Eventually consistent; common in distributed NoSQL systems.
17. Concurrency: Ability to handle multiple operations or users at the same time.
18. Idempotency: Performing the same operation multiple times results in the same effect.
19. Rate Limiting: Restricting the number of operations per user or client in a given time frame.
20. Backpressure: Mechanism to handle overwhelming input by slowing down producers.

##### Architectural

21. Monolithic Architecture: A single unified codebase where all functionality is packaged together.
22. Microservices: Architecture where functionalities are split into independent, deployable services.
23. Service-Oriented Architecture: Similar to microservices but with more emphasis on enterprise services and interoperability.
24. Event-Driven Architecture: Systems communicate using events rather than direct API calls.
25. Serverless Architecture: Backend is managed by the cloud provider, and developers focus only on code.
26. Layered Architecture: Divides responsibilities into layers like presentation, business, and data access.
27. Hexagonal Architecture (Ports and Adapters): Isolates the core logic from outside dependencies.
28. Domain-Driven Design (DDD): Designing software based on real-world business models.
29. Command Query Responsibility Segregation (CQRS): Separates read and write operations into different models.
30. Event Sourcing: Storing all changes to application state as a sequence of events.
31. Model-View-Controller (MVC): Separates an application into three interconnected components.
32. Model-View-ViewModel (MVVM): Enhances MVC for modern UIs with better state management.

##### Distributed Systems

33. Leader Election: Selecting a coordinator node among peers in a cluster.
34. Heartbeat: Regular signal sent to indicate a system is alive.
35. Gossip Protocol: Spreading information through decentralized communication between nodes.
36. Vector Clocks: Tracking causality between events in distributed systems.
37. Quorum: Minimum number of votes required to proceed with an operation (e.g. read/write).
38. Distributed Consensus: Agreement among distributed nodes, e.g., using Paxos or Raft.
39. Replication Lag: Delay between primary and secondary node updates.
40. Data Locality: Keeping data close to where it is processed to reduce latency.
41. Distributed Locking: Mechanism to safely manage access to shared resources across nodes.
42. Anti-Entropy: Process of synchronizing inconsistent replicas.

##### Communication & APIs

43. REST: Representational State Transfer; uses HTTP for stateless communication.
44. GraphQL: Query language for APIs allowing clients to request only needed data.
45. gRPC: High-performance RPC framework using Protocol Buffers.
46. WebSockets: Bi-directional communication between client and server over a single TCP connection.
47. Message Queues: Asynchronous communication via queues (e.g., RabbitMQ, Kafka).
48. Pub/Sub: Publisher-subscriber model for event-based messaging.

##### Databases & Storage

49. Relational Databases: Structured data stored in tables with defined schemas (e.g., PostgreSQL).
50. NoSQL Databases: Schema-less or flexible schema databases (e.g., MongoDB, Cassandra).
51. Columnar Storage: Data stored by columns, optimized for analytical queries.
52. Key-Value Stores: Data stored as key-value pairs (e.g., Redis).
53. Document Stores: Data stored as JSON-like documents (e.g., MongoDB).
54. Time-Series Databases: Optimized for storing time-stamped data (e.g., InfluxDB).
55. Full-Text Search Engines: Specialized databases for search (e.g., Elasticsearch).
56. Write-Ahead Logging (WAL): Logs changes before applying to ensure durability.
57. Compaction: Process of cleaning up redundant/deleted data in log-structured systems.
58. Cold vs Hot Storage: Trade-off between access speed and cost of storing data.

##### Testing & Observability

59. Monitoring: Collecting system metrics for performance and health.
60. Logging: Capturing events and errors during system execution.
61. Tracing: Following the flow of a request across multiple services.
62. Health Checks: Endpoints or processes to validate system readiness and liveness.
63. Canary Releases: Gradually rolling out a new version to a subset of users.
64. Blue-Green Deployment: Switching between two environments for zero-downtime deployment.
65. Chaos Engineering: Intentionally introducing failures to test system resilience.

##### Performance & Optimization

66. Content Delivery Network (CDN): Caches and delivers content closer to users.
67. Edge Computing: Performing computation near the data source to reduce latency.
68. Lazy Loading: Loading data only when it’s needed.
69. Pre-fetching: Loading data in advance to improve perceived performance.
70. Compression: Reducing size of data to improve transfer speed.
71. Connection Pooling: Reusing existing DB connections instead of creating new ones.
72. Database Indexing: Speeds up data retrieval by indexing certain fields.

##### Security

73. Authentication: Verifying the identity of a user.
74. Authorization: Granting access to resources based on permissions.
75. OAuth: Open standard for delegated authorization.
76. JWT (JSON Web Tokens): Compact way to transmit identity and claims between parties.
77. TLS/SSL: Encrypts communication over networks.
78. HMAC: Ensures message integrity and authenticity.
79. Rate Limiting for Abuse Prevention: Prevents DoS and bot abuse.
80. CSRF/XSS Prevention: Mitigating cross-site request forgery and scripting attacks.

##### DevOps & CI/CD

81. Infrastructure as Code (IaC): Managing infrastructure through version-controlled code.
82. Containerization: Isolating apps and dependencies (e.g., Docker).
83. Orchestration: Managing containers and workloads (e.g., Kubernetes).
84. CI/CD Pipelines: Automating testing and deployment processes.
85. Secrets Management: Securely storing and accessing credentials and keys.

##### Design & Tradeoffs

86. Vertical Scaling vs Horizontal Scaling: Adding power vs adding more machines.
87. Strong Consistency vs Eventual Consistency: Immediate accuracy vs eventual synchronization.
88. Latency vs Throughput: Speed vs capacity tradeoff.
89. Read vs Write Optimization: Prioritizing data access or data mutation.
90. Precomputed Data vs On-the-Fly Computation: Speed vs flexibility.
