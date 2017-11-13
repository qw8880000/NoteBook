git

# git subtree是什么？为什么使用git subtree

git subtree 可以实现一个仓库作为其他仓库的子仓库。
![image](http://oxnimkw03.bkt.clouddn.com/BeforeAfterGitSubtreeDiagram.png)

使用git subtree 有以下几个原因：
* 旧版本的git也支持(最老版本可以到 v1.5.2).
* git subtree与git submodule不同，它不增加任何像`.gitmodule`这样的新的元数据文件.
* git subtree对于项目中的其他成员透明，意味着可以不知道git subtree的存在.

当然，git subtree也有它的缺点，但是这些缺点还在可以接受的范围内：
* 必须学习新的指令(如：git subtree).
* 子仓库的更新与推送指令相对复杂。

# git subtree 的使用


git subtree的主要命令有：
```sh
git subtree add   -P <prefix> <commit>
git subtree add   -P <prefix> <repository> <ref>
git subtree pull  -P <prefix> <repository> <ref>
git subtree push  -P <prefix> <repository> <ref>
git subtree merge -P <prefix> <commit>
git subtree split -P <prefix> [OPTIONS] [<commit>]
```

## 准备

我们先准备一个仓库叫photoshop，一个仓库叫libpng，然后我们希望把libpng作为photoshop的子仓库。
photoshop的路径为`https://github.com/test/photoshop.git`，仓库里的文件有：
```
photoshop
    |
    |-- photoshop.c
    |-- photoshop.h
    |-- main.c
    \-- README.md
```
libPNG的路径为`https://github.com/test/libpng.git`，仓库里的文件有：
```
libpng
    |
    |-- libpng.c
    |-- libpng.h
    \-- README.md
```

以下操作均位于父仓库的根目录中（我写此文档时git subtree要求所有的git subtree命令必须位于父仓库的根目录才能执行）。

## 在父仓库中新增子仓库

```sh
git subtree add --prefix sub/libpng https://github.com/test/libpng.git master --squash
```
(`--squash`参数表示不拉取历史信息，而只生成一条commit信息。)

执行`git status`可以看到提示新增两条commit:
![image](http://oxnimkw03.bkt.clouddn.com/git_status.png)

`git log`查看详细修改：
![image](http://oxnimkw03.bkt.clouddn.com/git_log.png)

执行`git push`把修改推送到远端photoshop仓库，现在本地仓库与远端仓库的目录结构为：
```sh
photoshop
    |
    |-- sub/
    |   |
    |   \--libpng/
    |       |
    |       |-- libpng.c
    |       |-- libpng.h
    |       \-- README.md
    |
    |-- photoshop.c
    |-- photoshop.h
    |-- main.c
    \-- README.md
```

# 更多

* [Git subtree: the alternative to Git submodule](https://www.atlassian.com/blog/git/alternatives-to-git-submodule-git-subtree)
* [The power of Git subtree](https://legacy-developer.atlassian.com/blog/2015/05/the-power-of-git-subtree/)
