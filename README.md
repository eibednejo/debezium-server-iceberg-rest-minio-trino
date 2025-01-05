# debezium-server-iceberg-rest-minio-trino
Ingest real-time data from PostgreSQL to Minio in Iceberg table format using Debezium Server and access the data using Trino

Inspired by https://github.com/memiiso/debezium-server-iceberg/tree/master.

Tested and worked:
 - Insert new data to source db (PostgreSQL), captured by debezium and written to Minio
 - Update existing data to source db (PostgreSQL), captured by debezium and written to Minio
 - Read data in Minio using Trino
 - Update data in Minio using Trino
 - Delete data in Minio using Trino
