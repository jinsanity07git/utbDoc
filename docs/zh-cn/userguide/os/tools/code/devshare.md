# 协同开发

您可以将云应用或代码库作为组件分享给伙伴或团队成员实现协同开发。

## 分享开发

在云桌面，右键点击要分享的组件文件夹，在弹出菜单中选择 <img src="./././././media/logo/share2.png" width="40" height="20">，即打开`分享管理`对话框。

输入要分享的用户名，设置权限后，点击 <img src="./././././media/logo/addmember.png" width="40" height="20"> 按钮，即可完成将用户添加到分享列表。

分享成功后，被分享的组件上则会显示 <img src="./././././media/logo/sharebutton.png" width="20" height="20"> 图标。如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/sharedev.gif "分享组件开发")

## 锁定/释放开发权限

组件分享后，为了避免多个用户对组件中同一代码同时进行操作所导致的数据错误，Code 提供了 "开发权限锁定" 功能。

组件被某一用户锁定开发权限后，其他成员对该组件仅有`只读`权限，直到锁定的开发权限被释放。

点击 Code 导航栏顶部 <img src="./././././media/logo/lockbutton.png" width="20" height="20"> 或 <img src="./././././media/logo/unlockbutton.png" width="20" height="20"> 图标，可以锁定或释放组件的开发权限 (可以发现锁定前后的变化)，如下图所示：

![Matrix.OS](../../../../../media/os/tools/code/lockdev.gif "锁定释放组件开发权限")

## 分工与集成

当多个开发者对组件进行协同开发时，不同开发者可先各自在本地端完成不同功能模块的编码工作，然后通过 Terminal 或者云桌面将代码上传至组件文件夹，最后使用 Code 来完成开发集成和编译调试。


