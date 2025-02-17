---
id: 3e389eed-da91-4a54-bd83-2645161e58e0
title: Dynamodb
desc: ""
updated: 1626054210304
created: 1621709312456
---

## General Overview

- [performance-metrics](https://www.datadoghq.com/blog/top-dynamodb-performance-metrics/)
- [11-things-before-start](https://blog.yugabyte.com/11-things-you-wish-you-knew-before-starting-with-dynamodb/)
- [dynamo-is-not-for-everybody](https://read.acloud.guru/why-amazon-dynamodb-isnt-for-everyone-and-how-to-decide-when-it-s-for-you-aefc52ea9476?gi=d300d4ccd949)
- [back-to-rds](https://blog.codebarrel.io/why-we-switched-from-dynamodb-back-to-rds-before-we-even-released-3c2ee092120c?gi=b30f9bb06d99)
- [understanding-scaling-behaviour](https://theburningmonk.com/2019/03/understanding-the-scaling-behaviour-of-dynamodb-ondemand-tables/)

## Basics

![image-20191124220520552](/assets/images/image-20191124220520552.png)

![image-20191124222012419](/assets/images/image-20191124222012419.png)
![](/assets/images/2021-07-09-23-25-02.png)

## Tables

- name.other or name_other name convention
- no foreign keys on different tables
- tables are independents
- Strict ACID

## Data Types

- Scalar Types
  - String
  - Number
  - Boolean
  - Binary
  - Null
- Document Types
  - Lists []
  - Maps: key-values map automatically to dynamo DB JSON

## Consistency Model

![image-20191124223816308](/assets/images/image-20191124223816308.png)

Dynamo read consistency can be

- Strong: most up-to-date

- Eventual: first, 50% cheaper (default)

## Capacity Units

RCUs WCUs

1 partition can handle 1000 WCUs or 3000 RCUs

## Partitions

- up to 10 GB

- depends on provisioned capacity

- ![image-20191124225317460](/assets/images/image-20191124225317460.png)

- Not be deleted if is modified

## Indexes

Hashing algorithm

### Secondary Indexes

- Local secondary Index

- Global secondary Index

## Should you use DynamoDB

![deicision Tree](/assets/images/decision-tree.png)

## Best Practices

- Consistent Hashing ?

### Partition cases

![image-20191126143924334](/assets/images/image-20191126143924334.png)

More database size will need to modify the provision capacity.

Is recommended to move data base on frecuency, so we can have tables that store data wi less R/W capacity yhan others. This can be a cost bases solution.

Present an example of migration to have the provition capacity and then lower it down.
When doing that since there was created many partitions during the migration process and then when lowering down, we found out that the Read and Write capacity is smaller for each partititons since the provision capacity is divided in the number of partitions.

Dynamodb does not allocate everything or reduce in 1 partitions. partitions will remain. Increasing our cost 6 times

The best practice will be to distribute data using ´partition key to write simultanipously on dynamodb.

### DynamoDb keys

Primary keys

stay away scan operations

filters are made after the data was getted

max local secondary indexes: 5

global seco

![image-20191126153939760](/assets/images/image-20191126153939760.png)

### Hot keys or Partitions

Hot keys: when certain keys has information that is going to use data from 1 partition often thatn others for example when we get recent data.

We can move recent data to other table.

or use DAX as cache

### Design patterns

![image-20191126171249941](/assets/images/image-20191126171249941.png)

## Summary

DynamoDB offers a bunch of features that you can use to start an application with minimal set up. Worry less about scaling, sharding, and put your application running in short time. Also you are in AWS Ecosystem that can bring many benefits. For large-scale applications, there is some things to take into consideration.

- An really good estimation of R/W operatations for our database. In other words be able to predict concurrency and storage which impacts in the **provision capacity** that we need to set up at the beginning, we can modify it later but we can get into unexpected incresing in costs and slowing down every partition created since the **provision capacity** will be divided on each one.
- Be able to predict how to deal with **hot keys and partitions**, In case we have keys refering data that will be used often than others will end up on using a single partition instead of all tje partitions available. Increasing cost, and delay. As a solution you can "archived" some data and move it to other table, in that way you will only worry for the latest data. This startegy needs planning and play with a lot of variables.
- There is an alternative that Amazon provides adding a layer Using DAX, with it you can redirect incomming request in a way that can lower down the consuption of a single partition and distribute incomming R/W operations over all partitions. This alternative will increase the cost for being an aditional service.
- queries stron cosnistency and eventually reads
- index
- tenancy
- chech wiki adsk

## Usefull Links

- [performance-metrics](https://www.datadoghq.com/blog/top-dynamodb-performance-metrics/)
- [11-things-before-start](https://blog.yugabyte.com/11-things-you-wish-you-knew-before-starting-with-dynamodb/)
- [dynamo-is-not-for-everybody](https://read.acloud.guru/why-amazon-dynamodb-isnt-for-everyone-and-how-to-decide-when-it-s-for-you-aefc52ea9476?gi=d300d4ccd949)
- [back-to-rds](https://blog.codebarrel.io/why-we-switched-from-dynamodb-back-to-rds-before-we-even-released-3c2ee092120c?gi=b30f9bb06d99)
- [understanding-scaling-behaviour](https://theburningmonk.com/2019/03/understanding-the-scaling-behaviour-of-dynamodb-ondemand-tables/)

- Youtube: [AWS re:Invent 2018: Amazon DynamoDB Deep Dive: Advanced Design Patterns for DynamoDB (DAT401)
  ](https://www.youtube.com/watch?v=HaEPXoXVf2k)

let's say that you are forced to increase the PC to handle more R/W operations during black friday and return to the previous value after that event, as a result you will end up with more partitions which is fine when the value was higher but the we can
