# debezium-server-iceberg-rest-minio-trino
Ingest real-time data from PostgreSQL to Minio in Iceberg table format using Debezium Server and access the data using Trino

Inspired by https://github.com/memiiso/debezium-server-iceberg/tree/master, I did some modif. Use REST instead of JDBC as Iceberg Catalog.

Tested and worked:
 - Insert new data to source db (PostgreSQL), captured by debezium and written to Minio in Iceberg table format
 - Update existing data to source db (PostgreSQL), captured by debezium and written to Minio in Iceberg table format
 - Create new schema using Trino
 - Create new table using Trino
 - Insert data using Trino
 - Read data using Trino
 - Update data using Trino
 - Delete data using Trino
 - Drop Table using Trino

## Use this for Trino connection in DBeaver
![image](https://github.com/user-attachments/assets/828819f8-4305-42c7-9a86-186a4377d694)

## Some Trino queries to get started with

```sql
CREATE SCHEMA iceberg.staging;
```
```sql
CREATE TABLE iceberg.staging.orders (
    id INT,
    name VARCHAR,
    created_at TIMESTAMP
)
with (
	location = 's3a://warehouse/staging/orders');
```
```sql
insert into iceberg.staging.orders (id, name, created_at)
values (1, 'abed', current_timestamp);
```
```sql
select * from iceberg.staging.orders; 
```
```sql
drop table iceberg.staging.orders;
```

> **Note**: Ideally, data in Raw schema should only be controlled by any activities in the source db. If you want to do something with the data from Raw schema, create another schema and do it there.
