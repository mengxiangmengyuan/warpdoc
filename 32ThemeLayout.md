## 主题布局

了解如何渲染主题布局。

两个核心的PHP文件决定了主题的布局和标记。了解如何呈现模块的位置以及如何计算它们的大小。

### theme.php

每个主题的核心是*theme.php*，它为基本主题标记提供了整个HTML。这不同于标准的Joomla主题，*index.php*是主要的模板文件。

下面是*theme.php*的框架结构。该文件需要导入*theme.config.php*，规定模块位置，检索配置变量，并渲染系统输出。

```
<?php

// 获取主题配置
include($this['path']->path('layouts:theme.config.php'));

?>
<!DOCTYPE HTML>
<html lang="<?php echo $this['config']->get('language'); ?>" dir="<?php echo $this['config']->get('direction'); ?>"  data-config='<?php echo $this['config']->get('body_config','{}'); ?>'>

  <head>
  <?php echo $this['template']->render('head'); ?>
  </head>

  <body>

    // 显示模块位置
    <?php echo $this['widgets']->render('widget-position'); ?>

    // 显示配置参数
    <?php echo $this['config']->get('variable'); ?>

    // 输出系统内容
    <?php echo $this['template']->render('content'); ?>

  </body>

</html>

```
#### 配置对象

*config.xml*中的变量存储在*config*对象中。要访问变量的值，只需使用*get*方法。

```

// 输出branding变量的值
<?php echo $this['config']->get('theme_branding'); ?>

// 根据系统设定输出to-top scroller
<?php if ($this['config']->get('totop_scroller')) : ?>
<a class="tm-totop-scroller" data-uk="smooth-scroll" href="#"></a>
<?php endif; >

```

#### 模块（控件）对象

页面的模块（小部件）存储在*widgets*对象中。要在某个位置输出所有小部件，请使用*render*方法。您可以使用*count*方法检查某个位置上是否发布了任何小部件。

```

<//输出位于top-a位置的所有模块
<？php echo$this['widgets']->render（'top-a'））；？>

//将并行布局应用于位于top-a位置的所有小部件
<？php if（$this['widgets']->count（'top-a'））：？>
<？php echo$this['widgets']->render（'top-a'，array（'layout'=>'parallel'））；？>
<？PHP？>

```

### theme.config.php

*theme.php*基本上只定义主题的标记，逻辑被外包给*theme.config.php*。它负责计算，比如，3列布局以及body的类和社会化分享按钮。