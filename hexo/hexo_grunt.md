---
title: hexo使用grunt实现自动化 | hexo
date: 2017-10-26 22:32:00
categories:
    - hexo
tags:
    - hexo
abbrlink: 3b05183235dcc265
---

本文介绍hexo使用grunt实现一些自动化操作。

开发过前端或者node.js的同学对grunt应该不陌生，如果对grunt不熟悉可略过本文。

开始使用hexo来处理静态博客时我就遇到了问题，我的文章已经写了很多篇了，都是markdown格式，而且托管在github上了，然而hexo并不支持导入文章。

好在我发现只要把markdown文件拷贝到hexo里的`source/_posts`，hexo就会解析，我可以考虑直接把所有文章直接拷贝到这个目录。

但是另外一个问题又出现了，问题在于存在两份一模一样的源文件，一份我托管在github上，一份在`source/_posts`，后期文章改动的话，两边不同步，维护很费力。

后来想到的方法就是利用自动化工具来处理源文件的拷贝，博客的部署等一些操作。由于对grunt比较熟悉，所以使用了grunt。

如果对grunt不熟悉，可以前往[grunt 网站](http://www.gruntjs.net/)

# 准备

* 切换到hexo博客目录
* 执行以下命令安装grunt cli： `npm install -g grunt-cli`
* 执行以下命令安装grunt： `npm install grunt --save-dev`
* 执行以下命令安装插件：`npm install --save-dev grunt-bg-shell grunt-contrib-clean grunt-contrib-copy grunt-contrib-watch grunt-rewrite grunt-zip grunt-shell load-grunt-tasks`
* 新建`Gruntfile.js`
* 新建`raw`目录

完成后，我的hexo博客里的目录结构是这样子的：
![image](http://oxnimkw03.bkt.clouddn.com/20171105113134.png)


# grunt插件说明

以下为使用到的插件：

| 插件                | 作用                                       |
|---------------------|--------------------------------------------|
| grunt-bg-shell      | 在后台运行shell命令                        |
| grunt-contrib-clean | 删除文件和目录                             |
| grunt-contrib-copy  | 拷贝文件和目录                             |
| grunt-contrib-watch | 监测文件的新增、修改与删除并运行对应的任务 |
| grunt-rewrite       | 文件特定内容的替换                         |
| grunt-shell         | 运行shell命令                              |
| grunt-zip           | zip压缩                                    |
| load-grunt-tasks    | 自动加载grunt插件                          |

# Gruntfile.js 编写

新建`Gruntfile.js`，以下是我的`Gruntfile.js`的内容：
```js
// see: https://gruntjs.com/sample-gruntfile
module.exports = function(grunt) {
  
  var config = {
    pkg: grunt.file.readJSON('package.json'),
    pathConfig: {
      raw: 'raw',
      posts: 'source/_posts',
    },

    clean: {
      posts: {
        src: ['<%= pathConfig.posts %>/'],
      },
    },

    copy: {
      main: {
        files: [{
          expand: true,
          cwd: '<%= pathConfig.raw %>',
          src: '**/*.md',
          dest: '<%= pathConfig.posts %>',
          flatten: true,
          filter: function(filepath) {
            // var patterns = ['---\ntitle:'];
            var patterns = ['^---$'];
            var matchRegex = function(filepath, patterns) {
              var content = grunt.file.read(filepath);

              return patterns.some(function(pattern){
                var regex = new RegExp(pattern, 'm');
                // var regex = new RegExp(pattern);
                return regex.test(content);
              });
            };
            return matchRegex(filepath, patterns);
          },
        }],
      },
    },

    watch: {
      raw: {
        files: ['<%= pathConfig.raw %>/**/*.md'],
        tasks: ['copy:main'],
        options: {
          // spawn: false,
        },
      },
    },

    bgShell: {
      hexoServer: {
        cmd: 'hexo server',
        bg: true,
      },
      
    },

    shell: {
      gitClone: {
        command: 'git clone git@github.com:xxxxxxx/my_blog.git <%= pathConfig.raw %>/my_blog'
      },
      gitPullRaw: {
        command: 'cd ./raw/my_blog && git pull'
      },

      hexoGenerate: {
        command: 'hexo g',
      },
      hexoClean: {
        command: 'hexo clean',
      },
    },

    rewrite: {
      abbrlink: {
        src: '<%= pathConfig.raw %>/**/*.md',
        editor: function(contents, filepath){
          const crypto = require('crypto');
          const hash = crypto.createHash('sha256');

          hash.update(contents);
          var hashValue = hash.digest('hex');

          return contents.replace(/abbrlink: 3fb9c7a4f247726d/g, "abbrlink: " + hashValue.substring(0, 16));
        }
      },
    },

    zip: {
      dist: {
        src: [
          'public/**/*',
        ],
        dest: 'blog.zip'
      }
    }

  };

  grunt.initConfig(config);
  require('load-grunt-tasks')(grunt);

  // 运行grunt init 调用此任务
  grunt.registerTask('init', [
    'shell:gitClone'
  ]);

  grunt.registerTask('RawToPosts', [
    'shell:gitPullRaw',
    'rewrite:abbrlink',
    'copy:main',
  ]);

  // 运行 grunt 或者 grunt default 调用此任务
  grunt.registerTask('default', [
    'clean:posts',
    'RawToPosts',
    'bgShell:hexoServer',
    'watch',
  ]);

  // 运行grunt build调用此任务
  grunt.registerTask('build', [
    'clean:posts',
    'RawToPosts',
    'shell:hexoClean',
    'shell:hexoGenerate',
    'zip:dist'
  ]);

};
```

上述`Gruntfile.js`中有三个比较重要的任务：
* grunt init
* grunt
* grunt build


`grunt init` 任务是调用`shell:gitClone` 把我的博客源文件从github上拉取下来，放到`raw/my_blog`目录，这个命令只需要执行一次，后期不再需要。

`grunt` 任务用于日常本地写博客，它的子任务分别是：
* `clean:posts`: 删除`source/_posts`下的所有文件
* `RawToPosts`: 从github拉取更新到`raw/my_blog`，并拷贝符合条件的文件到`source/_posts`
* `bgShell:hexoServer`: 执行`hexo server`，启动hexo本地服务
* `watch`: 监测文件变化，辅助`hexo server`刷新

`grunt build` 任务用于发布博客，它的子任务分别是：
* `clean:posts`: 删除`source/_posts`下的所有文件
* `RawToPosts`: 从github拉取更新到`raw/my_blog`，并拷贝符合条件的文件到`source/_posts`
* `shell:hexoClean`: 执行`hexo clean`
* `shell:hexoGenerate`: 执行`hexo genetate`
* `zip:dist`: 打包`public`成为`blog.zip`

通过上述grunt自动化脚本，我保持了博客文件与hexo博客环境相分离的目标，我只需要运行`grunt build`，grunt会自动帮我拉取最新的博客文件并最终生成hexo目标文件。

这样做的好处是以后不使用hexo时，我可以很方便转移我的博客。

# 其他

如果是使用`github pages`来托管博客的同学，可以把`grunt build`的`zip:dist`换成自动部署博客的任务，就能一键部署啦。

