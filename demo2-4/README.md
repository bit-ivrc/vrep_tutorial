# 教程2-4
本教程介绍使用三维建模软件Blender绘制盘山公路的基本步骤，然后将三维模型导入VREP，将公路变成实体，添加**教程1-1**搭建的[VREP小车模型](https://github.com/bit-ivrc/vrep_tutorial/tree/master/demo1-1), `demo1-1.ttm`进行仿真。  
图片素材、中将过程文件及完成文件均可在文件夹demo2-4/下找到。教程用到的图片素材 在demo2-4/texture/下获得。中间文件，Blender文件在demo2-3/blender/下，OBJ文件在demo2-3/obj/下。教程完成文件`demo2-4.ttm`，在文件夹demo2-4/下可以获得。



## 1 Blender盘山公路建模
这部分可参考[视频教程](https://www.youtube.com/watch?v=BJeV8djtlyU)，下面整理主要步骤。

### 1.1 建立一小段路
可使用教程2-3完成的[Blender道路模型](https://github.com/bit-ivrc/vrep_tutorial/tree/master/demo2-3/blender), `road_segment.blend`进行接下来的工作。

### 1.2 雕刻一座小山
- 添加网格。
- 进入雕刻模式进行小山的雕刻。
- 平滑处理和细分表面。

### 1.3 形成盘山公路
- 添加曲线，调整道路形状。曲线形状要和山地相匹配。
- 添加一个平面(plane)，让这个平面沿着曲线重复。*Add modifier > Array*, *Add modifier > Curve*。
- 让平面与山地产生包裹。*Add modifier > Shrinkwrap*。
- 进行道路形状位置的 调整。
- 进行平滑处理。
- 让一小段路和平面一样，沿着曲线重复。*Add modifier > Array*, *Add modifier > Curve*。
- 进行调整，应用这些modifier，最后导出OBJ文件。*File > Export > Wavefront*

**Note**: 我们现在有三个网格构成的实体，分别是山地、平面沿曲线重复形成的道路、一小段路沿平面形成的道路，为便于描述，分别记为实体1、实体2、实体3。

## 2 模型导入VREP
### 2.1 让道路可以参与仿真
- 导入obj文件.注意检查贴图是否存在，是否清晰。
- 可以看到导入了3个实体，打开实体3属性对话框，点击*Show dynamic properties dialog*，勾选*Body is respondable*。

### 2.2 进行仿真
- 添加**教程1-1**搭建的[VREP小车模型](https://github.com/bit-ivrc/vrep_tutorial/tree/master/demo1-1), `demo1-1.ttm`。
- 调整小车的大小和位置，使与道路大小匹配。
- **开始仿真**，可以用键盘方向键控制小车沿着盘山公路行驶，并通过多个窗口观察小车运动情况。
