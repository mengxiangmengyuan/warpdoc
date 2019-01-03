## 定制

了解如何添加您的自定义设置，并进一步了解Warp中的文件层次结构。

为了提供尽可能多的灵活性，Warp应用了一个特殊的文件级联。如果包含任何文件（如css、js或模板php文件），则Warp将依次在特定文件夹中查找这些文件，并将加载找到的第一个文件。这使您能够完全灵活地覆盖任何与主题相关的重要文件。

我们将进一步解释覆盖级联。如果您只想知道如何覆盖主题文件，请直接跳到适当的示例。

### 覆盖层叠

例如，*/layouts*文件夹的覆盖层次结构就是这样的。

1. 样式文件夹
    主题的 */styles/style-name/layouts* 文件夹位于层次结构的顶部，您在此处所做的修改或添加将覆盖所有其他主题文件。同样，此文件夹将在更新期间保留，因此它是进行修改的最安全位置。

2. 主题文件夹
    主题 */layouts* 文件夹存储所有主题特定布局文件。

3. 系统文件夹
    */warp/systems/joomla/layouts*文件夹提供与特定CMS集成所需的单个系统实现。这一层使Warp适应特定的系统，形成一个一致的主题开发API。

4. Warp文件夹
    */warp/layouts*文件夹包含核心框架所做的基本覆盖。核心框架的每个部分都是通用的，并且设计为在每个支持的系统上工作。

*/js、/css和/layouts*文件夹的级联在主题的config.php中定义。如果要在级联中注册另一个文件夹，可以在此处进行注册。

### 布局覆盖

要自定义常规主题布局，需要重写 */layouts/theme.php*。为此，请创建 */styles/style-name/layouts* 目录，复制其中的文件并开始添加自己的PHP代码。

这样，您还可以覆盖系统文件。例如，只需将Joomla文章布局 */warp/systems/joomla/layouts/com_content/article/default.php* 复制到样式文件夹 */styles/style-name/layouts/com_content/article/default.php* 并进行修改。现在，将使用修改后的文章布局文件，而不是默认的系统布局。

### 添加您自己的CSS

有几种方法可以将您自己的自定义CSS添加到Warp主题中。您可以使用*自定义程序*更改主题的大部分方面，而不必编写任何CSS。请记住，只有当样式文件夹中有一个style.less文件时，样式才会显示在*自定义程序*中。使用*自定义程序*时，更改将保存在*style.less*文件中。与主题LESS文件一起，它将被编译到 */css/theme.css*文件中，并覆盖您已经做过的任何自定义。

#### 添加自定义CSS

您可以使用*自定义工具*，也可以通过在 */css* 文件夹中为相关样式创建一个 *custom.css* 文件来添加您自己的css。这样，当您在*自定义程序*中保存更改时，您的CSS就不会被覆盖。

#### 添加CSS而不使用LESS的和自定义程序

如果您根本不打算使用定制程序，只需复制现有样式并删除 *style.less* 文件即可。现在，当编译LESS时，*/css/theme.css*将不再被覆盖。您可以直接在*theme.css*文件中编写自定义项。

### 添加自定义javascript

配置文件 */layouts/theme.config.php* 初始化所有PHP类并加载必要的Javascript。如果需要加载自定义的javascript文件，可以在这里进行。启用的压缩和Data URI将自动应用于您在此添加的所有文件。

1. 创建一个新文件 */styles/style-name/layouts/theme.config.php*。
2. 使用*require*函数通过PHP加载原主题的 *theme.config.php* 文件。
3. 然后将您的Javascript文件添加到asset集合中，这样它将自动添加到模板header中。
4. 将您自己的自定义Javascript文件放在 */styles/style-name/js/my-js.js* 目录中。
    ```

    require(__DIR__.'/../../../layouts/theme.config.php');

    // add script
    $this['asset']->addFile('js', 'js:MY-JS.js');

    ```