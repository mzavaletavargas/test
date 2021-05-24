---
id: 8a285efb-1044-43b2-b86f-904ad3bf48fc
title: Databases
desc: ""
updated: 1621709646409
created: 1621707701484
stub: false
---

## Introduction

- NoSql database
- Unlimited Concurrent Read/Write
- DAX for improve speed

## Basic relational concepts

- Data is a collection.
- Database organize of this collection.
- Rows/Columns.
- Primary key identify each row.
- Foreign key reference data from other tables.
- Scale adding ram cpu, etc.

### Normalization

- Organize data

- Eliminate redundant data

- Advantages

  - | name | courseId1 | courseName1 | courseId2 | courseName2 |
    | ---- | --------- | ----------- | --------- | ----------- |
    | foo  | 3         | Math        | 4         | Science     |
    | bar  | 3         | Math        |           |             |
    | test | 4         | Science     | 3         | Math        |

  - 1NF: deleting repeating groups, single value attribute

    - | name | courseId | courseName |
      | ---- | -------- | ---------- |
      | foo  | 3        | Math       |
      | foo  | 4        | Science    |
      | bar  | 3        | Math       |
      | test | 4        | Science    |
      | test | 3        | Math       |

  - 2NF: deleting redundant data

    - | studentId | studentName |
      | --------- | ----------- |
      | 1         | foo         |
      | 2         | bar         |
      | 3         | test        |

    - | courseId | courseName |
      | -------- | ---------- |
      | 3        | Math       |
      | 4        | Science    |
      | 3        | test       |

    - | relationId | courseId | employeId |
      | ---------- | -------- | --------- |
      | 0001       | 3        | 1         |
      | 0002       | 4        | 1         |
      | 0003       | 3        | 2         |
      | 0004       | 3        | 3         |
      | 0005       | 4        | 3         |

  - 3NF: not transitive dependencies

    -

- Downside:

  - Computing
  - SQL queries complex

### NoSQL Basic Concepts

- Support unstructured data
- Big data apps
- scale horizontally adding more machines, partitions
- Object Based APIs for interaction

## Types of NoSQL

- Columnar database
  - Analytics
  - loaded from disk
  - redshif
- Key-value store
  - Socual networking
  - Media
  - fast access
  - redis, dynamodb
- Graph Database
  - trees
  - Neo4j
- Document Database
  - Json or objects
  - kasandra
  - mongodb
  - couchdb

## ACID

- Atomicity: transaction can execute completely or not at all.
- Consistency: data written should be valid according to all defined rules.
- Isolation: Although there is high concurrency, each transactions should be treated 1 by 1
- Durability: once data has been committed should remain even having system failures
