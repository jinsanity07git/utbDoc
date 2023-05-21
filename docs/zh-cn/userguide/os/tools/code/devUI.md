# (三) 用户界面接口

Code 在开发云应用时通过用户界面接口来实现用户交互。用户界面接口主要包括两种类型：

* **模型视图接口**：连接模型视图窗体获取用户操作与输入。
* **文件端口**：获取用户上传的单个或批量文件。

在本例中，我们将同时使用以上两种接口类型。

## 模型视图接口

模型视图（Model-View）是 Matrix 用于实现数据标准化、前端 UI 设计、和交互接口功能的标准模型与可视化页面。关于模型视图的详细介绍和使用请参考教程《模型视图管理器》相关章节。

Code 支持开发者引入任意多个模型视图作为云应用前端来实现用户交互，并将每一个模型视图映射为独立的 json 接口文件 (显示在左侧导航栏中，文件名前有 <img src="./././././media/logo/codeuifile.png" width="15" height="15"> 标记)，用于在代码中调用，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/modelviewport.png "模型视图接口文件")

### 创建模型视图

我们首先需要创建一个模型视图作为应用的输入界面。该视图可以接收用户输入的 "绘图尺寸" 来自动绘制环状树图。具体步骤如下：

1）右键点击 `UI` 文件夹，选择创建 `模型视图`，将其命名为 "chart"，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/newmv.gif "建立模型视图")

2）打开 "chart"，创建一个视图页面草稿，取名为 "图表信息"，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/newdraft.gif "建立视图页面草稿")

3）在 "图表信息" 视图页面添加两个`整数输入控件`，分别对控件做以下设置：

* 控件ID："chartwidth"，控件文本："输入图表宽度（像素）" ，默认值： `1280`。
* 控件ID："chartheight"，控件文本："输入图表高度（像素）" ，默认值： `720`。

如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/newcontrol.gif "添加输入控件")

注意：以上设置的控件 ID 将会在后面使用代码调用模型视图接口时用到。

4）保存视图草稿，然后将其`添加到发布`。然后进入`发布区`，在视图列表中，将 "图表信息" 视图 ID 设置为 "chartinfo" 并保存，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/releasedraft.gif "发布模型视图，修改视图ID")

### 连接模型视图

完成模型视图的创建与编辑，我们返回 Code，现在要添加一个模型视图接口，用来连接 `UI`文件夹下刚刚编辑好的模型视图 "chart"，将它作为云应用的前端输入界面。 

1）点击 <img src="./././././media/logo/codeui.png" width="80" height="20"> 按钮，即打开`用户界面设置`对话框，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/openUIport.gif "打开用户界面接口设置")

2）选中 <img src="./././././media/logo/codemvport.png" width="80" height="20">，需要设置：

* `视图名称`：所添加的模型视图接口文件名（也即模型视图对应的 json 格式数据节点树文件名）。
* `简介`：介绍性信息文字。

在这里，我们将`视图名称`设置为 "chart" (可以设置为任意名称)，将`简介`设置为 "请输入制图尺寸"，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/modelviewUI1.gif "设置视图接口文件名与简介")

3）点击 <img src="./././././media/logo/codeaddport.png" width="45" height="20"> 按钮，在对话框中选择 "UI" 文件夹下的模型视图 "chart"，点击 <img src="./././././media/logo/createbutton.png" width="45" height="20"> 按钮，即可完成模型视图接口连接（出现在对话框下方列表中），如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/modelviewUI2.gif "连接创建好的模型视图")

4）关闭对话框，可以发现在 Code 左侧导航栏出现一个新文件 "chart.json"，这个文件就是模型视图 "chart" 映射到 Code 中的接口文件 (带有 <img src="./././././media/logo/codeuifile.png" width="15" height="15"> 标记)，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/modelviewUI3.gif "生成接口文件")

5）点击 <img src="./././././media/logo/codedebug.png" width="60" height="20"> 按钮，打开用户输入模块，可以测试模型视图接口文件内容，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/modelviewUI4.gif "测试模型视图接口文件内容")

可以发现，用户使用模型视图输入信息后，会更新到接口文件 "chart.json" 中，结构如下图所示：

<img src="./././././media/os/tools/code/demomvjson1.png" width="50%" height="50%">

### 调用模型视图接口

有了接口文件，我们可以非常方便地在代码中调用它来获取用户输入。

在 "radial.py" 中输入以下 python 代码，保存后调试运行。

```python
import json

with open('../chart.json') as f:  # 读取模型视图接口文件 chart.json（注意使用相对路径）
  userinput = json.load(f)        
  
print(userinput['chartinfo']['chartwidth'])   # 解析获取用户输入的制图宽度并打印
print(userinput['chartinfo']['chartheight'])  # 解析获取用户输入的制图高度并打印
```

以上代码读取模型视图接口文件 "chart.json"，将读取信息赋予 userinput 字符串。然后解析 userinput，获取模型视图中每个控件所对应的节点数据（也就是制图的宽与高），并打印出来。如下图示例：

![Matrix.OS](../../../../../media/os/tools/code/modelviewUI5.gif "代码调用接口文件信息")

以上我们展示了建立、连接、调用模型视图接口的方法。照此方法，开发者可以根据实际需要在 Code 中操作多个模型视图，实现更为复杂的功能。更多例子请参考：《[Matrix 玩法与案例应用：开发实践](zh-cn/demo/gallery.md)》。

## 文件端口

除了输入绘图尺寸，云应用还允许用户自行上传数据文件，据此来绘制环状树图。为此，我们还需要在应用中添加文件端口来实现这一功能。

Code 支持开发者引入任意多个文件端口实现用户交互，并以文件或文件夹的形式显示在左侧导航栏中（有 <img src="./././././media/logo/codeuifile.png" width="15" height="15"> 标记），用于在代码中调用，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/fileport.png "文件端口")

Code 提供了两种类型的文件端口：

* `单文件端口`：接收用户上传的单个文件（在本例中介绍并使用）。
* `批量文件端口`：接收用户批量上传多个文件。

### 创建单文件端口

1）在`用户界面设置`对话框中，选中 <img src="./././././media/logo/codefileport1.png" width="90" height="20">，需要设置：

* `文件端口名`：所添加的单文件端口名（用于在代码中调用）。
* `文件类型`：限定用户上传文件的类型（文件扩展名，如 csv）。
* `简介`：介绍性信息文字。

在这里，我们将`文件端口名`设置为 "data" (可以设置为任意名称)，`文件类型`设置为 "json"，`简介`设置为 "请上传 json 格式制图数据文件"。点击 <img src="./././././media/logo/codeaddport.png" width="45" height="20"> 按钮，即可完成单文件端口创建（出现在对话框下方列表中），如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/fileport1.gif "建立单文件端口")

2）关闭对话框，可以发现在 Code 左侧导航栏出现一个新文件 "data.json"，这就是刚刚创建的单文件端口 (带有 <img src="./././././media/logo/codeuifile.png" width="15" height="15"> 标记)，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/fileport2.gif "查看单文件端口")

### 调用单文件端口

有了单文件端口，我们可以非常方便地在代码中调用它来获取用户上传的单个文件。

将 "radial.py" 更新为以下代码并保存。

```python
import json

with open('../chart.json') as f:  # 读取模型视图接口文件 chart.json（注意使用相对路径）
  userinput = json.load(f)        
  
print(userinput['chartinfo']['chartwidth'])   # 解析获取用户输入的制图宽度并打印
print(userinput['chartinfo']['chartheight'])  # 解析获取用户输入的制图高度并打印

with open("../data.json", "r", encoding="utf-8") as f:  # 读取文件端口 data.json（注意使用相对路径）
    userdata = json.load(f)
  
print(userdata)   # 获取文件端口中的用户上传数据文件并打印
```

可以发现，以上代码在之前基础上，增加了读取单文件端口 "data.json" 功能，将读取的用户数据文件赋予 userdata 字符串，并在用户终端打印出来。

点击 <img src="./././././media/logo/codedebug.png" width="60" height="20"> 按钮，打开用户输入模块，可以发现新增添的文件输入项。我们使用云桌面上的 "flare.json" 数据，测试运行如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/fileport3.gif "测试单文件端口")

通过以上测试运行可以发现，单文件端口成功地获取了用户提供的 "flare.json" 文件，并在右侧终端窗口打印出来。

### 创建多文件端口

尽管在本例中不会使用到多文件端口，我们依然在这一节教程中对此做简要介绍。其它多文件端口使用例子参见《[Matrix 玩法与案例应用：开发实践](zh-cn/demo/gallery.md)》。

创建多文件端口的过程与创建单文件端口类似，步骤如下：

1）在`用户界面设置`对话框中，选中 <img src="./././././media/logo/codefileport2.png" width="90" height="20">，需要设置：

* `文件端口名`：所添加的多文件端口名（用于在代码中调用）。
* `文件类型`：限定用户上传文件的类型（文件扩展名，如 csv）。
* `端口允许最大文件数`：允许用户批量上传的文件数量最大限制。
* `简介`：介绍性信息文字。

在下图中我们将`文件端口名`设置为 "uploadfiles" (可以设置为任意名称)，`文件类型`设置为 "json"，`端口允许最大文件数`设置为 20，`简介`设置为 "请批量上传 json 格式数据文件"。点击 <img src="./././././media/logo/codeaddport.png" width="45" height="20"> 按钮，即可完成多文件端口创建（出现在对话框下方列表中），如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/fileport4.gif "建立多文件端口")

2）关闭对话框，可以发现在 Code 左侧导航栏出现一个新文件夹 "uploadfiles"，这就是刚刚创建的多文件端口 (带有 <img src="./././././media/logo/codeuifile.png" width="15" height="15"> 标记)，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/fileport5.gif "查看多文件端口")

可以发现，多文件端口与单文件端口的不同在于它会**映射为一个文件夹而非一个文件**，这个文件夹会接收用户批量上传的全部文件，开发者则可以在代码中使用该文件夹名和索引来操作用户上传的多个文件。

### 调用多文件端口

开发者可以引用多文件端口文件夹名和索引，来操作用户上传的多个文件。

将 "radial.py" 替换为以下代码并保存。

```python
import json

with open("../data.json", "r", encoding="utf-8") as f:  # 读取文件端口 data.json（注意使用相对路径）
    userdata = json.load(f)
  
print(userdata)   # 获取文件端口中的用户上传数据文件并打印
```

以上代码读取多文件端口 "uploadfiles" 功能，将读取的用户数据文件赋予 userdata 字符串，并在用户终端打印出来。

点击 <img src="./././././media/logo/codedebug.png" width="60" height="20"> 按钮，打开用户输入模块，可以发现新增添的文件输入项。我们使用云桌面上的 "flare.json" 数据，测试运行如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/fileport3.gif "测试多文件端口")

通过以上测试运行可以发现，多文件端口成功地获取了用户上传的三个 json 格式文件，并在右侧终端窗口分别打印出来。

## 删除用户界面接口

对于错误或不需要的用户界面接口，可以在`用户界面设置`对话框下方列表中删除。

只需在表中操作栏点击 <img src="./././././media/logo/codedeleteport.png" width="45" height="20"> 按钮即可。在下图示例中，我们移除了接口 "test"，可以发现其映射接口文件 "test.json" 也自动地从左侧导航栏被移除了。

![Matrix.OS](../../../../../media/os/tools/code/codedeleteport.gif "删除用户界面接口")