# 教程1-2
本教程使用教程1-1搭建的小车，可在本教程目录demo1-2/scene文件夹中，
或在demo1-1/文件夹中获得demo1-1.ttt文件。
将介绍如何显示小车的运动轨迹，及传感器的使用。已完成的文件demo1-2.ttt，可在demo1-2文件夹中获得。

首先，打开vrep，点击菜单*File > Open scene*，选择demo1-1.ttt文件。

## 1 Gragh的使用
### 1.1 显示小车运动轨迹
- 点击菜单栏的*Add > Graph*，改名为Vehicle_Graph，拖到Vehicle下。弹出的窗口先不管。
为了不与地板重合，调整z坐标为0.05。
- 打开Vehicle_Graph的属性对话框，点击*Add new data stream to record*，对话框中
*Data stream type*项选择Object: absolute x-position，
*Object/item to record*选择Vehicle_Graph，
相同，把物体的y，z位置绝对也添加进Vehicle_Graph。
- 把列表中的Data, Data0, Data1重命名为Data_x_vehicle, Data_y_vehicle, Data_z_vehicle。
- 将Data stream recording list的三个数据全部勾选掉*visible*。
- 点击*Edit 3D curves*，接着点击*Add new curve*，xyz值分别对应
Data_x_vehicle, Data_y_vehicle, Data_z_vehicle。勾选*Relative to world*，
设置*curve width*为4
- **开始仿真**，用按键控制小车运动，即可观察到小车的运动轨迹。

**Note**: 可通过*Edit 3D curves*中*Adjust color*按钮，设置曲线颜色。

### 1.2 观察小车速度
- 在Vehicle_Graph的属性对话框中再添加一条数据，
将Object: absolute velocity添加进Vehicle_Graph。保持Visible勾选。改名为velocity。
- 运行仿真，可看到小车的速度在Vehicle_Graph窗口Time graph选项卡下显示。

**Note**: 可通过*Adjust curve color*按钮，，设置曲线颜色。

## 2 传感器
### 2.1 视觉传感器
- 添加4个Cylinder作为障碍物，放在小车前方。Cylinder的x,y,z尺寸均为0.3。
- 点击菜单栏的*Add > Vision sensor > Perspective type*，更改位置，
x为0，y为-0.55，z为+0.25。旋转，Alpha为90。并将其拖入Vehicle树下。
- 打开Vision_sensor的属性对话框。Near/far clipping plane为0.01/2，
Persp. angle为45，Resolution X/Y为256/256。注意观察变化。
- 打开Cylinder的属性对话框，在shape选项卡下，打开*dynamic properties*，
勾掉*body is dynamic*。其他三个Cylinder相同。
在Common选项卡下，勾上Collidable, Measuable, Detectable, Renderable。
其他三个Cylinder相同。
- 选中Vision_sensor，在场景中*右键 > Add > Floating view*，
在出现的Floating view上*右键 > Associate view with ... version sensor*。
- **运行仿真**，即可在视图窗口中看到视觉传感器检测到的物体。
- 打开Vision_sensor属性对话框，点击*show filter dialog*，
选择*edge detection on work image*，点击*add fliter*，并将此fliter顺序调到第二位。
双击fliter可设置阈值。
- **运行仿真**，可看到上述窗口显示了物体的边缘。
- 隐藏Vision_sensor物体。打开属性对话框，在Common选项卡下layer第二层打勾。

**Note**: 在设置Object/item属性及参数的时候注意理解其中的含义。

### 2.2 距离传感器
- 点击菜单栏的*Add > Proximity sensor > Cone type*，使用*Apply to selection*
将Proximity_sensor进行与Vision_sensor相同的*平移*和*旋转*。
- 打开属性对话框，设置*detection parameters*，仅保持前四项勾选。第四项角度为45。
设置*detection volume properties*，更改Range为0.5，Angel为30，其他保持不变。
- 将Proximity sensor拖到Vehicle树下并改名为sensingNoise。
- 打开Vehicle_Graph对话框，*add new data stream to record*，
Proximity sensor: detection distance对应sensingNoise。并将data改名为distance_obstacle。
- 更改distance_obstacle的curve颜色为绿色，与velocity的红色curve保持区分。
- **开始仿真**，移动小车，可按到Vehicle_Graph窗口中出现红绿两条曲线。

**Note**: 在设置Object/item属性及参数的时候注意理解其中的含义。

### 2.3 激光雷达
- 添加两个Cuboid，xyz为0.1, 0.7, 0.8。作为障碍物，移动到小车两侧。
- 打开Cuboid的属性对话框，在shape选项卡下，打开*dynamic properties*，
勾掉*body is dynamic*。在Common选项卡下，勾上Collidable, Measuable, Detectable, Renderable。另外一个Cuboid相同。
- 点击Model browser的components > sensor将velodyneHDL_64E_S2拖入scene中。
- 沿着z轴将激光雷达移动到小车车身上方。并将激光雷达拖到Vehicle树下。
- **运行仿真**，可看到激光雷达工作。在激光雷达的脚本中，可更该频率参数。
的在激光雷达树下vision sensor的属性对话框中可更改与激光雷达有关的其他参数。

**Note**: 注意理解各项参数的含义。
