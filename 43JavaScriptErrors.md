## Javascript错误

了解如何处理Javascript问题和防止错误。

几乎每个Joomla扩展都使用Javascript，依赖jQuery之类的库。在网页上使用不同的脚本可能会导致它们之间的冲突。

### 如何检测错误

如果在单击某个内容没反应，或动画停止工作时，则可能是由于脚本错误。在这种情况下，浏览器会停止执行脚本。

以下开发工具向您显示脚本错误，包括有关出错的信息、文件和行号以及导致错误的源代码。

|开发者工具|描述|
|-------|------------|
|*浏览器调试控制台*|一种方法是在出现错误的页面上使用浏览器的调试控制台。它将帮助您识别Web服务器上的脚本及其相关文件。|
|*Firebug和其他浏览器WDT*|火狐的Firebug允许您检查和非破坏性地编辑HTML，还包括一个强大的Javascript调试器。其他浏览器如Chrome、Safari或Opera也有类似的内置工具。|


### 如何解决错误

通常，错误是由一个或多个扩展引起的。如果您在一个页面上检测到一个Javascript错误，您需要找到它的来源。

1. 一旦确定了扩展，请尝试*禁用*它，以确保您的页面能够正常工作，不会再次出现任何错误。
2. 如果错误消失了，您就找到了导致冲突的扩展。
3. 现在，您可以查找*扩展配置选项*，看看它是否允许您启用/禁用加载类似jQuery的Javascript库来解决错误。


### 防止在Joomla 2.5中多次加载jQuery

Joomla社区正在讨论如何防止跨扩展多次加载jQuery。我们已经采取措施，实施了一个被广泛接受的解决方案。我们通过JApplication注册来插卡jQuery是否加载。如果第三方扩展加载jQuery库，可以使用以下代码段防止Zoo、WidgetKit或Warp主题加载两次。

```
// load jQuery, if not loaded before
if (!JFactory::getApplication()->get('jquery')) {
    JFactory::getApplication()->set('jquery', true);
    // add jQuery
    ...
}
```

*注意*：您也可以与第三方扩展开发人员联系，并请他们实现这一点。