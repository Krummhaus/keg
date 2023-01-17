# Iterate trough all tables and operate on them

Using:
- [for-loop](https://www.geeksforgeeks.org/postgresql-for-loops/)
- [format-function](https://www.geeksforgeeks.org/postgresql-format-function/)
- `~` operator for regexp finding

```sql
do
$$
declare
   tbl text;
begin
        for tbl in select tablename from pg_tables
                where tablename ~ '^s_\d+.*' and schemaname = 'public'
        loop
                --raise notice 'TAB: %', tbl;
                execute format('alter table %I add column segment integer default 0', tbl);
        end loop;
end;
$$;
```

Tags:
    #pgsql #for-loop #postgre
