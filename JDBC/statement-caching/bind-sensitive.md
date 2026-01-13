## Bind-sensitive execution plans

`status` column
with three distinct values:
`TO_DO`, `DONE`, and `FAILED`.

1000 `TO_DO` entries,
95000 `DONE`,
4000 `FAILED`.

The lower the selectivity,
the fewer rows
are matched
for a given
bind value.

Optimizer prefer
sequential scans
over index lookups
for high selectivity percentages,
to reduce
total number of
disk-access roundtrips,
especially
when data is
scattered among
multiple data blocks.
___
### Demo

Searching for
`DONE` entries:

```sql
SQL> EXPLAIN SELECT * FROM task WHERE status = 'DONE' LIMIT 100;

Limit (cost=0.00..1.88 rows=100 width=13)
-> Seq Scan on task (cost=0.00..1791.00 rows=95080 width=13)
    Filter: ((status)::text = 'DONE'::text)
```

`TO_DO` or `FAILED`:

```sql
SQL> EXPLAIN SELECT * FROM task WHERE status = 'TO_DO' LIMIT 100;

Limit (cost=0.29..4.25 rows=100 width=13)
-> Index Scan using task_status_idx on task (cost=0.29..36.16 rows=907)
    Index Cond: ((status)::text = 'TO_DO'::text)

SQL> EXPLAIN SELECT * FROM task WHERE status = 'FAILED' LIMIT 100;

Limit (cost=0.29..3.86 rows=100 width=13)
-> Index Scan using task_status_idx on task (cost=0.29..143.52 rows=4013)
    Index Cond: ((status)::text = 'FAILED'::text)
```