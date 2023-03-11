```
http://kb.avinetworks.com/2016/03/01/http-basic-auth-for-api-queries/
curl --user admin:xxxxx  --insecure -H "Accept: application/json" -X GET https://controller161/api/virtualservice/
curl --user admin:xxxxx  --insecure -v -H "Content-Type: application/json" -X POST -d @test.json https://controller161/api/pool/
curl --user admin:xxxxx  --insecure -v -H "Content-Type: application/json" -X POST --data @test2.json  https://controller161/api/healthmonitor
```
test.json
```
{
  "name": "Hello_REST_pool",
  "servers": [
    {
      "ip": {
        "type": "V4",
        "addr": "10.130.161.11"
      }
},
{
      "ip": {
        "type": "V4",
        "addr": "10.130.161.12"
      }
}
  ]
}
```

test2.json
```

{
    "receive_timeout": 4, 
    "name": "http-hmon", 
    "failed_checks": 3, 
    "send_interval": 10, 
    "http_monitor": {
        "http_request": "GET / HTTP/1.0", 
        "http_response_code": [
            {
                "code": "HTTP_2XX"
            }
        ]
    }, 
    "type": "HEALTH_MONITOR_HTTP"
}
```
