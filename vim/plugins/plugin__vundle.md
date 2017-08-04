

# 出现的问题
~~~~~~~~~~~

Processing 'gmarik/vundle'
Error detected while processing function vundle#installer#new..<SNR>129_process..vundle#installer#run..vundle#installer#install..<SNR>129_sync..<SNR>129_system:
line    1:
E484: Can't open file C:\Users\gallia1\AppData\Local\Temp\VIo8E1E.tmp
Error detected while processing function vundle#installer#new..<SNR>129_process:
line   13:
E121: Undefined variable: g:vundle_last_status
E15: Invalid expression: 'error' == g:vundle_last_status
line   17:
E121: Undefined variable: g:vundle_last_status
E15: Invalid expression: 'updated' == g:vundle_last_status && empty(msg)

~~~~~~~~~~~

解决：

    1. 把vim74(如：C:\Program Files\gVimPortable\vim74)加入系统变量Path
    2. 安装 git for Windows ,选择``Run git from Windows command prompt option``

参考：[Vundle for Windows](https://github.com/VundleVim/Vundle.vim/wiki/Vundle-for-Windows)
