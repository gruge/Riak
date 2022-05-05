[logo]: https://github.com/adam-p/markdown-here/raw/master/src/common/images/icon48.png "Riak"
# Riak overview
a simple run-through of Riak features and usage

## Table of contents:
1. [What does Riak Mean?](#what-does-riak-mean)
    1. [Pros of Riak](#pros-of-using-riak)
    2. [Cons of Riak](#cons-of-using-riak)
2. [Riak products]
    1. [Riak KV]
    2. [Riak TS]
    3. [Riak CS]
## What Does Riak Mean?
Riak is an open-source, Web scalable distributed database based on the NoSQL and Dynamo database system. It is developed by [Basho Technologies](https://riak.com/).

Riak is highly distributed database software that provides scalable, reliable performance in variety of different operation environments. 
 
 ### Pros of using Riak
 - __Highly available:__ If nodes go offline for any reason, the system still operates.

 - __Highly scalable:__ There is a minimum of 5 nodes, which can handle a lot by themselves. When scaling is required, it can be done easily, with minimal to no downtime on large scales.

 - __Fast searching:__ Riak has SOLR indexing built-into the core product, which makes querying for data very fast.

 - __Schemaless design:__ Riak makes it really easy to apply whatever design you like. Since you're not locked into seeing things just the SQL way, you've got more freedom with the type of data you store and the way you store it.

 ### Cons of using Riak
 - __Indexing:__ When the index definition changes, reindexing takes an extremely long time.
  
 - __Dead data resurrection:__ The deletes seem to reappear weeks, even months, after the delete was issued, on rare occasions.

 - __Precise search:__ Currently there's no way to tell what data you have in Riak without already knowing a particular bucket/key. There is a way to list the keys for a given bucket but due to performance implications, this is not a viable method to lookup data. Especially when you have a large amount of keys in the bucket.

## Riak products
