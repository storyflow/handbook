
## 概念
OpenResty是一个基于 nginx 与 Lua 的高性能 Web 平台，其内部集成了大量精良的 Lua 库、第三方模块以及大多数的依赖项。用于方便地搭建能够处理超高并发、扩性极高的动态 Web 应用、Web 服务和动态网关。

## 安装
```
$ wget https://openresty.org/download/openresty-1.11.2.5.tar.gz
$ tar -xzvf openresty-1.11.2.5.tar.gz
$ cd openresty-1.11.2.5
$ ./configure --prefix=/opt/openresty \
            --with-luajit \
            --without-http_redis2_module \
           --with-http_iconv_module
$ make && make install
```

## 示例
```
location /lua {
            default_type text/html;
            content_by_lua_block {
                ngx.say("<p>hello, world</p>")
            }
        }
```
