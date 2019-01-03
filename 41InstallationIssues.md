## 安装问题

了解如何解决安装过程中的PHP问题

### PHP配置

大部分安装问题都是因为资源限制，比如在一个共享服务器上。如果需要的话，您应该检查[PHP配置设置](http://www.php.net/manual/en/ini.core.php)。

|设置|说明|
|-------|-----------|
|*post_max_size*|使用post方法在单个表单提交中数据的最大尺寸。|
|*upload_max_filesize*|上载单个上载文件的最大文件大小。|
|*max_execution_time*|在解析器终止脚本之前，允许脚本运行的最长执行时间（秒）。|
|*memory_limit*|允许脚本分配的内存量（以字节为单位）。|

您可能需要通过直接修改*php.ini*文件为php分配更多的资源。如果不可能，可以尝试通过Web服务器上的 *.htaccess* 文件设置PHP设置。尽管这也取决于您的服务器是否允许使用 *.htaccess* 重写。

要通过php.ini文件更改php配置，请使用以下语法

```
# example of recommended settings
post_max_size = 8M
upload_max_filesize = 8M
max_execution_time = 60
memory_limit = 128M

```

使用*.htaccess* 文件设置时，使用以下语法

```
# example of recommended settings
php_value post_max_size 8M
php_value upload_max_filesize 8M
php_value max_execution_time 60
php_value memory_limit 128M
```