@Filename:       vim_快捷键映射.md  
@Author:         wangjl  
@Date:           2016-03-23 22:36  
@Last modified:  2016-03-23 22:36  
@Description:   

# vimrc中 映射快捷键

noremap是不会递归的映射 (大概是no recursion)

例如
noremap Y y
noremap y Y
不会出现问题

前缀代表生效范围:
* inoremap就只在插入(insert)模式下生效
* vnoremap只在visual模式下生效
* nnoremap就在normal模式下(狂按esc后的模式)生效

