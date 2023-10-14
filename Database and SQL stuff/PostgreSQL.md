## List schemas

Use `\dn`

```
postgres=# \dn
 List of schemas
 Name   |  Owner
--------+----------
 public | postgres
(1 row)
```

## Drop all tables

Find the schema name:
```
postgres=# \dn
 List of schemas
 Name   |  Owner
--------+----------
 public | postgres
(1 row)
```

Drop the schema
```
drop schema public CASCASE;
```
### List tables (using SELECT command)

```sql
SELECT * FROM pg_catalog.pg_tables
WHERE schemaname != 'information_schema' AND
schemaname != 'pg_catalog';
```

## List all indexes

credit: https://www.postgresqltutorial.com/postgresql-indexes/postgresql-list-indexes/

```
SELECT
    tablename,
    indexname,
    indexdef
FROM
    pg_indexes
WHERE
    schemaname = 'public'
ORDER BY
    tablename,
    indexname;
```