# Grant privileges to user in Postgres `psql`

Using `\z <table>` we can se privileges on table with psql CLI.  
Another way is to use `\dp <table>`.  
With command `grant all on <table> to <user>;`.  
Or specify `grant select, update, insert on <table> to <user>;`   

```sql
-- postgresql docs
rolename=xxxx -- privileges granted to a role
        =xxxx -- privileges granted to PUBLIC

            r -- SELECT ("read")
            w -- UPDATE ("write")
            a -- INSERT ("append")
            d -- DELETE
            D -- TRUNCATE
            x -- REFERENCES
            t -- TRIGGER
            X -- EXECUTE
            U -- USAGE
            C -- CREATE
            c -- CONNECT
            T -- TEMPORARY
      arwdDxt -- ALL PRIVILEGES (for tables, varies for other objects)
            * -- grant option for preceding privilege

        /yyyy -- role that granted this privilege

/* pslq example using `\dp s_help_segments`
                                     Access privileges
 Schema |      Name       | Type  |    Access privileges    | Column privileges | Policies
--------+-----------------+-------+-------------------------+-------------------+----------
 public | s_help_segments | table | postgis=arwdDxt/postgis |                   |
*/
```

Related:  
    (postgresql.org)[https://www.postgresql.org/docs/9.1/sql-grant.html]  
    (DigitalOcean Tutorial)[https://www.digitalocean.com/community/tutorials/how-to-use-roles-and-manage-grant-permissions-in-postgresql-on-a-vps-2]  

Tags:  
    #psql #pgsql #permissions #privileges
