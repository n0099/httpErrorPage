# httpErrorPage
![](https://img.shields.io/github/languages/code-size/n0099/httpErrorPage.svg)
![](https://img.shields.io/github/license/n0099/httpErrorPage.svg)

基于[Hacker themed error page](https://codepen.io/robinselmer/pen/vJjbOZ)修改而来的自定义HTTP错误页
支持以下状态码：
* 401 Unauthorized
* 403 Forbidden
* 404 Not Found
* 500 Internal Server Error
* 502 Bad Gateway

其他状态码请自行填充模板

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
    location = /error/404.html {
        internal; # 直接访问/error/404.html时仍可返回404状态码，用于搭配Wordpress 404页重定向，详见http://nginx.org/en/docs/http/ngx_http_core_module.html#internal
    }
```
## Wordpress
如果你使用Wordpress且url位于域名根目录，所有请求都会转发给WP的index.php处理从而由WP主题而非webserver返回404页

请修改`wp-content\themes\当前使用主题\404.php`内容为以302重定向至404页
```php
<?php
wp_redirect('https://example.com/404.html');
```
不想保留[软404](https://support.google.com/webmasters/answer/181708?hl=zh-Hans)请查看上方nginx状态码注释

# Acknowledgment
* 文字闪烁效果来自https://codepen.io/lbebber/pen/ypgql
* 错误中文描述来自IIS 8自带错误页（位于C:\inetpub\custerr\zh-CN）
* [中科大Google Fonts镜像CDN](fonts.lug.ustc.edu.cn)
