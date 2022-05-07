[TOC]

# TODO

- [ ] MATLAB - Division (Left, Right) of Matrics 
  [MATLAB - Division (Left, Right) of Matrics (tutorialspoint.com)](https://www.tutorialspoint.com/matlab/matlab_matrix_division.htm)
- [ ] 

# Declare variable

##### declare a matrix

```matlab
t = [1,2,3;4,5,6;7,8,9]		//declare a 3*3 matrix
t = [1,2,3]		//declare a row vector
```



# Command

### Commands for Managing a Session#用于管理会话

| Command |                  Purpose                  |
| :-----: | :---------------------------------------: |
|   clc   |          Clears command window.           |
|  clear  |      Removes variables from memory.       |
|  exist  | Checks for existence of file or variable. |
| global  |     Declares variables to be global.      |
|  help   |        Searches for a help topic.         |
| lookfor |   Searches help entries for a keyword.    |
|  quit   |               Stops MATLAB.               |
|   who   |         Lists current variables.          |
|  whos   |  Lists current variables (long display).  |

### Commands for Working with System#系统交互命令

| Command |                     Purpose                     |
| :-----: | :---------------------------------------------: |
|   cd    |            Changes current directory            |
|  date   |                Displays current                 |
| delete  |                  Delete afile                   |
|  diary  |      switches on/off diary file recording       |
|   dir   |      Lists all files in current directory       |
|  load   |                 Loads workspace                 |
|  path   |              Displays search path               |
|   pwd   |             print working directory             |
|  save   |       Saves workspace variables in a file       |
|  type   |           Displays contents of a file           |
|  what   | Lists all MATLAB files in the current directory |
| wklread |           Reads .wk1 spreadsheet file           |

### Input and Output Commands

| Command |                   Purpose                   |
| :-----: | :-----------------------------------------: |
|  disp   |   Displays contents of an array or string   |
| fscanf  |       Read formatted data from a file       |
| format  |       Controls screen-display format        |
| fprintf | Performs formatted writes to screen or file |
|  input  |    Displays prompts and waits for input     |
|    ;    |         Suppresses screen printing          |

### Other commands

[MATLAB - Commands (tutorialspoint.com)](https://www.tutorialspoint.com/matlab/matlab_commands.htm)

# Simulink

### Simulink模块库:

1. Sinks：输出模块	//out模块提供与matlab主程序的interface
2. sources：源模块    //in模块提供与matlab主程序的interface

# 杂项

# Q&A

##### 如何查看帮助

```
help ***
```

##### 如何添加图例

```matlab
legend('图例一'，‘图例二’)	//使用legend(参数)
```

