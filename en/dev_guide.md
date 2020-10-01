



## 基础

目录：

[TOC]



### 起步

#### 申请帐号

#### 新建装备

- 对象：一个以问卷为载体的数据收集，可以用于众包的问卷调查。
- 程序：一个以问卷为交互，以程序脚本驱动的在线应用，可以用于实现特定程序功能。

此教程目标以`你的第一个小程序`为例子，帮助开发人员快速上手从装备创建，装备开发，到本地调试，在线调试以及在线发布的全过程。

你的第一个小程序：

在左侧`新建装备`栏下点击`程序`，即可弹出新建程序窗口，按下图所示填写装备名称，装备标签和装备简介，最后点击确认完成装备创建。

![image-20190220222733539](https://ws4.sinaimg.cn/large/006tKfTcly1g0novk2pijj30j20fsdgt.jpg)

#### 创建组件

在`组件`栏中点击:heavy_plus_sign: 号，开始创建新的组件，在对话框中输入组件的名称`Hello Utopia`，选择程序开发语言。 点击确认完成组件创建。

![image-20190228140114062](https://ws1.sinaimg.cn/large/006tKfTcly1g0mrxe1r1aj309g05pjrw.jpg)

#### 编辑权限

平台支持装备的开发和分享，用户需要获取`编辑权限`后才能对装备进行开发，一旦装备中组件的处于被编辑状态，只能由该成员进行编辑。

### 装备构成

在获取编辑权限后，开发者可以在`齿轮` :gear: 选项中定义装备的配置，初始配置如下图所示：

![image-20190220212227437](https://ws1.sinaimg.cn/large/006tKfTcly1g0mrnp3kymj305k0e0t9c.jpg)

#### 配置输入格式

组件的输入格式是Utopia独创的用户交互界面—`问卷`，涵盖了十余种题型，各种题型之间灵活的排列组合可以满足大多数程序的输入需求，方便，快捷地从用户端获取数据。 

![image-20190228140935877](https://ws1.sinaimg.cn/large/006tKfTcly1g0ms66uuotj30b70g6ta3.jpg)



`题型设置`: 在`Hello Utopia` 组件中仅需要一个`文件上传`题型，通过编辑按钮进行以下编辑：

- 将Id设置为’content‘，
- 问题设置为'请上传一个txt文件,该程序可将文本转换成ACSII艺术字体(目前只支持英文）'，
- 文件类型限制为‘txt’格式，
- 提示出输入”英文输入“
- 将文件数量设置为不大于500KB
- 点击`完成`按钮完成题型设置，
- 再点击右上角` 保存` 按钮完成问卷设置

![image-20190301082213843](https://ws1.sinaimg.cn/large/006tKfTcly1g0nnqyzao5j30dz0gp0uc.jpg)

`Tab修改`: 在完成题型设置后，可以点击`分页栏`的:gear: 处，根据开发需求修改分页的名称，​修改界面如下图所示，单机确认即可完成修改。

![image-20190301082619582](https://ws4.sinaimg.cn/large/006tKfTcly1g0nnv8t8atj30dv07e75e.jpg)

![image-20190301082748396](https://ws3.sinaimg.cn/large/006tKfTcly1g0nnwrzj5rj30cm05jwep.jpg)

`题型设置`和`Tab修改`结束后，单机左上角的`保存`按钮，系统提示操作成功即编辑完成。

问卷的参数存储格式为一个json文件，点击右上角`预览`按钮即可查看用户视角下的问卷，再次点击右上角`预览`按钮，可以看到该问卷所对应的json文件，该文件可以下载到本地，用于本地的开发测试。



#### 输出格式

每一个组件都会对应一个输出文件，目前支持的输出文件有（html,txt,csv,png）四种格式。

- `Hello Print` 组件需要将输出格式设置成`txt格式` 

- 组件的输出格式需要与脚本中的输出格式对应

- 每个组件只支持一种格式的输出作为结果呈现形式

  - 程序支持多个输出文件，可以通过脚本将输出文件整合到一个呈现形式中

  ![image-20190301163843831](https://ws1.sinaimg.cn/large/006tKfTcly1g0o23k6l7pj309g04gdgn.jpg)



#### 数据文件 

`数据文件`主要用于执行文件中模板和特定参数的配置，方便开发人员对程序进行版本更新和模式修改。目前支持 "csv, xlsx, json, dat, txt" 的文件扩展名。

- 支持多个文件的上传

- 例子：

  - 数据文件`data_file`： 1）slogan.txt 2）mission.txt

  - ```python
    ## slogan.txt
    乌托邦：要理想，不空想
    
    ## mission.txt
    专为中国专业人士和组织打造的知识一站式服务平台
    ```

  - 

![image-20190228160859749](https://ws2.sinaimg.cn/large/006tKfTcly1g0mvmbrpz6j309g06mdg0.jpg)

文件对接配置

```python
# n>=0， k>=m>=0
### 数据文件(配置文件)
data_file[1]... data_file[n] = sys.argv[1]...sys.argv[n] 

### 输入格式文件(json文件)
config_data=sys.argv[n+1]   

# 用户读取的文件 file_(n+1+m),..., file_(n+1+k) 对应 
inputdata[n+1+m] ... inputdata[n+1+k] = sys.argv[n+1+m],..., sys.argv[n+1+k]   

# 输出文件(对应输出格式)
outdata = sys.argv[n+1+k+1]
```

说明：

- 脚本中变量 `n, k,m `为平台根据用户上传的个数**自适应**生成
  - 开发人员只需要根据自己上传的文件数在脚本中调整相对应的参数

#### 执行文件

执行文件是一个用于实现组件功能的程序脚本，为了在平台端能够实现所需的功能，脚本的撰写需要遵循平台的开发模板，主要分为`规定代码`和`核心代码`两块，通过5个步骤实现：

1. 导入执行脚本所需的包

   ```python 
   ##规定代码：对接云平台所需的包
   import json
   import sys
   ##脚本核心代码所需的包
   import pyfiglet
   ```

   

2. 对接装备文件集

   ```python
   #规定代码：
   #n 为开发者配置文件的个数
   n = 2
   #k 为输入文件的个数,可以为0
   #m 为输出文件的索引
   k = 1
   m = k + 1
   
   ## 读取开发者上传的配置文件，
   ## 根据所需文件个数调整相应参数n
   data_file_1 = sys.argv[1]
   data_file_n = sys.argv[n]
   
   ## 读取问卷的配置文件
   config_data=json.loads(sys.argv[n+1])
   
   ## 读取用户上传的配置文件
   ## 根据所需文件个数调整相应参数n
   inputdata = sys.argv[n+1+k]
   
   ## 定义输出文件的名称
   ## 根据所需文件个数调整相应参数m,现阶段只支持一个输出文件
   outdata = sys.argv[n+1+m]
   ```

3. 脚本核心代码

   ```python
   ##读取配置文件1，存储为字符串格式到变量slogan
   with open(data_file_1, 'r', encoding='utf-8') as myfile:
     slogan = myfile.read()
   
   ##读取配置文件2，存储为字符串格式到变量smission
   with open(data_file_n, 'r',encoding='utf-8') as myfile:
     mission = myfile.read()
   
   ##核心代码，使用函数figlet_format讲字符串字体装换成ASCII格式的艺术字体
   with open(inputdata, 'r',encoding='utf-8') as myfile:
     content = myfile.read()
   
   head = pyfiglet.figlet_format(content, font = "slant"  )
   ```

4. 生成输出文件

   ```python 
   ##将所有字符串整合到输出文件：output.txt
   with open(outdata,'w') as f:
       print(head,file=f)
       print('#'*20,file=f)
       print(slogan,file=f)
       print('#'*20+'\n'+'使命：' ,file=f)
       print(mission,file=f)
   ```

5. 脚本结尾

   ```python
   # 规定代码：脚本最后必须打印'1'
   print("1")
   ```

##### 注意事项

- 三个必须：
  - 平台支持多个执行文件的上传，但是主程序必须以`main.py`命名
  - 脚本的结尾必须打印‘1’ ，用于告知平台脚本执行完毕
  - 脚本中必须包含配置文件对对应的接口，以正确读取文件
- 常见问题：
  - 未能找到脚本核心代码所需的包： 
    - 需要联系平台方安装
  - 需要调用系统层级的软件
    - 需要联系平台方配置
  - 未能找到某项函数
    - 检查相关包的版本是否与本地端一致
  - matplotlib 中Plt() 函数不能生成输出文件，且会导致程序无法运行出结果
    - 删除plt()相关代码，用figure.save()代替

### 本地开发

#### 推荐开发套件

- 代码编辑器： 1) Notepad++  2) Brackets 3) Sublime 4)Atom
- 脚本测试软件：1) [nteract](https://nteract.io/)  2) Jupyter Notebook 3) Terminal 

#### 本地调试范式

1. 新建文件夹，通常以组件名称命名
   - eg. 1stProgramm

![image-20190301090549458](https://ws1.sinaimg.cn/large/006tKfTcly1g0np0bscokj302a02jglk.jpg)



2. 在该文件夹下，按照需求准备数据文件和用户输入文件
   eg. 1）slogan.txt 2）mission.txt

3. 按照执行文件模板撰写脚本，命名`main.py`
   ![image-20190301090627308](https://ws1.sinaimg.cn/large/006tKfTcly1g0np0yu8hkj30d5050mxo.jpg)

4. 在该文件夹下创建一个新的ipynb文件，用本地命令行代码模拟平台代码运行机制。![image-20190228165238267](https://ws2.sinaimg.cn/large/006tKfTcly1g0mwvpr22nj30p903174f.jpg)

   ```
   !python main.py slogan.txt mission.txt '{"basic_config": "json"}' content.txt output.txt
   
   ```

   - 命令行解释：

     - ```python
       # n = 2
       #k 为输入文件的个数
       #m 为输出文件的索引      k = 1  m = k + 1
       !python : 		在notebook中调用Python解释器
       main.py : 		sys.argv[0]; 执行文件
       slogan.txt ： 	sys.argv[1]; 数据文件1
       mission.txt：	sys.argv[2]; 数据文件2
       ’字符串‘：		  sys.argv[3]; 问卷生成的json,命令行中需要为json形式的字符串
       content.txt： 	sys.argv[4]；输入文件1
       output.txt：		sys.argv[5]；输出文件1
       ```

   - 输出结果为’1‘， 则代表程序运行成功

本地端输出结果：

```
    __  __     ____         __  ____              _      
   / / / /__  / / /___     / / / / /_____  ____  (_)___ _
  / /_/ / _ \/ / / __ \   / / / / __/ __ \/ __ \/ / __ `/
 / __  /  __/ / / /_/ /  / /_/ / /_/ /_/ / /_/ / / /_/ / 
/_/ /_/\___/_/_/\____/   \____/\__/\____/ .___/_/\__,_/  
                                       /_/               

####################
乌托邦：要理想，不空想

####################
使命：
专为中国专业人士和组织打造的知识一站式服务平台

```



注意：

- `你的第一个小程序` 例子中未涉及到Config.json文件, 关于问卷配置以及如何配合程序解析问卷的脚本编写可以参见一个可视化小工具例子[link]()



### 发布前的准备

一旦开发者按照模板完成配置之后，即可上传执行文件，点击`上传` 按钮上传成功后即可`调试运行`。

![image-20190228171325857](https://ws1.sinaimg.cn/large/006tKfTcly1g0mxhcyg1aj309g05pglu.jpg)

#### 调试运行

首先网页端会显示一个之前所配置的问卷，上传content.txt文件到指定框中，单击`上传`，上传完成后即可点击右上角`运行`按键。

![image-20190301083737953](https://ws2.sinaimg.cn/large/006tKfTcly1g0no6z4jqaj30a50fr0tc.jpg)

#### 错误提示

当程序运行不成功时，可以点击右上角的 :heavy_exclamation_mark: ​ 按键查看错误信息。

- 本例子中的错误信息显示：平台环境缺少‘pyfiglet’的包支持，需要额外安装
- 解决方法：在线修改代码来安装缺少的包——pyfiglet

![image-20190228172218684](https://ws1.sinaimg.cn/large/006tKfTcly1g0mxqlxhfyj30i0080gma.jpg)

#### 在线修改

按照上述步骤新建一个装备用于安装包，可以省略输入格式，数据文件的配置，只需要将输出文件设置为txt格式以及配置执行文件。

配置执行文件时可以选择在线创建或者本地上传两种形式：

![image-20190228231643658](https://ws3.sinaimg.cn/large/006tKfTcly1g0n7ze7w60j312e0qqgp6.jpg)

在线配置：

![image-20190228231211237](https://ws3.sinaimg.cn/large/006tKfTcly1g0n81z1jtdj30m00kcmzo.jpg)

本地上传：

```python
#请编辑您的代码
import sys

# 规定代码：代码前置
#以下代码为I/O operation，其结果可以在系统级保存
#至输出文件，但是不会被平台识别
print ('1')

outdata = sys.argv[2]
sys.stdout = open(outdata, "w")

try:
    from pip import main as pipmain
    print ('在python2下安装包')
    pipmain(['install', 'pyfiglet'])
    print ('安装成功')

except ImportError:
    from pip._internal import main as pipmain
    print ('在python3下安装包')
    pipmain(['install', 'pyfiglet'])

    print ('安装成功')
 
print('task completed'),
print ('#########################################')
sys.stdout.close()
```

第一次成功安装会显示如下结果：

```
在python3下安装包
Collecting pyfiglet
  Downloading https://files.pythonhosted.org/packages/33/07/fcfdd7a2872f5b348953de35acce1544dab0c1e8368dca54279b1cde5c15/pyfiglet-0.8.post1-py2.py3-none-any.whl (865kB)
Installing collected packages: pyfiglet
Successfully installed pyfiglet-0.8.post1
安装成功
task completed
#########################################
```

重复安装已安装的包会显示如下结果：

```
在python3下安装包
Requirement already satisfied: pyfiglet in c:\users\administrator\appdata\local\programs\python\python35\lib\site-packages (0.8.post1)
安装成功
task completed
#########################################
```

再次尝试运行`你的第一个小程序 ` 中的`Hello Utopia`组件，程序运行成功之后会在新的页签中显示如下内容：(注意：如浏览器设置自动拦截新窗口的弹出，用户需手动取消该设置以查看结果)。

![image-20190301083923488](https://ws3.sinaimg.cn/large/006tKfTcly1g0no8v67zaj30bn0duab0.jpg)

### 上线

#### 示例展示

成功运行程序后，开发人员可以将该装备配置文件，执行文件和输出文件保存成一个示例，以供使用人员参考。点击右上角`保存示例`即可完成。保存成功后，组件的设置栏当中会出现`示例展示`选项。

![image-20190301084401683](https://ws1.sinaimg.cn/large/006tKfTcly1g0nodnc6lnj306209vmxk.jpg)

 



#### 成员管理

在正式发布装备之前，通常需要在开发成员之间完成几轮内测。在uDev平台的装备中添加多个成员需进行以下操作：

- 在左侧`你的第一个小程序`装备信息栏下单击`成员管理`![image-20190301085057423](https://ws1.sinaimg.cn/large/006tKfTcly1g0nol6k3rgj306s0dg74r.jpg)
- 在搜索框中输入成员用户名或者账号信息，选择成员身份，点击分享即可完成成员添加![image-20190301085357224](https://ws3.sinaimg.cn/large/006tKfTcly1g0nonzkmq2j30bn061aah.jpg)
- 随后，在`组件`中的:gear: 选项中​点击成员管理，选择分享给装备内的人员，设置相应权限，点击分享即可完成组件分享![image-20190301085826236](https://ws4.sinaimg.cn/large/006tKfTcly1g0nosmovjoj30bl076gm6.jpg)

