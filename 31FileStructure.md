## 文件结构

了解所有基于Warp 7的主题的文件结构。

### 文件

每个Warp7主题都包含以下文件和文件夹。

|文件夹/文件|说明|
|-------|-----------|
|*/css*|包含主题的所有css文件|
|*/css/custom.css*|使用此文件可以轻松添加自定义css。尽管建议的方法是创建一个*新样式*，以便进行更改和更新|
|*/css/ie8.css*|修复了Microsoft Internet Explorer 8的基本问题|
|*/css/theme.css*|包含主题的默认css。此文件是根据*less/theme.less*文件编译的|
|*/images*|包含主题的所有图像文件|
|*/js*|包含主题的所有javascript文件|
|*/js/theme.js*|负责所有javascript效果和所有基于javascript的函数|
|*/layouts*|包含负责主题布局的核心文件|
|*/layouts/theme.php*|为基本主题布局提供完整的HTML标记。有关详细信息，请查看*主题布局*。|
|*/layouts/theme.config.php*|包含布局计算，并组装主题的css和js文件。|
|*/layouts/widget.php*|负责显示所有控件变量。有关更多信息，请查看*模块位置*。|
|*/less*|此文件夹中存储的主题LESS文件。|
|*/less/uikit*|包含所有uikit主题LESS文件，即构建warp的前端框架。|
|*/less/bootstrap*|包含所有与bootstrap相关的less文件（仅限joomla 3）。|
|*/less/theme.less*|定义主题样式并导入uikit主题。每次在主题设置中单击*编译LESS*时，此文件都将编译为css并保存在*/css*文件夹中。同时，所有样式都将保存在*/styles/style-name/css*文件夹中。|
|*/less/customizer.json*|定义将在默认或高级模式下显示哪些自定义参数。它对uikit变量进行分组，设置可以通过颜色选择器、直接输入或选择框定义的内容，并添加字体。|
|*/less/bootstrap.less*|导入所有与bootstrap相关的文件（仅限joomla 3）。就像*/less/theme.less*文件一样，每次在主题设置中点击*compile less*，它都会编译成css。|
|*/styles*|在这里您可以找到可用的样式变量，并添加您自己的*自定义样式*。|
|*/styles/style-name/style.less*|通过自定义程序生成的LESS变量的自定义集。每次在主题设置中单击*编译LESS*时，这些变量都将用于以*/styles/style-name/css*编译CSS文件。如果不存在此文件，则不会编译任何CSS文件。如果您希望完全使用自己的自定义CSS，这样就不会被覆盖了。|
|*/styles/style-name/css*|包含风格的所有已编译的css文件，比如，*theme.css*文件，对于Joomla 3，还包含一个的*bootstrap.css*文件。所有这些文件都是通过定制程序生成和编译的。|
|*/warp*|此文件夹包含实际的warp 7核心框架。|
|*/changelog.md*|为您提供有关Warp主题的版本号以及迄今为止所做的所有更改的信息。|
|*/config.xml*|定义主题设置。有关详细信息，请查看*config.xml*。|
|*/config.json*|存储保存的主题设置。保存设置后，此文件将自动生成。|
|*/config.default.json*|备份默认主题设置。|
|*/config.php*|注册所有应编译为css的LESS文件。|
|*/templatedetails.xml*|此文件包含有关主题的常规信息，如名称、发布日期、目录和模块设置。|
|*/warp.php*|此文件加载warp框架。|
|*/favicon.ico*|将显示在浏览器栏中。要更改favicon，只需替换此文件。|
|*/apple_touch_icon.png*|，如果您在移动设备上为网站添加书签，这个图片将显示。要更改图标，只需替换此文件。|