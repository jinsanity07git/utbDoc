# 文件控件 (File Box)

![Matrix.OS](../../../../../media/os/tools/modelview/showfilebox.gif "文件控件")

文件控件是一个选取器，允许用户选取本地文件，通过模型视图接口上传到云OS，从而实现与各种云端应用和代码的交互。具有下列属性：

* ID：控件的唯一标识，由开发者赋予，代表控件在数据节点树中的键值 (支持数值、英文字符，和中文)。

* 控件文本：与控件一起显示的标题性文字。

* 提示工具：当用户悬停在控件上时，显示的提示性文本。

* 文件类型：由开发者指定的文件控件扩展名过滤器。

* 文件数：由开发者指定的最多允许上传文件个数。

* 必填：强制用户上传文件。

## 添加文件控件

在视图页面草稿中，点击工作区顶部 <img src="./././././media/logo/controlfile.png" width="50" height="20"> 按钮，即可完成文件控件的添加，如下图所示：

![Matrix.OS](../../../../../media/os/tools/modelview/addfilebox.gif "添加文件控件")

新添加的文件控件使用系统默认设置，如下图所示，开发者可以对其进一步修改和定制。

![Matrix.OS](../../../../../media/os/tools/modelview/addfilebox.png "文件控件默认设置")

## 编辑文件控件

点击控件右侧 <img src="./././././media/logo/editcontrol.png" width="60" height="20"> 按钮，即可打开`控件设置`对话框，对文件控件的属性进行编辑与设置，如下图所示：

![Matrix.OS](../../../../../media/os/tools/modelview/editfilebox1.gif "编辑文件控件 - 打开控件设置对话框")

首先，可以对 "控件ID" 和 "控件文本" 进行编辑，如下图所示：

![Matrix.OS](../../../../../media/os/tools/modelview/editfilebox2.gif "编辑文件控件 - 控件ID与文本编辑")

如需要限定可上传的 "文件类型"，可以在`文件类型`输入框中依次输入文件扩展名并回车，建立文件类型过滤器，如下图所示：

![Matrix.OS](../../../../../media/os/tools/modelview/editfilebox3.gif "编辑文件控件 - 设置扩展名过滤")

如需要限定上传文件的数量，可以激活 <img src="./././././media/logo/filelimit.png" width="90" height="20"> 并输入最大文件个数，如下图所示：

![Matrix.OS](../../../../../media/os/tools/modelview/editfilebox4.gif "编辑文件控件 - 限制上传文件数")

完成所有设置后，点击 <img src="./././././media/logo/saveclose.png" width="60" height="20"> 按钮，即保存设置并返回视图页面，可以查看控件的编辑与设置结果，如下图示例：

![Matrix.OS](../../../../../media/os/tools/modelview/editfilebox5.gif "编辑文件控件 - 保存控件设置")

## 预览测试

与其他控件不同，文件控件不支持预览模式，只能在部署后的模型视图中使用。详细使用方法与案例参见《[Matrix 案例库：模型视图应用](zh-cn/demo/gallery.md)》相关章节。
