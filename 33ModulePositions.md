## 模块位置

了解如何为Joomla模块创建新的位置、布局和样式。

在主题中添加模块的新位置非常简单。您必须命名一个位置并定义该位置在*主题布局*中的渲染位置。

### 添加新位置

在*templatedetails.xml*中添加一个新位置，使您的内容管理系统知道它存在。然后，新选项将显示在主题设置中。

```

<position>top-a<position>
<position>my-position<position>
<position>bottom-a<position>

```
#### 添加设置

使用*setting*属性，可以控制你添加的位置上的模块外观。您可以在主题设置的*模块*面板中找到这些。可用值包括*class, style, icon, badge, display*。

```

<！--所有选项都可用-->
<position>my-position<position>

<！--没有可用的选项-->
<position settings="">my-position<position>

<！--只有样式和徽章选项可用-->
<position settings=“style badge”>my-position<position>

```

*注意*：如果没有*setting*这个属性，您添加的位置将自动显示所有可用选项。如果在不添加值的情况下使用*setting*这个属性，它将不会显示在*模块*面板中。

在*模块管理器*一章中获取有关*setting*的更多信息。

### 位置的主题设置

编辑*config.xml*，将在主题设置中的*设置*和*布局*面板中，添加更多关于这个位置的选项。

#### 设置自定义位置上模块的默认样式

将新的 *<row>* 元素添加到 *setting* 部分的表格字段 *panel_default* 中，以便您的位置可以选择默认样式。

```

<fields name="Settings">
    ...
    <field type="table" name="panel_default">
        <rows label="Position">
            <row>MY-POSITION</row>
            ...

```

#### 设置自定义位置上布局的默认样式

将新的 *<row>* 元素添加到 *layouts* 部分的表格字段 *grid* 中，以便您的位置具有设置布局、响应式和分隔符的选项。

```
<fields name=“layouts”>
…
<field type=“table”name=“grid”>
<rows label=“position”>
<row>my-position<row>
…

```

请参阅*config.xml*一章，了解有关它的更多信息。

### 渲染位置

*/layouts/theme.php* 提供了主题的基本标记。在这里，您可以定义模块（小部件）位置的渲染位置，并添加新位置。

```

<?php if ($this['widgets']->count('MY-POSITION')):?>
    <section class="uk-grid" data-uk-grid-match="{target:'> div > .uk-panel'}">
        <?php echo $this['widgets']->render('MY-POSITION', array('layout'=>$this['config']->get(
        'grid.MY-POSITION.layout'))); ?>
    </section>
<?php endif;?>

```

*注意*：如果在*config.xml*中声明了一个选项，您只需要添加*$this['config']->get('grid.my-position.layout')*语句。

请看一下*主题布局*，以便更好地理解模块（小部件）的渲染方法。

### 添加CSS类的高级方法

如果您的位置在*config.xml*的表个字段*grid*中声明为一个新的 *<row>* ，那么我们提供了一种添加CSS类的简单方法。只是添加```<?php echo $grid_classes['MY-POSITION']; ?>```到您的*class*属性。这将为您的位置提供设置布局、响应行为和分隔符的选项。

```
<?php if ($this['widgets']->count('MY-POSITION')) : ?>
    <section class="<?php echo $grid_classes['MY-POSITION']; ?>" data-uk-grid-match="{target:'> div > .uk-panel'}" data-uk-grid-margin>
        <?php echo $this['widgets']->render('MY-POSITION', array('layout'=>$this['config']->get('grid.MY-POSITION.layout'))); ?>
    </section>
<?php endif; ?>

```