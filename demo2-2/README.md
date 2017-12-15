# 教程2-2
本教程介绍将Solidworks绘制的车辆模型导入VREP中，使成为可以进行仿真的车辆模型。教程中使用的CAD模型文件可在demo2-2/CAD_model文件夹中找到。目录下包含两种类型的文件，`.SLDPRT`文件是使用Solidworks 2014创建的文件，`.STL`文件是一种三维图形文件格式，本例中使用这种格式进行Solidworks与VREP的文件交互。完成的模型文件为demo2-2.ttm。

**Note**: Solidworks曲线和曲面命令是车身和轮胎三维建模过程中经常用到的命令。完成的车身三维模型为`body.SLDPRT`,完成的轮胎三维模型为`wheel.STDPRT`。

## 1 Solidworks
Solidworks软件方面，假设已经完成了车身和轮胎的三维建模，得到了车身和轮胎的工程文件`body.SLDPRT`和`wheel.STDPRT`。
- 使用Solidworks打开`body.SLDPRT`，进入“过滤实体模式”，分别选择车身的各个实体，点击*文件 > 另存为*，把个实体另存为STL格式文件。
- 同样，将轮胎模型`wheel.STDPRT`各实体也另存为STL格式文件。
- 最终产生6各STL文件。`wheelhub.STL`, `tyre.STL`, `frame.STL`, `lamp.STL`, `lampshade.STL`, `windows.STL`。可在demo2-2/CAD_model文件夹中找到。

**Note**: STL格式的选项中，可以选择输出二进制或者ASCII，两种格式都可以。调节品质可调整输出精度，不宜过大，一般选择默认的*粗糙* 即可。

## 2 VREP
把上面得到的STL文件倒入进VREP，更改各部分位置和颜色，添加关节(joint)。
- 点击菜单栏的*File > Import  > Mesh* 选择上面生成的各个STL文件。在弹出的对话框中，*Mesh scaling* 表示放大比例，可以根据需要选择；有的三维建模软件采用Z轴向上，有的采用y轴向上，在*Mesh Orientation* 中对应选择。
- `wheelhub.STL`和`tyre.STL`组成车轮，共有四个车轮。`frame.STL`, `lamp.STL`, `lampshade.STL`和`windows.STL`组成车身body。
- 调整车身和车轮各部分的位置。Object/Item Translation/Position。
- 调整各部分颜色。双击Object，打开属性对话框，点击Adjust color。
- 添加关节(joint)。具体的做法请参照
[教程1-1](https://github.com/bit-ivrc/vrep_tutorial/tree/master/demo1-1)。
- 调整各Object的父子关系和名称，最终结构如下：
<br>&nbsp;\- Vehicle
<br>&nbsp;\- Vehicle_body
<br>&nbsp; &nbsp; &nbsp; \- Vehicle_rearleftMotor
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Vehicle_rearleftwheelRespondable
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Vehicle_rearleftwheelhub
<br>&nbsp; &nbsp; &nbsp; \- Vehicle_rearrightMotor
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Vehicle_rearrightwheelRespondable
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Vehicle_rearrightwheelhub
<br>&nbsp; &nbsp; &nbsp; \- Vehicle_frontleftsteeringMotor
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Vehicle_frontleftsteeringMotorpart
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Vehicle_frontleftMotor
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Vehicle_frontleftwheelRespondable
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Vehicle_frontleftwheelhub
<br>&nbsp; &nbsp; &nbsp; \- Vehicle_frontrightsteeringMotor
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Vehicle_frontrightsteeringMotorpart
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Vehicle_frontrightMotor
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Vehicle_frontrightwheelRespondable
<br>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; \- Vehicle_frontrightwheelhub
- 将对象`Vehicle_body`, `Vehicle_rearleftwheelhub`, `Vehicle_rearrightwheelhub`, 
`Vehicle_frontleftwheelhub`, `Vehicle_frontrightwheelhub`设置为可见，其余对象均为不可见。
- 添加教程1-1用到的
[脚本](https://github.com/bit-ivrc/vrep_tutorial/blob/master/demo1-1/script/script.txt)，进行按键控制。注意修改脚本中对应关节的名字。
- **开始仿真**，可以用键盘方向键控制小车运动。
- 点击*File > Save model as* 导出模型。
