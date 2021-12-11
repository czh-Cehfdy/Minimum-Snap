# Minimum Snap

算法细节，请参考我的博客[《【附源码和详细的公式推导】Minimum Snap轨迹生成，闭式求解Minimum Snap问题，机器人轨迹优化，多项式轨迹路径生成与优化》](https://blog.csdn.net/u011341856/article/details/121861930)

## 1. 介绍

该仓库主要是对Minimum Snap算法进行实现。

具有以下功能：

- 可以通过Rviz选择空间点，然后自动生成光滑的多项式曲线；
- 具有前端轨迹搜索，到后端光滑轨迹生成功能。

## 2. 编译

```shell
cd Minimum-Snap/
catkin_make -j8
```

## 3. 运行

**通过Rviz生成轨迹**

```shell
source devel/setup.zsh
roslaunch waypoint_trajectory_generator test.launch
```

运行之后，会自动打开Rviz，并自动加载插件。

使用方法：点击`3D Nav Goal`按钮，然后鼠标左键点击Rviz中的位置，左键不松，继续点击右键控制箭头的高度，同样的方法选择至少三个点，然后以一个高度为负的箭头结束，将自动生成一条光滑的轨迹。

![minimum_snap](doc/minimum_snap.gif)

**A star + Minimum Snap**

为了更加接近实际工程使用，帮助大家去更深入了解，我实现了一个比较完整的仿真实验环境，它具有随机二维地图生成功能，前端A star路径搜索功能，后端Minimum Snap轨迹生成。

```shell
source devel/setup.zsh
roslaunch trajectory_generator run_minimum_snap_2d.launch
```

使用方法：点击Rviz中的`2D Pose Estimate`，然后鼠标左键点击地图的任意位置，将会生成光滑的轨迹。

![A_star+minimum_snap](doc/A_star+minimum_snap.gif)