# 教程2-3
本教程介绍三维建模软件Blender的安装和使用。使用Blender绘制道路模型，并将其导入VREP中形成可以进行仿真的道路。  
图片素材、中将过程文件及完成文件均可在文件夹demo2-3/下找到。教程用到的图片素材 在demo2-3/texture/下获得，更多素材和模型可在demo2-3/other目录下找到。中间文件 ，Blender文件`road_segment.blend`在demo2-3/blender/下，OBJ文件`road_segment.obj`在demo2-3/obj/下。教程完成文件`demo2-3.ttm`，在文件夹demo2-3/下可以获得。

**Note**: 本例通过obj格式文件与VREP进行文件交互，与STL格式文件相比，增加了模型的texture属性。

## 1 Blender的安装和使用
### 1.1 Blender的安装
到Blender[官网](https://www.blender.org/download/)下载和安装最新版本的Blender。教程中使用的Blender版本为Blender 2.79，环境为Ubuntu 16.04。

### 1.2 Blender的使用
[这里](http://www.bilibili.com/video/av909518/)有非常详细地Blender中文视频教程。

### 1.3 道路模型
假设你已经具备使用Blender建模的能力。
- 绘制一小段道路。
- 添加材质。
- 添加贴图。使用提供的图片素材。
- 将模型导出为obj格式。*File > Export > Wavefront*

**Note**: 注意obj格式的导出选项，为保证贴图存在，建议在*Path Mode* 中选择*Relative*。

## 2 模型导入VREP
### 2.1 让三维模型可参与仿真
- 导入obj文件，步骤和[教程2-2](https://github.com/bit-ivrc/vrep_tutorial/tree/master/demo2-2)中导入STL文件过程类似。检查贴图是否存在。
- 添加地板。obj模型默认只是可见，但不发生物理学关系。通过*Add > Primitive shape* 进行排列组合，形成可发生物理关系的地板。
- 导出VREP模型文件。

### 2.2 模块化道路编辑
可以制作多个模块化的道路模型，如短直道、长直到、十字路口、T字路口等。为了方便的进行排列组合，需要对这些模型文件进一步的修改。
- 在上一步的VREP道路模型的基础上添加Dummy点，用来代表模型的位置。最终文件为demo2-3/下的`road_segment.ttm`文件。
- 编写排列道路组合模块。使用该模块对多个模块化的道路进行排列组合。bit-ivrc成员详见[此仓](https://github.com/bit-ivrc/autoSim-ivrc)中的内容。
