|Status Code|Message||
|---|---|---|
|200|Created||
|201|successful||
|204|No Content|No data need to send back|
|400|bad request||
|401|Unauthorized||
|403|Forbidden||
|404|Not Found||
|409|Conflict||
|500|Internal Server Error||

### filtering

```
http://<domain>/api/v1/users?age=100&gender=male
```

### gte

```
http://<domain>/api/v1/tours?duration[gte]=5
```

### sort

- ascending order
```
http://<domain>/api/v1/tours?sort=price
```

- decending order
```
http://<domain>/api/v1/tours?sort=-price
```