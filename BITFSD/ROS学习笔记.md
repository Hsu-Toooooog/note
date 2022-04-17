[TOC]



#### 一些注释

1. $后跟路径
2. #后跟命名
2. []中括号表示可选项
2. {}花括号表示必须在列出的项中选择一项
2. <>尖括号表示必选项

# 一些临时的关键字

- 

- 一个node(节点)应该由若干个（package)组成

- 节点是ros里的执行单元

- 通信的两种形式catkin init可以初始化workspace，而且初始化后，在workspace下的任何一个子目录里使用catkin工具，都相当于在workspace文件夹下使用，它会自动感知workspace。

  - 话题(Topic)
    - Publisher(发布者)
    - Subscriber(订阅者)
    - 单向传输
    - 特点:异步通信,单向传输

  - 服务(Service)

- ```
  roscore
  ```

  用于启动rosmaster(节点管理器)

- ```
  rosrun 'package' 'node'
  ```

  用于启动某个功能包内的某个节点
  Tip:输入package name 后可以按Tab查看包内的节点

- ```
  rqt_graph
  ```

  以图的形式查看当前运行的节点之间的联系

- ```
  rostopic
  ```

  话题相关的命令(按Tab可以查看提示)

- ```
  rosservice
  ```

  服务相关的命令(按Tab可以查看提示)

- ```
  rosbag record //用于记录话题数据
  rosbag play //用于复现话题数据
  ```

- Metapackage //没有实际功能的package, 但是有许多其它依赖项, 通过这种方式来将具有相似功能的包组成一个包集

#### Topic和Message的相关常用指令

- rostopic list
- rostopic info /topic_name
- rostopic echo /topic_name
- rostopic pub /topic_name
- rosmsg list
- rosmsg show /msg_

#### Node(每一个node都是一个进程)

1. roscore
2. rosrun [pkg_name] [node_name]//启动一个node
3. rosnode
4. roslaunch [pkg_name] [file_name]//启动master和多个node, file_name.launch中储存启动信息

- 当在一个包中创建了msg文件并对其进行编译后, 会在工作空间的devel目录下创建同名的.h文件, 所以在包的源文件中可以#include<[package_name]/[message_name.h]>
- 参数服务器
- 字典
- yaml和launch
- rqt_graph中圆圈代表节点方框代表话题
- topic_demo::gps msg;创建消息中topic_demo是命名空间还是类? 和include的消息文件有什么关系(是命名空间, 可以在编译生成的devel中找到对应头文件)

# ROS工程结构

- catkin workspace // catkin是ROS定制的编译构建系统,是对CMake的扩展. Workspace可以理解为Project(工程), 是一个组织和管理功能包的文件夹.
  总的来说, catkin workspace就是指以catkin为编译工具的工程文件夹//catkin_make在此路径下进行
  - **src(source space代码空间)** // 用于储存package源代码, 主要就和这个文件打交道,
    - package(可以有多个包) 		// catkin编译对象的基本单元
      - CMakelists.txt
      - package.xml
      - scripts
        - *.py
        - *.sh
      - msg
        - *.msg
      - srv
        - *.srv
      - include
        - *.h( *.hpp)
      - src
        - *.cpp
      - launch
        - *.launch
  - build(build space编译空间) // 用于储存catkin&CMake的缓存和中间文件, 了解就行
  - devel(Development space开发空间) // 储存目标文件, 比如头文件, 动/静态链接库和可执行文件, 了解就行

#  操作步骤

1. ## 创建工作空间

   ```
   mkdir -p $workspace_path/src //注意一定要有src目录
   ```

2. ## 初始化编译

   ```
   cd $workspace_path
   catkin_make
   ```

3. ## 创建包

   ```
   cd src
   catkin_create_pkg <package_name> [依赖项]
   ```

4. ## 编译

   ```
   catkin_make
   source $workspace_path/devel/setup.bash //生命周期短, 关闭当前终端后失效
   or
   echo "source $workspace_path/devel/setup.bash" >> ~/.bashrc //每次打开终端自动运行操作
   ```



# Topic操作步骤

1. ## 创建package//catkin_create_pkg

2. ## 定义message//修改msg文件

3. ## 具体实现//编写talker.cpp&listener.cpp

4. ## 修改CMakeList.txt&package.xml告诉

# 通信方式

- ## Topic

  - Pubulisher
  - Subscriber
  - 发布者和订阅者按照package的msg(message)文件中定义的数据类型(类)规则来向Topic发送/接收数据

# catkin tools

//catkin_tools是一个用来优化ROS的catkin编译系统的工具

//https://catkin-tools.readthedocs.io/en/latest/

//用法如下:

**基本用法:**

```
$ catkin [global options] <verb> [verb arguments and options]
```

1. 创建工作空间		//没啥区别
   
   ```
   mkdir -p /<workspace_path>/src
   ```
   
2. 初始化工作空间

   ```
   cd <workspace_path>
   catkin init
   ```

3. 创建功能包

   ```
   cd /<workspace_path>/src
   cattkin create pkg <pkg1>
   ```

4. 编译功能包

   ```
   catkin build		//可以在工作空间的任意级下执行(会向上寻找), catkin_make只能在$workspace_path下执行
   ```
   
   

# 出现的一些问题

1. 使用命令

   ```
   rospack list | grep test
   ```

   时无法找到package test

   

   **解决方案:暂无**

   ---

   

2. turtlesim运行小海龟仿真时无法读取键盘操作
   

   **解决方案:需要使读取键盘操作的终端处于活动状态(处于置顶状态),否则无法读取**

   ---

   
   
3. 运行Gazebo时报错"[Err] [REST.cc:205] Error in REST request"

   

   **解决方案:https://blog.csdn.net/qq_42573052/article/details/118710044**

   ---

   

4. 运行仿真时提示fssim/automated_res.py文件报错


   **解决方案:找到这个文件并将其设为可执行(chmod)**

# 一些想法

- 创建了一个新的海龟后如何使其订阅url: https://api.ignitionrobotics.org键盘的操作

# 不是很明白的名词

1. api
2. 依赖
3. 句柄(进程?)