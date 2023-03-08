# 颜色选择控件 (Color Picker)

![Matrix.OS](../../../../../media/os/tools/modelview/showcolorpicker.gif "颜色选择控件")

颜色选择控件允许用户点击色卡打开选取颜色对话框并在其中选取颜色，或者直接输入色调、饱和度与亮度完成交互。具有下列属性：

* ID：控件的唯一标识，由开发者赋予，代表控件在数据节点树中的键值 (支持数值、英文字符，和中文)。

* 控件文本：与控件一起显示的标题性文字。

* 提示工具：当用户悬停在控件上时，显示的提示性文本。

* 默认颜色：颜色选取器默认选定颜色。

* 必填：强制用户输入。

## 添加颜色选择控件

在视图页面草稿中，点击工作区顶部`颜色选择控件`按钮，即可完成颜色选择控件的添加，如下图所示：

![Matrix.OS](../../../../../media/os/tools/modelview/addcolorpicker.gif "添加颜色选择控件")

新添加的颜色选择控件使用系统默认设置，如下图所示，开发者可以对其进一步修改和定制。

![Matrix.OS](../../../../../media/os/tools/modelview/addcolorpicker.png "颜色选择控件默认设置")

## 编辑颜色选择控件

点击控件右侧`编辑`按钮，即可打开`控件设置`对话框，对颜色选择控件的属性进行编辑与设置，如下图所示：

![Matrix.OS](../../../../../media/os/tools/modelview/editcolorpicker1.gif "编辑颜色选择控件 - 打开控件设置对话框")

首先，可以对"控件ID"和"控件文本"进行编辑，如下图所示：

![Matrix.OS](../../../../../media/os/tools/modelview/editcolorpicker2.gif "编辑颜色选择控件 - 控件ID与文本编辑")

如需要，可以对默认颜色值进行设置，如下图所示：

![Matrix.OS](../../../../../media/os/tools/modelview/editcolorpicker3.gif "编辑颜色选择控件 - 设置默认颜色")

完成所有设置后，点击`保存并关闭`按钮，即保存设置并返回视图页面，可以查看控件的编辑与设置结果，如下图示例：

![Matrix.OS](../../../../../media/os/tools/modelview/editcolorpicker4.gif "编辑颜色选择控件 - 保存控件设置")

## 预览测试

滑动工作区右上角`预览`滑块，进入视图页面"预览模式"，可以对颜色选择控件进行测试和效果预览，查看数据节点树 JSON 文件校验颜色选取数值正确与否，如下图所示：

![Matrix.OS](../../../../../media/os/tools/modelview/testcolorpicker.gif "测试颜色选择控件")