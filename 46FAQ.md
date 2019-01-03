## 常见问题解答

此页回答许多常见问题和已知问题。

如果你的主题有问题，这可能有很多原因。首先，主题设置中的内置系统检查将自动检测并通知您常见问题。

### 为什么我不能保存主题配置？

这可能是由于文件权限问题。有关详细信息，请参阅教程中的文件权限部分。

### 为什么重命名主题后无法保存主题配置？

重命名主题目录 */theme-name* 时，还需要调整主题的*templatedetails.xml*中设置的路径，以确保 *addpath* 属性与主题的目录匹配。
```
<fields name=“params” addfieldpath=“/templates/theme-name/…”>
```

### 为什么主题设置没有样式化？

这是由管理区域中的Javascript冲突引起的。很可能另一个jQuery库正由第三方扩展或插件加载。请阅读有关*Javascript错误*的文档以解决此问题。

### Javascript效果停止工作。怎么搞的？

如果您在Javascript效果方面遇到问题（例如，如果Accordion菜单停止工作），这可能是由于jQuery冲突造成的。有关更多信息，请阅读有关*Javascript错误的*教程。

### 为什么我的网站没有风格？

如果没有加载CSS，这可能是由于主题目录中的文件权限问题造成的。请看一下*文件权限教程*来解决这个问题。

### 我的网站只显示一个空白页。我应该恐慌吗？

没有理由惊慌。这很可能是由于一个PHP错误引发的。您需要在*php.ini*中启用[display_errors](http://www.php.net/manual/en/errorfunc.configuration.php#ini.display-errors)参数。这样，错误消息将显示在您的站点上，以便您可以检测到问题。

另一种检查PHP错误的方法是查看您的PHP错误日志。您的主机应该配置PHP将这些信息写入日志，而不是在屏幕上输出。

请查阅[本指南](https://coding.smashingmagazine.com/2011/11/20/a-guide-to-php-error-messages-for-designers/)，了解有关此主题的更详细的信息，以获取网页设计者的PHP错误消息。

### 为什么我总是得到验证错误？

像[W3C验证服务](https://validator.w3.org/)一样，验证程序可能会向您显示，根据其规范，新安装的主题不是100%有效的，因为它还没有识别广泛采用的现代标记，或者检测到它时遇到问题。