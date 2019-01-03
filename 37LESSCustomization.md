## LESS定制

了解如何在主题中自定义LESS、添加自己的uikit主题或向*自定义程序*添加新设置。

### 文件结构

以下是 */less* 文件夹的简短概述。

|文件夹/文件|说明|
|--------------|--------------|
|*/less/theme.less*|定义主题样式并导入uikit主题。每次在主题设置中单击*编译LESS*时，此文件都将编译为css并保存在 */css* 文件夹中。同时，所有样式都将保存在 */styles/style-name/css* 文件夹中。|
|*/less/customizer.json*|定义在默认或高级模式下显示哪些自定义参数。它对uikit变量进行分组，设置可以通过颜色选择器、直接输入或选择框定义的内容，并添加字体。|
|*/less/bootstrap.less*|导入所有与bootstrap相关的文件（仅限Joomla 3）。就像 */less/theme.less*文件一样，每次在主题设置中单击*编译LESS*，它都会编译成css。|
|*/less/uikit*|包含uikit主题文件。uikit核心文件可以在 */warp/vendor/uikit* 中找到。|


### 添加自定义LESS文件夹

在进行任何LESS的自定义之前，请首先遵循本教程。

1. 复制 */less* 文件夹并将其重命名为 */less-custom*。
2. 打开主题的*config.php*并注册新文件夹，而不是 */less* 文件夹：

    ```

    'path' => array(
        'theme'   => array(__DIR__),
        'js'      => array(__DIR__.'/js'),
        'css'     => array(__DIR__.'/css'),
        'less'    => array(__DIR__.'/less-custom'), // Here
        'layouts' => array(__DIR__.'/layouts')
    ),

    ```
    *注意*：这将更改核心LESS文件夹。通过*自定义程序*生成的所有样式都将使用新的 */less-custom*文件夹编译其CSS。

3. 在新的 */less-custom/theme.less* 中导入旧的 */less/theme.less*，方法是用以下导入规则替换整个内容。

    ```

    @import "../less/theme.less";

    ```

    仅限Joomla 3：要使自定义更新更新时不被破坏，请在新的 */less-custom/bootstrap.less* 中导入旧的 */less/bootstrap.less*，方法是使用以下导入规则替换整个内容。

    ```
    @import“../less/bootstrap.less”；

    ```

4. 删除文件夹 */less-custom/uikit*和 */less-custom/bootstrap*。
5. 现在您可以开始在 */less-custom/theme.less* 中添加自定义代码。

### 定制UIKIT

uikit有自己的文档，可以在uikit网站上找到。当您开始使用Warp主题和uikit时，您可能需要特别查看关于**变量、最佳主题化实践和customizer.json**的文档。

执行以下步骤添加自己的uikit主题。

1. 按照上面的教程，添加您自己的LESS自定义文件夹。
2. 将以下文件复制到您的 */less-custom/* 文件夹：
    1. */less/uikit*
    2. */less/bootstrap.less*
    3. */less/theme.less*
3. 现在，您可以自定义 */less-custom* 中的所有文件，如 /*less-custom/uikit* 文件夹、 */less-custom/theme.less*文件或 */less-custom/customizer.json*以添加自定义变量。

### 在自定义程序中选择自定义字体

Warp允许您访问Google字体目录中的所有可用字体。但有时你可能会想添加你自己的字体或者谷歌没有提供的字体。

#### 从链接添加字体

1. 按照上面的教程，添加您自己的LESS文件夹。
2. 打开 */less custom/customizer.json* 文件，并将字体选项和正确的路径添加到列表中。

```
"Custom Fonts": [
    {"name": "FONT-FAMILY", "value": "'FONT-FAMILY'", "url":""}
],
"System Fonts": [ ... ]

```

### 添加您自己的字体

1. 按照上面的教程，添加您自己的LESS文件夹。

2. 在主题目录中创建一个 */fonts*文件夹，并将字体文件放在那里。

3. 将字体的 *@font-face* 规则添加到 */less-custom/theme.less* 并链接到字体文件：

```

@font-face {
  font-family: 'FONT-FAMILY';
  src: url('../fonts/FONT-FAMILY-webfont.eot');
  ....
}

```
4. 打开 */less-custom/customizer.json* 文件并添加如下字体选项：

```

"Custom Fonts": [
    {"name": "FONT-FAMILY", "value": "\"FONT-FAMILY\", Helvetica, Arial, sans-serif"}
],
"System Fonts": [ ... ]

```
就这样！现在可以在主题中使用自定义字体了。

### 定制器和图像

如果要将选择图像（如不同背景）的选项添加到*自定义程序*中，可以按照本教程进行操作。比如说，你想添加两种不同的背景样式，**红色**和**蓝色**。

1. 首先，在 *style/styles/style-name* 目录中创建一个 */images* 文件夹，并将背景图像放在其中。

2. 通过上面的教程，创建一个新 *theme.less*。

3. 为body样式创建一个新变量，并将其添加到 */less-custom/theme.less* 文件中。
```
@theme_global-body-style:‘’；
```
1. 现在我们将为每个背景案例创建一段代码。在我们的示例中，红色的情况一个，蓝色的情况下一个。

```

.body-style() when (@theme_global-body-style = red) {

  body { background: url(../styles/STYLE-NAME/images/my-red.jpg) 0 0 repeat; }

}

.body-style() when (@theme_global-body-style = blue) {

  body { background: url(../styles/STYLE-NAME/images/my-blue.jpg) 0 0 repeat; }

}

```
5. 然后，我们需要调用代码，它生成实际的css输出。

```
 .body-style();
```

6. 现在，我们将为body的样式 *@theme_global-body-style* 创建一个选择框。只需在 */less-custom/customizer.json* 中添加以下代码。

```
{
    "type": "select",
    "vars": [
        "@theme_global-body-style"
    ],
    "options": [
        {"name": "Default", "value": ""},
        {"name": "Red", "value": "red"},
        {"name": "Blue", "value": "blue"}
    ]
},

```
，
7. 最后，定义新创建的变量应该出现在哪个组中。在我们的示例中，我们将它添加到*一般*变量中。

```
 "groups": [
        {
            "label": "General",
            "vars": [
                "@theme_global-body-style",
                "@global-background",
                "@global-border",
```