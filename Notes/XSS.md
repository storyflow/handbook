# XSS

## 定义
XSS 全称(Cross Site Scripting) 跨站脚本攻击， 是Web程序中最常见的漏洞。指攻击者在网页中嵌入客户端脚本(例如JavaScript), 当用户浏览此网页时，脚本就会在用户的浏览器上执行，从而达到攻击者的目的.  比如获取用户的Cookie，导航到恶意网站，携带木马等。

## CI框架中的处理

```
/**
 * Do Never Allowed
 *
 * @used-by CI_Security::xss_clean()
 * @param   string
 * @return  string
 */
protected function _do_never_allowed($str)
{
    $str = str_replace(array_keys($this->_never_allowed_str), $this->_never_allowed_str, $str);
    foreach ($this->_never_allowed_regex as $regex)
    {
        $str = preg_replace('#'.$regex.'#is', '[removed]', $str);
    }
    return $str;
}
```

## 参考资料

* [Web安全测试之XSS](http://www.cnblogs.com/TankXiao/archive/2012/03/21/2337194.html)