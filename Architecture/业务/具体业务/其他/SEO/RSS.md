# 站内UGC

## 要求
格式：一般为xml
提供内容：链接列表 或者 sitemap


## 内容处理正则表达式
```
只保留<p><img>标签
function dealContent($content) {
    $content = str_replace(array('<p>','</p>','<br/>', '<br />'),array("\n\r","\n\r","\n\r","\n\r"),$content);
    $content = preg_replace("/style=\"(.*?)\"/si","",$content);
    $content = preg_replace("/[\n\r]/i",'</p><p>',$content);
    $content = strip_tags($content,"<img><p>");
    $content = "<p>".$content."</p>";
    $content = str_replace(array('</p><p></p><p></p><p></p><p>', '</p><p></p><p></p><p>', '</p><p></p><p>'), array('</p><p>', '</p><p>','</p><p>'), $content);
    $content = str_replace('</p><p></p><p>','</p><p>', $content);
    $content = str_replace('<p></p>','', $content);
    return $content;
}
```
