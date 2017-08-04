
## intro

下面是一些vim Markdown preview 的一插件


### 1.vim-instant-markdown

    当你用vim打开Markdown文件时会自动打开一个浏览器窗口展示编辑成网页的Markdown文件，网页内容会随你的编辑自动更新。

支持平台

    OSX and Unix/Linuxes*

github address

(https://github.com/suan/vim-instant-markdown)


### 2.vim-markdown-preview

    A small Vim plugin for previewing markdown files in a browser.

requirements

    Mac OS X  
    Unix  

github address

(https://github.com/JamshedVesuna/vim-markdown-preview)

### 3.vim-preview

    Preview plugin is a tool developed to help you to preview markup files such as .markdown, .rdoc, .textile and .html when you are editing them. 
    It builds html files and opens them in your browser.


requirements

    ??

github address

(https://github.com/greyblake/vim-preview)



### 4. python-vim-instant-markdown

github address

(https://github.com/isnowfy/python-vim-instant-markdown)


### 5. md-server

    Edit your file with your favourite editor and get the result in the browser when you save the file.

    A constant markdown file parsing, watching and reload server.
    
    It's super easy to use, it could reload your browser when you save the markdown file.
    
    Any issue is welcome!

depends:

    Node.js

github address

(https://github.com/chemzqm/md-server)

### 6. chrome 的 Markdown Preview plus 插件

使用方法:

1. 从chrome的webstore安装Markdown Preview Plus插件
1. 打开chrome://extensions/，在设置页中勾选 “允许访问文件网址”
1. 在chrome中打开本地markdown文件，http/https也是可以支持的
1. 你会看到已经转换成html的内容

在chrome中打开markdown文件，用vim编辑markdown，保存后页面就会自动刷新，实现预览。虽然不像一些工具一样是实时的，但是保存后再预览，这样我觉得也挺好。再在vimrc中加入以下内容：  

``
autocmd BufRead,BufNewFile *.{md,mdown,mkd,mkdn,markdown,mdwn} map <Leader>p :!start "C:\Program Files\Google\Chrome\Application\chrome.exe" "%:p"<CR>
``

参考： 

(http://howiefh.github.io/2013/05/16/vim-markdown-preview/)



### 备注

[Node.js](http://nodejs.cn/)
