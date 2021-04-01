#Cassandra
Apache Cassandra is a highly scalable, high-performance distributed database designed to handle large amounts of data across many commodity servers, providing high availability with no single point of failure.

## Cassandra Features
* Horizontal Scaling
* Control over availability
* Faster Writes
* Transaction Support - No ACID support with rollback or mechanism

### How Cassandra transactions are different
Cassandra does not use RDBMS ACID transactions with rollback or locking mechanisms, but instead offers atomic, isolated and durable transactions. No support for joins or foreign keys.

Atomicity - When Cassandra writes, it replicates the write to all nodes. If the write fails on one node but succeeds on other, cassandra reports a failure to replicate. However the replicated write that succeds on other node is not rolled back automatically.

If multiple client sessions update the same columns in a row concurrently, the most recent update is the one seen by readers.

Isolation - All write, delete etc are performed in isolation, and are not visible to any other use until they are complete.

Durability - All writes to a replica node are recorded in memory and in commit log.

#DDL
CREATE KEYSPACE test
  WITH replication = {'class':'SimpleStrategy', 'replication_factor' : 1};

CREATE TABLE emp (
    emp_id int PRIMARY KEY,
    emp_city text,
    emp_name text,
    emp_phone varint,
    emp_sal varint
);

create table user (uid uuid primary key,
  first_name varchar,
  last_name varchar,
  department_id int
);

# DML
use test; (switch to keyspace)
insert into emp
  (emp_id, emp_city, emp_name, emp_phone, emp_sal)
  values
  (1, 'Hyderabad', 'Soujanya', 7299942232, 50000);
insert into emp
  (emp_id, emp_city, emp_name, emp_phone, emp_sal)
  values
  (2, 'Puri', 'Swastik', 7299942232, 50000);

insert into user
  (uid, department_id, first_name, last_name)
  values
  (now(), 1, 'Swastik', 'Panda');
