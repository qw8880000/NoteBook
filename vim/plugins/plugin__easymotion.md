@Filename:       plugin__easymotion.md  
@Author:         wangjl  
@Date:           2016-03-23 23:08  
@Last modified:  2016-03-23 23:08  
@Description:   

# easymotion

简单说, 它提供了一组对应默认移动操作的键绑定, 能搜索并高亮所有可能的选择以供跳转, 类似Vimperator里链接跳转的方式, 效果相当棒

# 快捷键

## 跳转到当前光标前后的位置(w/b)

快捷键<leader><leader>w和<leader><leader>b

## 行级跳转(jk)

快捷键: <leader><leader>j和<leader><leader>k

## 行内跳转(hl)

快捷键<leader><leader>h和<leader><leader>l

## 搜索跳转(s)

快捷键<leader><leader>s

# 配置

    Bundle 'Lokaltog/vim-easymotion'
    let g:EasyMotion_smartcase = 1
    "let g:EasyMotion_startofline = 0 " keep cursor colum when JK motion
    map <Leader><leader>h <Plug>(easymotion-linebackward)
    map <Leader><Leader>j <Plug>(easymotion-j)
    map <Leader><Leader>k <Plug>(easymotion-k)
    map <Leader><leader>l <Plug>(easymotion-lineforward)
    " 重复上一次操作, 类似repeat插件, 很强大
    map <Leader><leader>. <Plug>(easymotion-repeat)

# 参考

http://www.wklken.me/posts/2015/06/07/vim-plugin-easymotion.html
