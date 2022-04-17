[TOC]

# 输入法相关问题

### 如何在中文输入模式下默认使用半角标点?

1. 点击右上角输入法
2. 打开配置当前输入法
3. 全局配置->显示高级选项
4. 根据里面的快捷键提示打开半角支持

### 简繁体切换快捷键

Ctrl+Shift+F

### 中文输入法无法输入英文

# Typora使用相关问题

### 如何添加目录

在需要添加目录的地方输入[TOC]

### 如何添加代码

```
ctrl+shrit+k
```

### 如何创建表格

```
Ctrl + T
```

### 打开链接

```
Ctrl + Click
```

### Markdown数学公式在线帮助

https://zhuanlan.zhihu.com/p/441454622

https://zhuanlan.zhihu.com/p/158156773

1. 分数

   ```
   \frac{}{}
   ```

2. 

### 创建超链接

```
/*在点击点*/
[显示的文本](#目标跳转点的标签名)

/*在目标跳转点*/
<a id="标签名">显示的文本内容</a>
```



### 其它用途

https://zhuanlan.zhihu.com/p/293557841

# 代理相关问题

### 如何测试是否实现终端代理

```
curl cip.cc
```

# ROS安装相关问题

### sudo rosdep init报错

https://blog.csdn.net/weixin_43288910/article/details/105627358

# ROS依赖相关

### 编译报错:fatal error: casadi/casadi.hpp: 没有那个文件或目录 #include <casadi/casadi.hpp>

车队的文件夹里有安装脚本

### roslaunch fssim auto_fssim.launch报错

```
Traceback (most recent call last):
  File "/home/tog/temp_ws/src/fssim/fssim/scripts/automated_res.py", line 50, in <module>
    from fssim.statistics import *
  File "/home/tog/temp_ws/src/fssim/fssim/src/fssim/statistics.py", line 33, in <module>
    from shapely.geometry import Point
ImportError: No module named shapely.geometry
[automated_res-2] process has died [pid 14499, exit code 1, cmd /home/tog/temp_ws/src/fssim/fssim/scripts/automated_res.py --config /home/tog/temp_ws/src/fssim/fssim/config/simulation.yaml name:=automated_res log:=/home/tog/.ros/log/6d2aae7a-8bed-11ec-9767-c8b29b66d9f6/automated_res-2.log].
log file: /home/tog/.ros/log/6d2aae7a-8bed-11ec-9767-c8b29b66d9f6/automated_res-2*.log
```

https://blog.csdn.net/u010205128/article/details/80995340

# Ubuntu使用问题

### 工具相关

##### 查看GPU使用情况

https://blog.csdn.net/caicaiatnbu/article/details/86506681

```
# 每隔 1s 显示一次显存使用情况
watch -n 1 nvidia-smi
```

### 蓝牙问题相关:

问题:无法连接耳机

解决方案:https://junchu.blog.csdn.net/article/details/106871349

# VSCode快捷键相关

### 选中快捷键

```
ctrl + D //选中当前光标单词
ctrl + L // 选中当前行
ctrl + 方向键 // 以单词为单位移动光标
```

# 深度学习相关

### yolo测试时报错libcudart.so.8.0: cannot open shared object file: No such file or directory

https://blog.csdn.net/wp1988/article/details/76651012

### 运行yolo后显示图像但无bounding box

原因:Makefile中的显卡算力不匹配

解决方案:根据Makefile中line25+的注释将修改ARCH

```
ARCH= -gencode arch=compute_61,code=sm_61 -gencode arch=compute_61,code=compute_61
```

也有说原因是Makefile中的CUDNN_HALF应改为0(可能是因为GTX1650不支持图灵架构)

https://blog.csdn.net/yuanshenqiang/article/details/115720472

### 数据集处理OIDv4_Toolk=Kit配置环境时报错:No module named 'skbuild'......Command"python setup.py egg_info" failed with error code 1

https://blog.csdn.net/GungnirsPledge/article/details/108566415

### 使用py脚本生成了空的test.txt和train.txt

解决方案:将data中的数据文件从二级目录中拖出,直接命名为obj和test

### 训练时报错: out of memory

解决方案:将.cfg文件的random参数改为0(可能是硬件配置不够)
