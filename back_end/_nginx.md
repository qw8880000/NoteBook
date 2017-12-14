
# location

```
Syntax:	location [ = | ~ | ~* | ^~ ] uri { ... }
location @name { ... }
Default:	—
Context:	server, location
```

* `~` 与 `~*` 表示使用正则表达式，其中`~*`对大小写不敏感。
* `^~` 表示不使用正则表达式。
* `=` 用于精确匹配。


```
location /i/ {
    alias /data/w3/images/;
}
```
与
```
location /i/ {
    root /data/w3;
}
```
