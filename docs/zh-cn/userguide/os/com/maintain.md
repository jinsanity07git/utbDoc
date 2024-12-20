# 组件的运营与维护

组件发布到开放平台后，可以通过 Matrix.OS 的`发布管理`功能来对组件进行更新、重构、升级、与维护。

右键点击已发布的组件，选择 <img src="./././././media/logo/releasemanage.png" width="60" height="20">，如下图所示：

![Matrix.OS](../../../../media/os/com/releasemanagement.gif "打开发布管理")

## 组件的"状态"

点击"发布管理"对话框右上角下拉式菜单，可以设置组件不同的状态，如下图所示：

![Matrix.OS](../../../../media/os/com/releasestatus.png "组件状态")

* **上线中：**组件处于正常在线发布状态，可以在开放平台被所有用户订阅、使用、运行。全部组件内容被自动锁定，开发者不能对组件内的文件和代码进行修改，但可以对组件信息进行更新。
* **重构中：**开发者正在对组件进行重构和升级，不会影响已订阅该组件用户的使用，但是新用户暂时不能订阅该组件。组件内容解除锁定，开发者重新获得该组件的开发和修改权限。
* **下线：**组件在开放平台下线，但是不会影响已订阅该组件用户的使用。
* **取消发布：**从开放平台彻底移除组件，终止全部用户对该组件的使用，组件重回私有化状态。

## 更新组件信息

组件发布上线后，开发者可以在不影响其上线状态和既有用户使用的情况下，对组件信息进行修改和更新。打开`发布管理`对话框，保持右上角下拉式菜单中的组件状态设置为"上线中"，可以对以下组件信息进行修改：

* 封面图片
* 产品名称
* 产品标签
* 产品简介
* 收费机制和定价
* 折扣
* 组件内容可见性
* 用户对组件的操作权限

**注意：组件发布后，其"发布类别"无法进行修改。编辑修改组件信息不会影响已订阅该组件用户的使用。**

组件信息修改完成后，点击 <img src="./././././media/logo/updaterelease.png" width="60" height="20"> 按钮，即完成组件更新并自动同步到开放平台，如下图所示：

![Matrix.OS](../../../../media/os/com/releaseupdate.png "更新发布组件")

## 组件维护、重构与升级

组件的重构通常是指开发者根据用户的反馈和建议来修复组件存在的错误、提升用户体验、或增添新的功能。这往往需要对组件进行文件结构性调整和代码修改。为了不影响已订阅该组件用户的使用，开发者应将组件状态设置为"重构中"，如下图所示：

![Matrix.OS](../../../../media/os/com/releaserefactor1.png "设置组件为重构中")

点击 <img src="./././././media/logo/closebutton.png" width="35" height="20"> 按钮，退出`发布管理`，可以发现在 Matrix.OS 上，组件变为"重构中"状态，如下图所示：

![Matrix.OS](../../../../media/os/com/releaserefactor2.png "Matrix.OS上组件状态更新为重构中")

![Matrix.OS](../../../../media/os/com/releaserefactor.gif "Matrix.OS上组件状态更新为重构中")

单击进入该组件文件夹，可以发现，全部组件内容恢复为"解锁"状态，开发者就可以对其进行编辑修改或添加新的内容来重构组件。如下图所示：

![Matrix.OS](../../../../media/os/com/releaserefactor3.png "重构中组件内容恢复解锁状态")

完成对组件的重构，测试无误后，可再次打开`发布管理`对话框，点击右上角下拉式菜单，将组件状态重新设置为"上线中"，然后关闭`发布管理`对话框，这样重构后的组件就成功上线了，如下图所示：

![Matrix.OS](../../../../media/os/com/releaseagain.gif "组件重构后上线")

与此同时，所有组件的订阅用户都会收到组件升级通知，升级方法参见《[组件订阅](zh-cn/userguide/os/com/subscribe.md)》。

## 组件下线

组件下线是指组件开发者终止该组件的维护、更新与订阅，但是保留已订阅该组件用户的使用权限。一般在组件重大更新换代全新发布到开放平台后，为不影响用户使用旧版本组件而设置。

打开`发布管理`对话框，点击右上角下拉式菜单，将组件状态重新设置为"下线"，然后关闭`发布管理`对话框，即成功完成组件下线设置，如下图所示：

![Matrix.OS](../../../../media/os/com/releaseoffline.gif "组件下线")

## 取消组件发布

取消组件发布是指从开放平台彻底移除组件，终止全部用户对该组件的使用，**组件重回私有化状态，仅供开发者个人使用**。

**注意：一旦组件在开放平台被订阅，则无法取消该组件的发布。**

打开`发布管理`对话框，点击右上角下拉式菜单，将组件状态设置为"取消发布"，然后关闭`发布管理`对话框，即取消组件的发布，如下图所示：

![Matrix.OS](../../../../media/os/com/releasecancel.gif "取消组件发布")

## 组件管理和运营

组件上线后，开发者可以在开放平台实现多组件管理、用户交互与运营。

首先，进入 Matrix 开放平台个人主页，点击页面上方 <img src="./././././media/logo/products.png" width="30" height="20"> 选项卡，即进入组件产品模块。在此可以浏览您自行创建的、被分享的、和订阅的所有组件产品。如下图所示：

![Matrix.OS](../../../../media/os/com/viewproducts.gif "进入组件产品模块")

然后，点击目标组件，进入组件主页。作为组件开发者，您可以直接运行该组件、查看或发表组件动态、回复用户问题与反馈、查看和管理用户列表、以及管理开发者团队等。如下图所示：

![Matrix.OS](../../../../media/os/com/manageproduct.gif "组件管理")