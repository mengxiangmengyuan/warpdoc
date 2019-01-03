## 设置部分

此部分允许您控制主题的行为和整体外观。

### 风格

样式部分包含自定义项。单击 *Customizer* 按钮添加您自己的样式或修改现有样式。加载自定义器后，您可以轻松自定义主题的颜色、字体、页边距甚至更多设置。自定义程序只保存修改过的变量，并自动将它们编译成CSS。

有关更多信息，请查看**自定义**教程。

### 开发

1. LESS 开发者模式

选中第一个选项，浏览器会在每次加载页面时自动通过Javascript编译LESS文件。这提供了一个适当的测试环境。不建议在实际站点上启用开发者模式，因为持续编译过程效率很低。

2. 动态风格

第二个选项允许浏览器按URL加载样式。如果你想为你的网站测试不同的风格，这很有用。当您的网站上线时，禁用此选项。

3. 编译 LESS 到 CSS

要完成 LESS 的修改，请单击*编译LESS*按钮，所有更改都将编译到最终的CSS中。

*重要提示*：确保您没有在 */styles/STYLE-NAME/css* 文件夹中进行开发，因为只要单击*LESS编译*按钮，这些文件夹就会被覆盖。

### 压缩

要优化页面加载时间，请选择以下压缩选项之一。

| 设置                                | 说明                                                                                                |
| ----------------------------------- | --------------------------------------------------------------------------------------------------- |
| None                                | 所有文件都不会单独加载并完全调整大小                                                                |
| *Combination+Minify*                | 此选项将最小化CSS和Javascript文件并将其组合为一个文件                                               |
| *Combination+Minify+Data URIs*      | Data URI 将图像数据直接嵌入到文档中，从而减少了对图像文件的HTTP请求。这仅适用于最大大小为10kb的图像 |
| *Combination+Minify+Data URIs+Gzip* | Gzip允许通过压缩数据包更快地传输数据，而不是通过单独发送来处理大数据量                              |

### 响应式

视区元标记控制移动浏览器上的布局。如果没有设置，手机上的默认宽度是980px，网站看起来与台式机上的相同。

### Bootstrap

通过选中此选项，可以禁用**Bootstrap**。当你只使用 Joomla 的博客和文章时，这样减少了页面加载时间。

### 内容

启用或禁用**向上**按钮和**Warp**标记。

### 社交按钮

要允许用户与其他人共享文章，请激活*社交按钮*选项。它在文章下面插入小部件。这些是通过*Twitter*、*Facebook*或*Google+*上的Javascript加载的。

### 模块

为特定位置设置默认模块样式。

*注意*：一旦在**模块设置**中为单个模块选择样式，此样式将被覆盖。

### 额外的脚本

您可以在这里插入其他的脚本，如下面的谷歌分析跟踪代码。它将添加到主题中的结束正文标记之前。

```

var _gaq = _gaq || [];
  _gaq.push(['_setAccount', 'UA-XXXXX-X']);
  _gaq.push(['_trackPageview']);

  (function() {
    var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
    ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
    var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
  })();

```

有关更多信息，请参阅谷歌分析教程。