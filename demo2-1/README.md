# 教程2-1
本教程介绍VREP贴图相关的操作。提供一个示例，通过VREP贴图操作制作一个路牌。教程中使用的图片素材可在demo2-1/texture文件夹中获得，使用的CAD模型可在demo2-1/CAD_model中获得。已完成的文件demo2-1.ttm，可在demo2-1文件夹中获得。不同于前面两个教程，本教程的完成文件.ttm文件是模型文件。点击菜单栏 *File > model* 可载入.ttm文件。

**Note**: 本教程不对CAD模型的格式作过多说明，关于CAD模型的说明请看后面的教程。

## 1 添加CAD模型
### 1.1 导入CAD模型
- 点击菜单栏的*File > Import > Mesh*，导入demo2-1/CAD_model文件夹下的所有模型。在VREP中显示为STL_Imported和STL_Imported0，将其改名为part1和part2。
- 点击菜单栏的*Add > Primitive shape*，添加一个Cuboid和Cylinder，分别改名为part3和part4。
### 1.2 调整模型的位置和色彩
- 调整part1，part2和part3，part4的大小和位置，使之组成一个路牌。
- 可对每一个Mesh和Shape调整色彩。打开Object的属性对话框，点击*Adjust color*进行调整。

## 2 添加图片
### 2.1 导入图片
- 在Shape上添加texture，让模型变得更加逼真。打开part3和part4的属性对话框，点击*Adjust texture*。
- 在弹出的对话框中点击*Load new texture*，part3选择town1.png，part4选择bus_stop.png。
- *Scale textures to*决定图片在VREP中的放大倍数，越大越清晰，但文件大小会变大。

**Note**: 支持导入的图片格式有JPEG, PNG, TGA, BMP, TIFF, GIF。

### 2.2 调整图片
- 在texture对话框值对导入的图片进行大小和位置的调整。
- 映射的[相关解释](http://www.coppeliarobotics.com/helpFiles/en/textureDialog.htm)。 贴图操作是将位图投射到一个Shape上，VREP提供几种投射纹理的方法（Mapping mode）: 投影映射、圆柱映射、球形映射，立方体映射。可根据需要选择合适的映射方式。

## 3 导出模型
- 选中part1, part2, part3和part4。右键*Edit > Grouping / Merging > Group selected shapes*进行合并，并重命名为guidepost。
- 打开guidepost1属性对话框，选择*Object is model based*。
- 点击*File > Save model as* 导出模型。
