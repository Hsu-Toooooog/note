1. 配置编译器MinGW

2. 配置launch.json和tasks.json文件

   - 注意！以下配置将编译生成的文件和调试的目标路径修改为当前目录下的bin文件夹下的目标文件，若为多文件项目还需修改

   - 对launch.json

     ```json
     {
         // 使用 IntelliSense 了解相关属性。 
         // 悬停以查看现有属性的描述。
         // 欲了解更多信息，请访问: https://go.microsoft.com/fwlink/?linkid=830387
         "version": "0.2.0",
         "configurations": [
             {
                 "name": "gcc.exe - 生成和调试活动文件",
                 "type": "cppdbg",
                 "request": "launch",
                 "program": "${fileDirname}\\bin\\${fileBasenameNoExtension}.exe",//修改了执行路径
                 "args": [],
                 "stopAtEntry": false,
                 "cwd": "${fileDirname}",
                 "environment": [],
                 "externalConsole": false,
                 "MIMode": "gdb",
                 "miDebuggerPath": "C:\\mingw64\\bin\\gdb.exe",
                 "setupCommands": [
                     {
                         "description": "为 gdb 启用整齐打印",
                         "text": "-enable-pretty-printing",
                         "ignoreFailures": true
                     },
                     {
                         "description": "将反汇编风格设置为 Intel",
                         "text": "-gdb-set disassembly-flavor intel",
                         "ignoreFailures": true
                     }
                 ],
                 "preLaunchTask": "C/C++: gcc.exe 生成活动文件"
             }
         ]
     }
     ```

   - 对task.json:

     ```
     {
         "tasks": [
             {
                 "type": "cppbuild",
                 "label": "C/C++: gcc.exe 生成活动文件",
                 "command": "C:\\mingw64\\bin\\gcc.exe",
                 "args": [
                     "-fdiagnostics-color=always",
                     "-g",
                     "${file}",
                     "-o",
                     "${fileDirname}\\bin\\${fileBasenameNoExtension}.exe"//修改了编译生成exe文件路径
                 ],
                 "options": {
                     "cwd": "${fileDirname}"
                 },
                 "problemMatcher": [
                     "$gcc"
                 ],
                 "group": {
                     "kind": "build",
                     "isDefault": true
                 },
                 "detail": "调试器生成的任务。"
             }
         ],
         "version": "2.0.0"
     }
     ```

   

