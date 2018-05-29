# 

PHP有对并发访问的支持：curl_multi_init


```
function requestHash($url, $p, $method)
{
    $url = strtolower(trim(trim($url), '&?/\\'));
    $phash = $this->arrayHash($p);
    $method = strtolower(trim($method)) == 'post' ? 'post' : 'get';
    return md5($url . $phash . $method);
}

function arrayHash($p, $filter = array('mdstr', 'expire'))
{
    $para_sort = array();
    foreach ($p as $k => $v) {
        if ($filter && in_array($v, $filter, true)) continue;
        // array object bool int float null resource...
        $para_sort[$k] = is_array($v) ? $this->arrayHash($v)
            : (is_object($v) ? $this->arrayHash((array)$v) : strval($v));
    }
    ksort($para_sort);
    return md5(http_build_query($para_sort));
}
```

当我们去主动获取请求结果时，如果当前请求已经执行完成，会立即返回请求结果，其他还没执行完的请求继续执行，不堵塞业务流程。如果当前请求没执行完，会堵塞直到当前请求执行结束。

## 相关库
https://github.com/jmathai/php-multi-curl