
####　log_agent
这个配置就是往redis队列中塞入日志就行。output的位置设置为redis就行。
```
input {
    file {
            type => "nginx_access"
            path => ["/mnt/logs/api.yejianfeng.com.logstash.log"]
    }
}
output {
    redis {
            host => "10.173.xx.xx"
            port => 8001
            password => pass
            data_type => "list"
            key => "logstash:redis"
    }
}
```
####　log_indexer
input: 负责从redis中获取日志数据
filter: 负责对日志数据进行分析和结构化
output: 负责将结构化的数据存储进入elasticsearch