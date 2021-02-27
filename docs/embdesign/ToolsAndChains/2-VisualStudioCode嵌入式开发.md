# Visual Studio Code 嵌入式开发

大多数时候我们使用集成开发环境如： Keil,IAR等进行开发，但随着VSCode的流行，它的简介，丰富的插件，开源免费等优点，让越来越多的嵌入式开发者也转入它的怀抱。

>Visual Studio Code 是由微软开发，同时支持 Windows 、 Linux 和 macOS 等操作系统且开放源代码的代码编辑器，支持测试，并内置了 Git 版本控制功能，同时也具有开发环境功能，例如代码补全、代码片段和代码重构等。[维基百科]

我们使用VSCode + GNU ARM 工具链可以替代其他嵌入式的IDE。代码编译用 GCC、调试代码用 GDB.

**软件工具**：
1. [Visual Studio Code](https://github.com/microsoft/vscode)
2. C/C++ 插件
3. [pyOCD](https://github.com/pyocd/pyOCD)
4. [GNU Arm Embedded Toolchain](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads) ----  gcc-arm-none-eabi-10-2020-q4-major-win32.exe / gcc-arm-none-eabi-10-2020-q4-major-win32.zip
5. [LLVM](https://releases.llvm.org/download.html) 或者[LLVM-GitHub](https://github.com/llvm/llvm-project)

**参考文章**
1. [Visual Studio Code 嵌入式开发环境](https://zhuanlan.zhihu.com/p/114311741)
2. [使用VScode 编写嵌入式C代码，实现代码提醒补充，函数跳转](https://www.jianshu.com/p/3e884483299a)

## 软件安装
后续更新……

## 配置试功能

Visual Studio Code 使用 launch.json 文件来对调试功能进行配置，可以参考以下步骤：

1. 打开项目工程目录
2. 在项目根目录下找到 .vscode/launch.json 文件，没有的话则自己新建。在该文件中输入以下配置：

``` json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "C++ Launch",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceRoot}/armgcc/_build/nrf52840_xxaa.out",
            "args": [],
            "stopAtEntry": true,
            "cwd": "${workspaceRoot}",
            "environment": [],
            "externalConsole": false,
            "debugServerArgs": "",
            "serverLaunchTimeout": 20000,
            "filterStderr": true,
            "filterStdout": false,
            "serverStarted": "GDB\\ server\\ started",
            "preLaunchTask": "make",
            "setupCommands": [
                { "text": "-target-select remote localhost:3333", "description": "connect to target", "ignoreFailures": false },
                { "text": "-file-exec-and-symbols ${workspaceRoot}/armgcc/_build/nrf52840_xxaa.out", "description": "load file", "ignoreFailures": false},
                { "text": "-interpreter-exec console \"monitor endian little\"", "ignoreFailures": false },
                { "text": "-interpreter-exec console \"monitor reset\"", "ignoreFailures": false },
                { "text": "-interpreter-exec console \"monitor halt\"", "ignoreFailures": false },
                { "text": "-interpreter-exec console \"monitor arm semihosting enable\"", "ignoreFailures": false },
                { "text": "-target-download", "description": "flash target", "ignoreFailures": false }
            ],
            "logging": {
                "moduleLoad": true,
                "trace": true,
                "engineLogging": true,
                "programOutput": true,
                "exceptions": true
            },
            "linux": {
                "MIMode": "gdb",
                "MIDebuggerPath": "arm-none-eabi-gdb",
                "debugServerPath": "pyocd-gdbserver"
            },
            "osx": {
                "MIMode": "gdb",
                "MIDebuggerPath": "arm-none-eabi-gdb",
                "debugServerPath": "pyocd-gdbserver"
            },
            "windows": {
                "preLaunchTask": "make.exe",
                "MIMode": "gdb",
                "MIDebuggerPath": "arm-none-eabi-gdb.exe",
                "debugServerPath": "pyocd-gdbserver.exe",
                "setupCommands": [
                    { "text": "-environment-cd ${workspaceRoot}\\armgcc\\_build" },
                    { "text": "-target-select remote localhost:3333", "description": "connect to target", "ignoreFailures": false },
                    { "text": "-file-exec-and-symbols nrf52840_xxaa.out", "description": "load file", "ignoreFailures": false},
                    { "text": "-interpreter-exec console \"monitor endian little\"", "ignoreFailures": false },
                    { "text": "-interpreter-exec console \"monitor reset\"", "ignoreFailures": false },
                    { "text": "-interpreter-exec console \"monitor halt\"", "ignoreFailures": false },
                    { "text": "-interpreter-exec console \"monitor arm semihosting enable\"", "ignoreFailures": false },
                    { "text": "-target-download", "description": "flash target", "ignoreFailures": false }
                ]
            }
        }
    ]
}
```

3. 在.vscode/tasks.json（没有该文件则新建）中创建一个make任务，这样在进入调试功能时可以自动重新编译代码：

``` json
{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "make",
            "options": {
                "cwd": "${workspaceRoot}/armgcc"
            },
            "problemMatcher": {
                "owner": "cpp",
                "fileLocation": ["relative", "${workspaceRoot}"],
                "pattern": {
                    "regexp": "^(.*):(\\d+):(\\d+):\\s+(warning|error):\\s+(.*)$",
                    "file": 1,
                    "line": 2,
                    "column": 3,
                    "severity": 4,
                    "message": 5
                }
            },
            "args": [],
            "linux": {
                "command": "make"
            },
            "osx": {
                "command": "make"
            },
            "windows": {
                "command": "make.exe"
            }
        }
    ]
}
```