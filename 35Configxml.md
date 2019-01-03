## Config.xml

config.xml定义了warp 7主题的设置。

在主题设置中，可以控制主题布局、模块和菜单的基本首选项。每个后台菜单选项卡都有自己的选项面板，并在*config.xml*中定义。

### 字段集

*<fields>* 元素定义了菜单选项卡并为其创建面板。

```

<?xml version="1.0" encoding="utf-8"?>
<config>
    <fields name="Settings" icon="uk-icon-cogs">
        ...
    </fields>
    <fields name="Layouts" icon="uk-icon-columns">
        ...
    </fields>
    <fields name="Modules" icon="uk-icon-th">
        ...
    </fields>
    <fields name="Menus" icon="uk-icon-reorder">
        ...
    </fields>
    <fields name="Information" icon="uk-icon-info-sign">
        ...
    </fields>
</config>

```

#### 添加新菜单项

*<fields>* 元素将添加一个新选项卡。*name*属性的值是选项卡名称。

```

<fields name="MY-MENUITEM" icon="uk-icon-info-sign">
    ...
</fields>

```

### 字段

*<field>* 元素包含在字段集元素中，为每个菜单项定义选项。

#### 基本的XML类型

可以使用基本XML类型为主题设置创建新选项。例如，可以是一个单选按钮、一个复选框或一个输入字段。

|类型|说明|
|------|----------|
|*section*|显示描述文本。|
|*radio*|单选按钮。|
|*checkbox*|复选框。|
|*select*|下拉列表。|
|*text*|文本框。|
|*textarea*|多行文本输入。|

##### 特殊XML类型

Warp7还提供了一些特定的类型：*layouts, verify, styles, compile， info*。

#### 标记实例

```
<!-- Section field -->
<field type="section" name="Headline" description="A description text." />

<!-- Checkbox field -->
<field type="checkbox" name="my-option-1" value="1" label="A description text." />

<!-- Radio field -->
<field type="radio" name="my-option-2" value="1" label="A description text." />

<!-- Select field -->
<field type="select" name="my-option-3" default="0">
    <option value="0">Option A</option>
    <option value="1">Option B</option>
    <option value="2">Option C</option>
    <option value="3">Option D</option>
</field>

<!-- Text field -->
<field type="text" name="my-option-4" />

<!-- Textarea field -->
<field type="textarea" name="my-option-5" class="uk-form-width-large" rows="8" />

```

#### 添加新选项

要创建新选项，请将 *<field>* 元素添加到设置中，即在要添加选项的 *<fields>*元素中。您还可以复制一个现有的并根据需要修改它。

### config.json

*config.xml* 定义哪些主题设置可用。如果有人保存了主题设置，它们将保存在压缩后的*config.json*文件中。每次保存过程中，该文件都将被覆盖。

Warp主题提供了一个单独的*config.default.json*文件，其中存储了默认的主题设置。这使您能够将后端恢复到默认设置，并备份自己的*config.json*文件，使您的设置更新时不会被破坏。

*注意*：要获得更好的浏览效果，请使用*JSON格式化程序*。这将使您的压缩文件更易于阅读。

### 配置对象

*config.xml*中的变量存储在*config*对象中。要访问变量的值，只需使用*get*方法。在*主题布局*一章中了解更多关于它的信息。