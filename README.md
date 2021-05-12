# httpErrorPage
![](https://img.shields.io/github/languages/code-size/n0099/httpErrorPage.svg)
![](https://img.shields.io/github/downloads/n0099/httpErrorPage/total.svg)
![](https://raw.githubusercontent.com/n0099/httpErrorPage/master/404.gif)

基于[Hacker themed error page](https://codepen.io/robinselmer/pen/vJjbOZ)修改而来的自定义HTTP错误页

支持以下状态码：
* 401 Unauthorized
* 403 Forbidden
* 404 Not Found
* 500 Internal Server Error
* 502 Bad Gateway

其他状态码请自行填充模板

* 文字闪烁效果来自https://codepen.io/lbebber/pen/ypgql
* 错误中文描述来自IIS 8自带错误页（位于C:\inetpub\custerr\zh-CN）

# Installation
## apache
```apache
ErrorDocument 401 /401.html;
ErrorDocument 403 /403.html;
ErrorDocument 404 /404.html;
ErrorDocument 500 /500.html;
ErrorDocument 502 /502.html;
```

## nginx
```nginx
error_page 401 /401.html;
error_page 403 /403.html;
error_page 404 /404.html;
error_page 500 /500.html;
error_page 502 /502.html;
```

## WordPress
如果你使用WordPress且url位于域名根目录，一般情况下所有请求都会转发给WP的index.php处理，从而由WP主题而非webserver来返回404页
因此请修改`wp-content\themes\当前使用主题名\404.php`内容为
```php
<?php
readfile('/path/to/your/404.html');
exit;
```
