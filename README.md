# AutoTrackControl_ROS1
NUDT - 《地面无人平台自主控制》
大作业：基于ROS通信的分布式多进程路径跟踪控制仿真系统

# 1、环境准备
- VMware 17.01
- Ubuntu 18.04
- ROS1 Melodic
- Python 2.7.17(Ubuntu 18.04 自带)

# tips
注意 Ubuntu 和 ROS 版本的兼容性，ROS 的安装可以借助"鱼香 ROS"的脚本一键安装，可以省去很多不必要的麻烦
```shell
wget http://fishros.com/install -O fishros && . fishro
```
安装好 Ubuntu 对应版本的 ROS 版本后，进行环境变量的配置（避免每次新开一个窗口加载 ROS 环境）
```shell
sudo gedit ~/.bashrc            # 以管理员权限打开当前用户主目录下的 .bashrc 文件，使用 gedit 文本编辑器进行编辑
```
```shell
# 在文件最后一行进行环境变量的配置

# >>> fishros initialize >>>
source /opt/ros/melodic/setup.bash
# <<< fishros initialize <<<

source ~/catkin_ws/devel/setup.bash
export ROS_PACKAGE_PATH=${ROS_PACKAGE_PATH}:~/catkin_ws/
```
```shell
source ~/.bashrc        # 让修改立即在当前终端中生效，而不需要重新启动终端
```

# 2、实验步骤
## ①创建 catkin_workspace
```shell
mkdir catkin_ws
cd catkin_ws
mkdir src
```
## ②将我的 src 的代码，拷贝到上述建立的 src 中，在 catkin_ws 根目录下，进行 catkin_make 构建
```shell
cd ..
catkin_make             # 在 catkin_ws 下
```
## ③gazebo 提供了仿真环境，可以模拟小车的行为
```shell
roslaunch gazebo_ros empty_world.launch         # 打开一个空白的世界

# 新开一个命令窗口
roslaunch car_model spawn_car.launch            # 在空白世界加载小车模型
```

# 3、关于 ROS1 Melodic 的其他常用命令
```shell
rostopic list           # 查看 ROS 下的 topic 列表
rostopic pub /smart/front_right_steering_position_controller/command std_msgs/Float64 "data: -0.5"    # 用前右轮 topic 发布指令，对前右轮进行转角控制
```

# 4、参考文献
- [B站视频 - 从零开始自动驾驶，视频参考](https://www.bilibili.com/video/BV1ZJ41187tS?vd_source=9d200f81297017a5a132e268a0a52f9d)
- [URDF](https://wiki.ros.org/cn/urdf)
- [xacro（XML Macros）](https://wiki.ros.org/cn/xacro)