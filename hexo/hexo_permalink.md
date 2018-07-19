---
title: 生成永久链接(permalink) | hexo
date: 2017-10-18 22:31:52
categories:
    - hexo
tags:
    - hexo 
abbrlink: 313ea05a1562b260
---

hexo默认的文章链接形式为`domain/year/month/day/postname`，当我们把文章源文件名改掉之后，链接也会改变，这很不友好。
这里介绍一种方法来生成永久链接。使用的是node.js常用的自动构建工具[grunt].

步骤为：

1. 文章的`Front-matter`中加入一个`abbrlink` 字段
![image](http://qiniu.wangjinle.com/20171019120507.png)

1. 使用[grunt]的插件`grunt-rewrite`自动填充`abbrlink`的值
编辑 `Gruntfile.js`
```js
module.exports = function(grunt) {
 
  grunt.initConfig({

    rewrite: {
      abbrlink: {
        src: 'source/_posts/**/*.md',
        editor: function(contents, filepath){
          const crypto = require('crypto');
          const hash = crypto.createHash('sha256');

          hash.update(contents);
          var hashValue = hash.digest('hex');

          return contents.replace(/@@abbrlink/g, hashValue.substring(0, 16));
        }
      },
    },
  });
 
  grunt.loadNpmTasks('grunt-rewrite');
};
```
这表示，插件到`source/_posts/` 下读取所有的`.md`文件，把文件中的`@@abbrlink`替换成文件内容的hash值。

1. 编辑站点配置文件`_config.yml`的`permalink`
```yml
permalink: posts/:abbrlink.html
```


最后，当我们运行`grunt rewrite`后，`@@abbrlink`会被替换成一个16位的hash值。
链接地址变成`blog.wangjinle.com/posts/916d83182e15eeb1.html`这种样式，只要不去改动这个hash值，链接地址不会变。




[grunt]: https://gruntjs.com/

