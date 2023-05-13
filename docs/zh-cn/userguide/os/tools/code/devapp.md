# 使用 Code 开发云应用

## 概要

云应用（App）是指专门解决某类问题或者提供某种功能的程序、微服务、工具、算法模块等（见下图示例），具备一定的用户交互功能（比如接收用户输入信息或者上传文件等）并生成满足用户需求的运行结果。

![Matrix.OS](../../../../../media/os/tools/code/codeapp.gif "云应用示例：环状树图制作工具")

使用 Code 开发云应用的关键在于**通过用户界面接口来实现用户输入与后端代码的交互**。下面将详细介绍建立不同类型用户界面接口的方法和在代码中调用的过程。为了方便展示，将使用一些简单的例子来说明。

更多云应用开发案例请参考：《[Matrix 玩法与案例应用：开发实践](zh-cn/demo/gallery.md)》

## 设置云应用引导程序

云应用一般由多个代码文件、多级模型视图以及资源文件通过 Code 组装编译而成。开发者首先需要设置引导程序（main 程序）文件来驱动代码和用户界面接口。

### 激活引导程序设置

点击 Code 左侧导航栏上方的 <img src="./././././media/logo/codegear.png" width="15" height="15"> 图标，点击选中 <img src="./././././media/logo/codemainon.png" width="80" height="20"> 复选框，这将激活 Code 中的引导程序设置功能，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/activatemain.gif "激活引导程序设置")

### 指定引导程序文件

点击选中待设置为引导程序的代码文件，拖动激活 <img src="./././././media/logo/codesetmain.png" width="70" height="20"> 滑块，即可将该文件设置为引导程序（文件名前显示 <img src="./././././media/logo/codemainlabel.png" width="20" height="20"> 标记），同时也激活了用户界面接口设置按钮 <img src="./././././media/logo/codeui.png" width="80" height="20">，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/setmain.gif "设置引导程序文件")

## 设置用户界面接口

Code 提供以下两种用户界面接口类型：

* **模型视图接口**：实现用户对一个或多个模型视图窗体的输入及其与引导程序的交互。
* **文件接口**：实现一个或多个用户上传文件与引导程序的交互。

### 模型视图接口

模型视图（Model-View）是 Matrix 用于实现数据标准化、前端 UI 设计、和交互接口功能的标准模型与可视化页面。关于模型视图的详细介绍和使用请参考教程《模型视图管理器》相关章节。

Code 支持开发者引入任意多个模型视图来实现用户交互，并将每一个模型视图映射为 json 接口文件，用于在代码中调用。在下图示例中，可以发现每一个模型视图都被 Code 映射为相应的 json 接口文件显示在左侧导航栏中。

![Matrix.OS](../../../../../media/os/tools/code/modelviewport.png "模型视图接口文件")

**添加模型视图接口**

以下，我们将使用一个简单的例子来说明添加模型视图接口的方法和代码调用过程。

在例子中，我们将添加一个模型视图接口，用来连接云 OS 上的一个名为 "demo" 的简单模型视图，该视图接收用户输入的个人信息。

点击 <img src="./././././media/logo/codeui.png" width="80" height="20"> 按钮，即打开`用户界面设置`对话框，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/openUIport.gif "打开用户界面接口设置")

选中 <img src="./././././media/logo/codemvport.png" width="80" height="20"> 复选框，需要设置：

* `视图名称`：所添加的模型视图接口文件名（也即模型视图对应的 json 格式数据节点树文件名）。
* `简介`：向用户介绍如何使用该视图界面的辅助性信息文字。

在例子中，我们将视图名称设置为 "person"，将简介设置为 "请输入个人信息"，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/modelviewUI1.gif "添加模型视图接口：视图名与简介")

点击 <img src="./././././media/logo/codeaddport.png" width="45" height="20"> 按钮，在云桌面 OS 上选择要连接的模型视图 "demo"，点击 <img src="./././././media/logo/createbutton.png" width="45" height="20"> 按钮，即可完成模型视图接口的添加（可在对话框下方列表中找到），如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/modelviewUI2.gif "添加模型视图接口：连接 OS 模型视图")

关闭对话框后，可以发现在 Code 左侧导航栏出现一个新文件 "person.json"，这个文件就是模型视图 "demo" 映射到 Code 中的接口文件，如下图所示：



### 文件接口


开发者需要选择设置一个引导程序（主程序）文件来驱动所有的代码和资源。当然如果开发者只是以开源代码为目的的发布，则无需设置引导程序文件。

关于终端的详细使用方法可参考:

《[使用网络终端](zh-cn/userguide/os/tools/terminals/webt.md)》
《[使用本地终端](zh-cn/userguide/os/tools/terminals/localt.md)》
《[使用Remote SSH](zh-cn/userguide/os/tools/terminals/remotessh.md)》