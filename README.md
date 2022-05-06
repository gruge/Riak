<p align="center">
<img width="400" height="400" src="img/riak.png">
</p>

# Riak overview
a simple run-through of Riak features and usage

## Table of contents:
1. [What does Riak Mean?](#what-does-riak-mean)
    1. [The advantages](#the-advantages)
    2. [Pros of Riak](#pros-of-using-riak)
    3. [Cons of Riak](#cons-of-using-riak)
2. [Influences](#influences)
    1. [CAP Theorem](#cap-theorem)
    2. [Amazon's Dynamo Paper](#amazons-dynamo-paper)
    3. [Experience running large networks](#experience-running-large-networks-akamai)
4. [Map/Reduce Terms](#map-reduce-terms)
5. [Map/Reduce Overview](#map-reduce-overview)
6. [Map Phase](#map-phase)
## What Does Riak Mean?
Riak is an open-source, Web scalable distributed database based on the NoSQL and Dynamo database system. It is developed by [Basho Technologies](https://riak.com/).

Riak is highly distributed database software that provides scalable, reliable performance in variety of different operation environments. 
 ### The advantages
 - Availability
 - Operational simplicity
 - Scalability
 - Masterless
 - Key/Value store
 - Document-oriented Database
 - Web-shaped storage

 ### Pros of using Riak
 - __Highly available:__ If nodes go offline for any reason, the system still operates.

 - __Highly scalable:__ There is a minimum of 5 nodes, which can handle a lot by themselves. When scaling is required, it can be done easily, with minimal to no downtime on large scales.

 - __Fast searching:__ Riak has SOLR indexing built-into the core product, which makes querying for data very fast.

 - __Schemaless design:__ Riak makes it really easy to apply whatever design you like. Since you're not locked into seeing things just the SQL way, you've got more freedom with the type of data you store and the way you store it.

 ### Cons of using Riak
 - __Indexing:__ When the index definition changes, reindexing takes an extremely long time.
  
 - __Dead data resurrection:__ The deletes seem to reappear weeks, even months, after the delete was issued, on rare occasions.

 - __Precise search:__ Currently there's no way to tell what data you have in Riak without already knowing a particular bucket/key. There is a way to list the keys for a given bucket but due to performance implications, this is not a viable method to lookup data. Especially when you have a large amount of keys in the bucket.

## Influences:

 ### CAP Theorem
 - __Consistent__ Reads and writes reflect a globally consistent system state
 - __Available__ System is available for reads and writes
 - __Partition tolerant__ System can handle the failure of individual parts
 
 ### Amazon's Dynamo Paper
 Keys | Meaning
--- | ---
 N | The number of replicas
 R | The number of replicas needed for a successful read
 W | The number of replicas needed for a successful write
 N - R | Read fault tolerance
 N - W | Write fault tolerance
 
 __N = 4,W = 2, R = 1__ </br>
 __4-2=2__ hosts can be down and __Riak__ can still perform writes </br>
 __4-1=3__ hosts can be down and __Riak__ can still perform reads 
 
 *N can vary per bucket* </br>
 *R and W can vary per operation*


 ### Experience running large networks (Akamai)

## Riak products:

 ### Riak KV
 __Riak KV__ is a distributed NoSQL database designed to deliver maximum data availability by distributing data across multiple servers. As long as your Riak KV client can  reach one Riak server, it should be able to write data.
 
 ### Riak TS
 __Riak TS__ is a distributed NoSQL key/value store optimized for time series data. With TS, you can associate a number of data points with a specific point in time. TS uses discrete slices of time to co-locate data. For example, humidity and temperature readings from a meter reported during the same slice of time will be stored together on disk.
 
 ### Riak CS
 __Riak CS__ is easy-to-use object storage software built on top of Riak KV, Riak’s distributed database. Riak CS is designed to provide simple, available, distributed cloud storage at any scale, and can be used to build cloud architectures—be they public or private—or as storage infrastructure for heavy-duty applications and services. Riak CS’s API is Amazon S3 compatible and supports per-tenant reporting for use cases involving billing and metering.

## Map/Reduce Terms
 Keys | Meaning
--- | ---
 Phase | A step within a job
 Job | A sequence of phases and inputs
 Map | Data collection phase
 Reduce | Data collation or processing phase
 
 ## Map/Reduce Overview
  - Map phases execute in parallel with data locality
  - Reduce phases execute in parallel on the node where job was submitted
  - Results are not cached or stored
  - Phases can be written in Erlang or Javascript

## Map Phase
 - Inputs must be bucket/key pairs
 - Must return a list
 - Parallel results are aggregated into a single list
