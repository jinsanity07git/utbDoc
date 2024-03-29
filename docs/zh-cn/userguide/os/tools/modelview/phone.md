# 手机号码输入控件 (PhoneNumber Input)

![Matrix.OS](../../../../../media/os/tools/modelview/showphone.gif "手机号码输入控件")

手机号码输入控件是一个简单的文本框，仅接受手机号码格式的输入并具有下列属性：

* ID：控件的唯一标识，由开发者赋予，代表控件在数据节点树中的键值 (支持数值、英文字符，和中文)。

* 控件文本：与控件一起显示的标题性文字。

* 提示工具：当用户悬停在控件上时，显示的提示性文本。

* 默认值：输入框的缺省内容。

* 必填：强制用户输入。

* 内容重用：反复使用手机号码输入框时保留上一次填写内容。

## 添加手机号码输入控件

在视图页面草稿中，点击工作区顶部 <img src="./././././media/logo/controlinput.png" width="50" height="20"> 按钮，在下拉菜单中选中`手机号码`，即可完成手机号码输入控件添加，如下图所示：

![Matrix.OS](../../../../../media/os/tools/modelview/addphone.gif "添加手机号码输入控件")

新添加的手机号码输入控件使用系统默认设置，如下图所示，开发者可以对其进一步修改和定制。

![Matrix.OS](../../../../../media/os/tools/modelview/addphone.png "手机号码输入控件默认设置")

## 编辑手机号码输入控件

点击控件右侧 <img src="./././././media/logo/editcontrol.png" width="60" height="20"> 按钮，即可打开`控件设置`对话框，对手机号码输入控件的属性进行编辑与设置，如下图所示：

![Matrix.OS](../../../../../media/os/tools/modelview/editphone1.gif "编辑手机号码输入控件 - 打开控件设置对话框")

首先，可以对 "控件ID" 和 "控件文本" 进行编辑，如下图示例：

![Matrix.OS](../../../../../media/os/tools/modelview/editphone2.gif "编辑手机号码输入控件 - 控件ID与文本编辑")

然后，可以对手机号码输入控件的默认内容进行设置，如下图示例：

![Matrix.OS](../../../../../media/os/tools/modelview/editphone3.gif "编辑手机号码输入控件 - 设置默认内容")

完成所有设置后，点击 <img src="./././././media/logo/saveclose.png" width="60" height="20"> 按钮，即保存设置并返回视图页面，可以查看控件的编辑与设置结果，如下图示例：

![Matrix.OS](../../../../../media/os/tools/modelview/editphone4.gif "编辑手机号码输入控件 - 保存控件设置")

## 预览测试

滑动工作区右上角 <img src="./././././media/logo/previewmv.png" width="50" height="20"> 滑块，进入视图页面 "预览模式"，可以对手机号码输入控件的操作和数据反馈正确性进行测试，在下图示例中，数据节点树 JSON 文件中的控件属性值正确响应了对手机号码输入控件的操作。

![Matrix.OS](../../../../../media/os/tools/modelview/testphone.gif "测试手机号码输入控件")