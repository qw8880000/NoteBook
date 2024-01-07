# windows系统下终端输出中文乱码

vscode使用的终端一般是windows系统下的cmd.exe，windows一般默认编码是GBK，而vscode使用的编码一般是UTF-8，两者由于编码不一致导致的中文乱码。

1. 确认系统编码环境：cmd终端输入chcp可以查看当前系统默认编码,65001代表UTF-8，936代表GBK;
2. 设置vscode打开终端时使用的编码。打开settings.json，找到`terminal.integrated.profiles.windows`，把`"Command Prompt"`下面的`args`参数设置成：`"args": ["/k", "chcp 65001"],`，意思就是当vscode打开windows终端的时候默认使用utf-8编码打开终端。
