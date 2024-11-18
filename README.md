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