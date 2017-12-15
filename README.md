本教程介绍VREP的使用，及可视化模型和场景的搭建等内容。
水平有限，错误和疏漏之处敬请指正。
感谢老师和师兄的帮助。

# 安装VREP
## 下载VREP
点击下载[64位Windows版本](http://coppeliarobotics.com/files/V-REP_PRO_EDU_V3_4_0_Setup.exe)
和[64位Linux版本](http://coppeliarobotics.com/files/V-REP_PRO_EDU_V3_4_0_Linux.tar.gz)
VREP。

**Note**: 目前（2017.11）最新的VREP版本为3.4，是64位的，3.4之前的版本是32位。
推荐使用64位Linux版本VREP。
其他平台及其他版本[下载地址](http://www.coppeliarobotics.com/previousversions.html)。

## 安装和运行
Windows

- 相信大家都会。

Linux

以Ubuntu 16.04为例。
- 打开终端`cd`到下载目录，输入`$tar -zxvf V-REP_PRO_EDU_V3_4_0_Linux.tar.gz`解压*V-REP_PRO_EDU_V3_4_0_Linux.tar.gz*文件。进入VREP目录，输入`$./vrep.sh`即可打开VREP。
- 在终端输入`$gedit ~/.bashrc`，在末尾添加
`alias vrep="<vrep folder path>/vrep.sh"`并保存，随后在终端输入`$source ~/.bashrc`。
现在可以在终端直接输入`$vrep`命令来打开VREP了。

**Note**: 如果你是bit-ivrc成员，在autoSim-ivrc仓中的
[脚本](https://github.com/bit-ivrc/autoSim-ivrc/tree/master/scripts)中
包含了VREP的安装bash，可通过此bash安装，也可以通过上边的介绍手动安装。

---
# 1 VREP基础
本教程使用VREP 3.4.0 版本。
通过这部分的实例，可以快速了解VREP的基础操作。
教程中初次提到的操作会详细描述，多次提到的操作将简略说明。

**Note**: 这部分整理自bit的VREP教学视频，
视频使用的VREP版本过早，但依然具有参考价值。
百度云[下载链接](https://pan.baidu.com/s/1jIMPSsm)，密码: 8und。

## [教程1-1](https://github.com/bit-ivrc/vrep_tutorial/tree/master/demo1-1)
- 搭建小车。添加车体车轮，添加和设置转向关节。
- 编写控制脚本，实现用键盘方向键对小车进行运动控制。

## [教程1-2](https://github.com/bit-ivrc/vrep_tutorial/tree/master/demo1-2)
- 观察小车运动轨迹。观察小车速度。
- 传感器的使用。视觉传感器、距离传感器、激光雷达。


# 2 可视化模型和场景

## [教程2-1](https://github.com/bit-ivrc/vrep_tutorial/tree/master/demo2-1)
介绍VREP贴图相关操作，利用VREP的贴图可以制作出丰富的场景。
- VREP贴图相关操作。
- 制作交通标志牌。

## [教程2-2](https://github.com/bit-ivrc/vrep_tutorial/tree/master/demo2-2)
Solidworks绘制车辆模型，并将车辆模型导入VREP中。
- 从Solidworks导出STL文件。
- 将STL文件导入VREP。
- 调整各模型实体的位置和颜色并添加关节(joint)。
- 添加脚本。

## [教程2-3](https://github.com/bit-ivrc/vrep_tutorial/tree/master/demo2-3)
使用三维建模软件绘制道路并导入VREP形成可用的道路。教程中绘制道路模型的三维软件为Blender。
- Blender的安装。
- Blender的使用基础。
- 使用Blender绘制道路模型。
- 将道路模型导入VREP中形成可以仿真的道路。
- 模块化道路场景搭建。

## [教程2-4](https://github.com/bit-ivrc/vrep_tutorial/tree/master/demo2-4)
制作盘山公路，使用教程1-1中的小车进行仿真。
- 使用Blender绘制盘山公路。
- 将盘山公路导入VREP，并将公路变为仿真实体。
- 添加小车进行仿真。
