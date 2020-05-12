# CURL and HTTP Headers

# 1.download the file use curl 

1.baseic useage 

```
curl http://example.com --output my.file
```

2.make curl slient

```
curl http://example.com --output my.file --silent
```

3.shortened options

```
curl -s -o my.file http://example.com
```

4.limit rate 

```
curl --limit-rate 200K -O http://example.com/my.file
```

5.Resuming a download

```none
curl -C - -O http://example.com/my.file
```

# 2.curl http request method

1.returning only the HTTP headers of URL

```
curl -I http://httpbin.org
```

2.GET method

```
curl   --request GET httpbin.org/get
```

3.POST method

```
curl   --request POST httpbin.org/post
```

4.make curl request with data

```none
curl -X POST http://www.example/login/ -d 'username=yourusername&password=yourpassword'
```

