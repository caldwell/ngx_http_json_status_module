ngx_http_json_status_module
===========================

** 開発中 **

仕様
----
nginxのstatusをjson形式で返却するモジュール

### ディレクティブ
```
syntax:	 status;
default: none;
context: location
```

### response
```json
{
    "version": 1,
    "nginx_version": "1.5.3",
    "address": "127.0.0.1",
    "timestamp": 1377263206961,
    "connections": {
        "accepted": 80399,
        "dropped": 0,
        "active": 1,
        "idle": 1
    },
    "requests": {
        "total": 80399,
        "current": 1
    },
    "upstreams":{
        "upstream_servers": [
            {
                "server": "127.0.0.1:1081",
                "state": "up",
                "weight": 1,
                "backup": false,
                "active": 0,
                "keepalive": 0,
                "requests": 470,
                "fails": 0,
                "unavail": 0,
                "downstart": 0,
                "sent": 78020,
                "received": 2350,
                "downtime": 0,
                "responses": {
                    "1xx": 0,
                    "2xx": 470,
                    "3xx": 0,
                    "4xx": 0,
                    "5xx": 0,
                    "total": 470
                },
                "health_checks": {
                    "checks": 0,
                    "fails": 0,
                    "unhealthy": 0
                }
            },
        ...
        ],
    }
}
```

組み込み
--------
```bash
./configure --add-module=./ngx_http_json_status_module
```

設定例
------
```
server {
  ...
  location = /status {
    status;
  }
}
```

参照
----
* [module guide](http://www.evanmiller.org/nginx-modules-guide.html)
* [nginx plus](http://nginx.com/products/)
* [nginx plus tips](http://qiita.com/harukasan/items/5123f797a876696b343e)
* [nginx status](http://nginx.org/en/docs/http/ngx_http_status_module.html)
* [build nginx](BUILD.md)
* [開発手順(未)](PROCEDUREofDEVELOPEMENT.md)
