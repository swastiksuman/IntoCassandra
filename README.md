#DDL
CREATE TABLE emp (
    emp_id int PRIMARY KEY,
    emp_city text,
    emp_name text,
    emp_phone varint,
    emp_sal varint
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
