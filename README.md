# Knex ClickHouse dialect

ClickHouse dialect for Knex.js

## Install

```bash
npm install @march_ts/knex-clickhouse-dialect
```

## Usage

```js
import knex from 'knex';
import clickhouse from '@march_ts/knex-clickhouse-dialect';

export default knex({
    client: clickhouse,
    connection: () => {
        return 'clickhouse://login:password@localhost:8123/db_name';
    },
    // optional migrations config
    migrations: {
        directory: 'migrations_clickhouse',
        disableTransactions: true,
        disableMigrationsListValidation: true,
    },
});
```

## Migration

Currently the migration default enging is MergeTree. If you want to use other enging, you can use the `table.engine` function to change the enging.

## Warning 

- MergeTree Family Enging need to have a primary key, the primary can be assing using `table.primary` function, or can be assign in column using .primary() function or else default is "id" column.

### MergeTree Family Enging
- on update data, please note that the primary key is immutable, DO NOT put primary key into entity for update data. or use insert then optimize table.



## Testing Compatibility

### Enging Migration

MergeTree

-   [x] MergeTree
-   [ ] ReplacingMergeTree,
-   [ ] SummingMergeTree
-   [ ] AggregatingMergeTree
-   [ ] VersionedCollapsingMergeTree
-   [ ] CollapsingMergeTree

Log

-   [ ] TinyLog
-   [ ] StripeLog
-   [ ] Log

Others Enging

-   [ ] Memory
-   [ ] Distributed
-   [ ] View, MaterializedView
-   [ ] Dictionary
-   [ ] File, URL
-   [ ] Buffer
-   [ ] Kafka, RabbitMQ
-   [ ] ODBC, JDBC, MySQL, PostgreSQL, HDFS

