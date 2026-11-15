# Technology Alignment & Depth Gaps — Expedia Group (`R-110899`)

## Strong Alignment
- **Experience Floor (`2+ years` Java & Backend):** Meets the `2+ years` threshold (~3 years total engineering experience since Jan 2023).
- **Distributed Systems & Messaging:** Kafka, GCP Pub/Sub, event-driven microservices, Data APIs, AWS & GCP cloud infrastructure, concurrency, algorithms, CI/CD.
- **Reliability & Culture:** Unit/integration testing, observability/monitoring/alerting, incident response, code reviews, pair programming, mentoring, GitHub Copilot.

## Explicit Depth Gaps (Important)
1. **Stateful Stream Processing (`Apache Flink`, `Kafka Streams / KStream`) — PRIMARY GAP:** Production event pipelines used core Kafka producers/consumers and Pub/Sub rather than stateful Flink or KStream windowing/topology APIs.
2. **Confluent Schema Registry & `AWS Kinesis` — MODERATE GAP:** Applied JSON/schema validation in application services, but lacks production Schema Registry (Avro/Protobuf evolution) and AWS Kinesis sharding operations experience.
3. **`Kotlin` / `Scala` (Nice-to-Have) — MINOR GAP:** Core JVM proficiency is in Java (`Java`), not Kotlin or Scala, though both run on JVM and can be learned rapidly.
4. **Clickstream / Global Travel Scale:** Prior workloads operated at multi-brand B2B/SaaS volume rather than Expedia's massive real-time petabyte clickstream scale.

