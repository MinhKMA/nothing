- Code 

```
$sql="SELECT * FROM security.users WHERE id=($id) LIMIT 0,1";
```

- Tương tự các bước less 54 nhưng thay thế  `'` thành `)`

```
http://10.10.10.171/sqli-labs/Less-55/?id=1) ORDER BY 3 --+
```
