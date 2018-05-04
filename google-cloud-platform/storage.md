# Storage

Everything is encrypted at rest.

## Local SSD

* 375GB SSD physically attached to the server (AWS EC2 Store Volumes)
* Can stripe across 8 drives for even better performance
* Data is lost when instances shut down
    * can survive a Live Migration
* Pay by GB-month

## Persistent Disk (PD)

* Zonal
* Flexible, block-based network-attached storage; boot disk for every GCE (AWS EBS)
* Data is encrypted in transit between PD and GCE
* Performance scales with volume size, way below Local SSD
* Replicated for durability and persist, can be reattached to new instance within zone
* Can be resized while in use
* Snapshotted
    * Magical - pay for incremental ($ and time), but use/delete like full backups
* Not file-based NAS, but can mount to multiple instances if **all** are read-only
* Pay for GB/month depending on perf class. Pay for GB/month for snapshot

## Cloud SQL

* Fully managed, reliable MySQL and PostgreSQL databases (AWS RDS)
* supports automated replication, backup, failover
* scaling is manual (vertical and horizontal)
* pay for underlying GCE instances and PDs, plus baked-in service fees

## Cloud Spanner

* Fully horizontally scalable, strongly consistent, relational database service
    * up to thousands of nodes, a node is a server in each replication location
* Choose consistency, partition-tolerance out of (CP or CAP theorem) - give up some availability
* Still very high availabiity (99.999%) for multi-region
    * not based on fail-over
* pay for provisioned node time (by region/multi-region) plus used storage-time
* Very expensive for very large systems

## BigQuery (BQ)

* Multi-regional
* Serverless column-store data warehouse for analytics using SQL (kind of like Redshift or more like Athena)
* Pay for GBs acually considered (scanned) during queries
    * Caches query results for 24 hours which are free
* Pay for data stored (GB-months)
    * cheaper if table is not modified for 90 days
* Pay for GBs added via streaming inserts

## Cloud Bigtable

* low latency & high throughput NoSQL DB for large operational & analytical apps (kind of like DynamoDB)
* supports Apache HBase API, integrates with Hadoop, Dataflow, Dataproc
* Scales seamlessly and unlimitedly
    * storage autoscales
    * processing nodes scaled manually
    * pay for processing node hours
    * pay for GB-hours for storage (HDD or SSD)

## Cloud Datastore

* managed & autoscaled NoSQL DB with indexes, queries, and ACID transaction support (more like DynamoDB)
* NoSQL
    * No joins or aggregates, must line up with indexes
    * NOT, OR and NOT EQUALS operations are not natively supported
* Automatic built-in indexes for simple filtering and sorting (ASC, DESC)
* Manual composite indexes for more complicated, but be aware of "exploding"
* Pay for GB-months for storage used
* Pay for IO operations performed

## Firebase Realtime DB & Cloud Firestore

* NoSQL document stores with almost real time client updates via managed websockets
* A Single huge JSON document, located only in central US
* Firestore has collections, documents, and contained data
* Free tier (spark), flat tier (flame), usage-based pricing (blaze)
    * realtime DB: pay more for GB/month stored and GB downloaded
    * firestore: pay for operations and less for storage and transfer

## Cloud Storage (GCS)

* Regional and multi-regional
* Infinately scalable, fully-managed, versioned, and highly durable object storage (S3)
* designed for 11 9s of durability
* strongly consistent (even for overwrite PUTs and DELETEs)
* integrated site hosting and CDN functionality
* lifecycle transitions across classes (multi-regional, regional, nearline, coldline)
    * diffs in cost & availability, not latency (no thaw delay)
* All classes have same API
* Pay for operations and GB-months stored by class + GBs retrieved for nearline & coldline

## Data Transfer Appliance

* Rackable, high-capacity storage server to physically ship data to GCS (snowball)
* Ingest only. cannot get egress
* 100TB or 480TB versions

## Storage Transfer Service

* Global 
* Copies objects without manual setup
* destination is a GCS bucket
* source can be S3, HTTP/HTTPS or other GCS bucket
* one-time or scheduled recurring transfers