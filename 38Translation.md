## 翻译

本章将向您展示如何翻译基于Warp的主题。

已经有很多不同的语言可用于Warp。如果你想为我们的语言包做贡献，可以在Github上fork并向我们发送一个request。感谢您的贡献。谢谢您！

### 创建语言文件

1. 转到目录 */warp/systems/joomla/language* 并复制现有目录，例如 */en-GB*。
2. 重命名它（例如，中文 */zh-CN*）。
3. 对目录中的 *.ini* 文件执行相同的操作。
4. 现在您只需要将 *xx-xx.tpl_Warp.ini* 的内容翻译为您的语言。

有关进一步的说明，请看一下Joomla教程中的语言文件规范。

下面是一个简短的示例，说明如何在Joomla模板中使用可翻译的语言字符串。*TPL_WARP_EXAMPLE*是语言变量。
```
JText:：（'tpl_warp_example'）
```