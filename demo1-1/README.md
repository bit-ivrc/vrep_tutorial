# 教程1-1
本教程介绍一个小车的搭建过程，通过编写脚本实现用键盘方向键对小车的控制。
脚本可在demo1-1/script中获得，已完成的文件demo1-1.ttt，可在demo1-1文件夹中获得。

## 1 搭建小车
### 1.1 车体和四个滚动轮
- 点击菜单栏的*Add > Primitive shape > Cuboid*，在弹出的对话框中
分别设置x,y,z参数为0.3, 1.1, 0.1，其他参数保持默认，点击OK。
- 点击*Add > Primitive shape > Cylinder*，在弹出的对话框中
设置x,y,z参数为0.3，其他参数保持默认，点击OK。
- 选中Cylinder，点击工具栏的*object/item rotate*，点击*Orientation*将beta值改为90。
- 选中Cylinder，点击工具栏的*object/item shift*，将*Position*下x,y,z坐标值改为0.4, -0.35, +0.05。
- 点击菜单栏的*Add > Joint > Revolute*，双击Revolute_joint图标，
在弹出的属性框点击*Show dynamic parameters dialog*,勾选*Motor enable*，
并设置*Target velocity*为10，*Max. torque*为20。关闭对话框。
- 选中Revolute_joint，点击工具栏的*object/item rotate*，点击*Orientation*将beta值改为90。
- 依次选择Revolute_joint和Cylinder，点击工具栏的*object/item shift*，
点击*Position*下的*Apply to selection*。此步骤设置Revolute_joint与Cylinder位置相同。
- 拖动Cylinder到Revolute_joint下，再拖动Revolute_joint到Cuboid下，形成一个树状结构。
- 将Cylinder和Revolute_joint作为整体进行复制，粘贴3次，并将复制出来的3个车轮和Joint拖到Cuboid下。
- 选中Revolute_joint0，点击工具栏的*object/item shift*，将*Position*下x值改为-0.4。
此时树下的Cylinder0会跟着进行位置变换。
- 相同的操作，将Revolute_joint1的y值改为+0.35；将Revolute_joint2的x,y值改为-0.4, +0.35。
- 选中Cuboid，进行位置变换（简略了操作说明），在*Mouse Translation*下选择*World*和*along Z*，用鼠标进行拖动；
也可在*Position*下直接更改z值改为0.175。此时树下的所有结构都一起做了位置变换。
- 双击Cuboid图标，在弹出的属性框*Common*选项卡下勾选*Object is model base*。
- 选中ResizableFloor_5_25，将size拉到最大。点击工具栏的*start/resume simulation*，可观察到小车在缓慢行驶。
- 更改shape和joint的名字。名字和结构如下。名字与脚本对应，非常重要。
<br>&nbsp;\- Vehicle
<br>&nbsp; &nbsp; &nbsp; \- Front_left_joint
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Front_left_wheel
<br>&nbsp; &nbsp; &nbsp; \- Front_right_joint
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Front_right_wheel
<br>&nbsp; &nbsp; &nbsp; \- Rear_left_joint
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Rear_left_wheel
<br>&nbsp; &nbsp; &nbsp; \- Rear_right_joint
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Rear_right_wheel
### 1.2 使两个前轮转向
- 添加一个Cuboid，参数默认，和一个Revolute_joint。依次选中Cuboid和Front_left_joint，
进行shift变换*Apply to selection*和rotate变换*Apply to selection*；
依次选中Revolute_joint和Front_left_joint，进行shift变换*Apply to selection*。
- 将Cuboid拖到Revolute_joint下，将Cuboid和Revolute_joint作为整体复制1个出来。
- 将Revolute_joint和Revolute_joint0拖到Vehicle下，将Revolute_joint0坐标x值改为-0.4。
- 将Front_left_joint拖到Cuboid下，将Front_right_joint拖到Cuboid0下，并改名。现在的结构如下所示。
<br>&nbsp;\- Vehicle
<br>&nbsp; &nbsp; &nbsp; \- Rear_left_joint
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Rear_left_wheel
<br>&nbsp; &nbsp; &nbsp; \- Rear_right_joint
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Rear_right_wheel
<br>&nbsp; &nbsp; &nbsp; \- Steer_left_joint
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Cuboid
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Front_left_joint
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Front_left_wheel
<br>&nbsp; &nbsp; &nbsp; \- Steer_right_joint
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Cuboid0
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Front_right_joint
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Front_right_wheel
### 1.3 属性框参数设置
- 打开Cuboid属性对话框，点击*Show dynamic parameters dialog*勾掉*Body is respondable*，
并在属性对话框中的*Common*选项卡下，将*Camera visibility layer*勾掉上边的勾，在下面打勾，将其设为隐藏。
对Cuboid0进行相同的设置。
- 打开Steer_left_joint属性对话框，点击*Show dynamic parameters dialog*，勾上*Motor enable*和*Control loop enable*，将Max. torque设置为1000。对Steer_right_joint的属性进行相同的设置。
- 打开Front_left_joint属性对话框，点击*Show dynamic parameters dialog*，勾上*Motor enable* 并改变Target velocity为0，Max. torque为200。对Front_right_joint进行相同的设置。
- 打开Rear_left_joint属性对话框，点击*Show dynamic parameters dialog*，勾掉*Motor enable*。对Rear_right_joint进行相同的设置。
- **开始仿真**，点击工具栏的start/resume simulation，小车不动，因为我们把速度设为了0。

## 2 编写控制脚本
- 选择Vehicle，点击菜单栏的*Add > Associated child script > Threaded*。
- 双击Vehicle右侧的图标，编写lua控制脚本。
本教程提供了一个lua
[脚本](https://github.com/bit-ivrc/vrep_tutorial/blob/master/demo1-1/script/script.txt)，
将内容粘贴进去即可。
- **开始仿真**，可以用键盘方向键控制小车运动。

**Note**: VREP的脚本为lua语言，关于lua可查阅
[lua教程](http://www.runoob.com/lua/lua-tutorial.html)。
关于VREP的API的使用可查看VREP
使用手册中API的[介绍](http://www.coppeliarobotics.com/helpFiles/en/apisOverview.htm)。
