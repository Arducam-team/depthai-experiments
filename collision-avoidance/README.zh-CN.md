[英文文档](README.md)

# 避免碰撞

该实验的目的是检测车辆向摄像头移动，并警告用户是否可能通过危险通道

## DepthAI购买渠道

购买DepthAI(请参见 [淘宝](https://item.taobao.com/item.htm?id=626257175462))

## 安装依赖

```
python3 -m pip install -r requirements.txt
```

## 运行程序

```
python3 main.py
```

## 背景

碰撞的计算过程取决于OAK-D摄像机提供的深度信息。

尽管我们可以在3D坐标中进行操作，但实际上大多数计算都是在2D中进行的，仅考虑x(水平)和z(深度)


在以下情况下可能会发生冲突：
- 汽车轨迹指向摄像头
- 车速以及因此影响的时间低于阈值

如果满足这两个条件，我们将在预览窗口中显示一条警告消息。

所有这些计算都在`crash_avoidance.py`文件内部完成。

我们还需要在帧之间保留有关对象的信息，以便我们实际跟踪在图像上行驶的汽车，不仅检测它们，因此在`tracker.py`代码中将图像上检测到的汽车分配给了先前检测到的汽车位置