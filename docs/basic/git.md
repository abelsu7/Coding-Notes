?> ![](https://notes.abelsu7.top/_media/git.svg ':no-zoom')Git 常用命令

## git remote 远程仓库

查看关联的远程仓库名称

```bash
git remote
```

查看关联的远程仓库详细信息

```bash
git remote -v
```

添加远程仓库的关联

```bash
git remote add <name> <url>
```

删除远程仓库的关联

```bash
git remote remove <name>
```

修改远程仓库的关联

```bash
git remote set-url <name> <url>
```

## git branch 分支

### 查看分支

查看所有分支及版本信息：

```bash
git branch -av
```

### 删除分支

在`Git v1.7.0`之后，可以使用以下语法删除远程分支：

```bash
git push origin --delete <branchName>
# 或者推送一个空分支
git push origin :<branchName>
```

或者使用`git branch`命令：

```bash
git branch -r -d origin/<branchName>
```

### 删除不存在对应远程分支的本地分支

?> [![](logo/csdn.ico ':size=16')Git 对远程分支和 tag 的操作 | CSDN](https://blog.csdn.net/mydo/article/details/42294387)

假设这样一种情况：

1. 我创建了本地分支`b1`并`push`到了远程分支`origin/b1`
2. 其他人在本地使用`fetch`或`pull`创建了本地的`b1`分支
3. 我删除了`origin/b1`远程分支
4. 其他人再次执行`fetch`或者`pull`并不会删除他们本地的`b1`分支，运行`git branch -a`也不能看出这个分支被删除了，如何处理？

使用以下命令查看`b1`的状态：

```bash
> git remote show origin
* remote origin
  Fetch URL: git@github.com:xxx/xxx.git
  Push  URL: git@github.com:xxx/xxx.git
  HEAD branch: master
  Remote branches:
    master                 tracked
    refs/remotes/origin/b1 stale (use 'git remote prune' to remove)
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (up to date)
```

可以看到`b1`分支是`stale`状态，使用`git remote prune`命令可以将其从本地版本库中去除：

```bash
git remote prune origin
```

更简单的方法是`fetch -p`，它会在`fetch`之后删除掉没有与远程分支对应的本地分支：

```bash
git fetch -p
```

### 重命名远程分支

?> 在 Git 中**重命名远程分支**，其实就是先**删除远程分支**，然后**重命名本地分支**，最后再重新**将本地分支推送至远程分支**

删除远程分支：

```bash
> git push --delete origin devel
To git@github.com:zrong/quick-cocos2d-x.git
 - [deleted]         devel
```

重命名本地分支：

```bash
git branch -m devel develop
```

推送本地分支：

```bash
> git push origin develop
Counting objects: 92, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (48/48), done.
Writing objects: 100% (58/58), 1.38 MiB, done.
Total 58 (delta 34), reused 12 (delta 5)
To git@github.com:zrong/quick-cocos2d-x.git
 * [new branch]      develop -> develop
```

## git tag 标签

?> [Git 打标签与版本控制规范 | 掘金](https://juejin.im/post/5b0531c6f265da0b7f44eb8c)<br>[创建标签 | 廖雪峰的 Git 教程](https://www.liaoxuefeng.com/wiki/896043488029600/902335212905824)<br>[![](logo/git.svg)git-tag Documentation](https://git-scm.com/docs/git-tag)


查看本地`tag`：

```bash
git tag
git tag -l
```

为当前`commit`打`tag`：

```bash
git tag -a <tagName> -m <tagMsg>
git tag -a v1.1.4 -m "tagging version 1.1.4"
```

删除本地`tag`：

```bash
git tag -d <tagName>
```

获取远程`tag`：

```bash
git fetch origin tag <tagName>
```

删除远程`tag`：

```bash
git push origin --delete tag <tagName>

# 或者推送一个空 tag 到远程 tag
git tag -d <tagName>
git push origin :refs/tags/<tagName>
```

把本地`tag`推送到远程：

```bash
git push origin <tagName>
git push --tags
```

## git alias 别名

?> 参见 [配置别名 | 廖雪峰的 Git 教程](https://www.liaoxuefeng.com/wiki/896043488029600/898732837407424#0)<br>[![](logo/wechat.svg)技巧-Git Alias 让你事半功倍 | 逅弈逐码![](logo/star.svg)](https://mp.weixin.qq.com/s/IrkIeYlL9Hsysgq-RoMuVg)

```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.ci commit
git config --global alias.br branch
git config --global alias.unstage "reset HEAD"
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

## git 取消文件跟踪

对某个文件取消跟踪：

```bash
git rm --cached readme1.txt # 删除 readme1.txt 的跟踪，并且保留在本地
git rm --f readme1.txt      # 删除 readme1.txt 的跟踪，并删除本地文件
```

对所有文件取消跟踪：

```bash
git rm -r --cached . # 不删除本地文件
git rm -r --f .      # 删除本地文件
```

然后`git commit`即可。

## git config 设置

```bash
git config --list
git config --global --list

git config --edit
git config --global --edit

git config --global user.name abelsu7
git config --global --unset user.name
```

## git 常见错误

### Another git process seems to be running in this repository

执行 `git commit -a` 在 VIM 界面输入信息时终端崩溃，再次执行 `git commit` 命令报以下错误

![](https://notes.abelsu7.top/_images/git-lock.png)

!> 进入 `.git/` 目录，手动删除 `index.lock` 以及 `.COMMIT_EDITMSG.swp`

### Windows 上关于 CRLF 的警告

```bash
git config --global core.autocrlf true
```

### 修改上一次的 commit message

```bash
git commit --amend
# 然后可以更改 commit message
```


## git stash

?> 参见 [Git 工具 - 储藏（Stashing）](https://git-scm.com/book/zh/v1/Git-工具-储藏（Stashing）) 

```bash
git stash
git stash list
git stash apply
```

## git diff

```bash
git diff --staged
# 包括暂存区中的 diff
```

## git merge

合并分支时`--ff`和`--no-ff`的区别：

- [git merge 和 git merge --no-ff 的区别 | TY·Loafer](https://tyloafer.github.io/posts/132/)
- [![](logo/csdn.ico ':size=16')Git：git-merge 的 --ff 和 --no-ff | CSDN](https://blog.csdn.net/chaiyu2002/article/details/81020370)
- [git merge --no-ff 是什么意思 | SegmentFault](https://segmentfault.com/q/1010000002477106)
- [分支管理策略 | 廖雪峰的 Git 教程](https://www.liaoxuefeng.com/wiki/896043488029600/900005860592480#0)





## Github SSH

```bash
ssh -T git@github.com
```

## git 教程

- [![](logo/flysnow.ico ':size=16')Github 的前世今生 | 飞雪无情![](logo/star.svg)](https://www.flysnow.org/2019/01/09/github-milestones.html)
- [![](logo/wechat.svg)每个程序员都该学会的Git知识 | 逅羿逐码![](logo/star.svg)](https://mp.weixin.qq.com/s/qgNua-ZcllDNk3G3W12T7Q)
- [![](logo/github.svg)LearnGitBranching | Github![](logo/star.svg)](https://github.com/pcottle/learnGitBranching)
- [![](logo/git.svg)learngitbranching.js.org![](logo/star.svg)](https://learngitbranching.js.org)
- [![](logo/wechat.svg)Double Kill，用玩游戏的方式来学习 Git | 吴小龙同学![](logo/star.svg)](https://mp.weixin.qq.com/s/xf1vqsMpD5HcbYB_DRghEA)
- [![](logo/wechat.svg)网易工程师 Ruheng 一文教你轻松学会 Git | 码洞![](logo/star.svg)](https://mp.weixin.qq.com/s/alB76HmbOzvc21srLOuoRw)
- [![](logo/wechat.svg)技巧-Git Alias 让你事半功倍 | 逅弈逐码![](logo/star.svg)](https://mp.weixin.qq.com/s/IrkIeYlL9Hsysgq-RoMuVg)
- [廖雪峰的 Git 教程](https://www.liaoxuefeng.com/wiki/896043488029600)
- [githug - Git your game on | Github](https://github.com/Gazler/githug)

## 开源项目收集

### 数据库

- [![](logo/github.svg)mycli - A Terminal Client for MySQL | Github![](logo/star.svg)](https://github.com/dbcli/mycli)
- [![](logo/github.svg)pgcli - A Terminal Client for PostgreSQL | Github![](logo/star.svg)](https://github.com/dbcli/pgcli)
- [![](logo/github.svg)litecli - A Terminal Client for SQLite![](logo/star.svg)](https://github.com/dbcli/litecli)

### 命令行

- [![](logo/github.svg)The Fuck | Magnificent app which corrects your previous console command.![](logo/star.svg)](https://github.com/nvbn/thefuck)
- [![](logo/github.svg)pingtop🏓 - Ping multiple servers | Github![](logo/star.svg)](https://github.com/laixintao/pingtop)

### 字体

- [![](logo/github.svg)Sarasa Gothic / 更纱黑体 | Github![](logo/star.svg)](https://github.com/be5invis/Sarasa-Gothic)
- [![](logo/github.svg)cascadia-code | Github![](logo/star.svg)](https://github.com/microsoft/cascadia-code)
- [![](logo/github.svg)日收 2700+ Star，微软新终端字体正式开源！| GithubDaily![](logo/star.svg)](https://mp.weixin.qq.com/s/GCqvpLUYYlFh6BzIXnAzfw)
- [APP 设计必备字体：San Francisco Pro、苹方、思源黑体和 Roboto 等 | 设计达人](http://www.shejidaren.com/app-she-ji-bi-bei-zi-ti.html)
- [在 Spacemacs 中配置 Fira Code 并启用 ligatures 特性 | iTimothy](https://xiaozhou.net/setup-spacemacs-with-fira-code-ligatures-2019-09-09.html)

### dotfiles

?> 参见 [![](https://notes.abelsu7.top/_media/favicon.ico ':size=16')Oh My Zsh/NeoVim/Tmux 打造终端 IDE | 苏易北](https://abelsu7.top/2019/05/21/terminal-ide-using-zsh-nvim-tmux)

- [![](logo/github.svg)int32bit/dotfiles - vim/zsh/git/tmux dotfiles | Github](https://github.com/int32bit/dotfiles)
- [![](logo/github.svg)ourvim - jusonalien| Github](https://github.com/jusonalien/ourvim)
- [![](logo/github.svg)TimothyYe/mydotfiles | Github](https://github.com/TimothyYe/mydotfiles)
- [![](logo/github.svg)amix/vimrc | Github](https://github.com/amix/vimrc)
- [![](logo/github.svg)wsdjeg/DotFiles | Github](https://github.com/wsdjeg/DotFiles)
- [![](logo/github.svg)barretlee/autoconfig-mac-vimrc | Github](https://github.com/barretlee/autoconfig-mac-vimrc)

### Github

- [![](logo/github.svg)Google 工程师 Hokein 的 Github Wiki 笔记](https://github.com/hokein/Wiki/wiki)
- [gitMemory | 查看 Github 项目历史记录](https://www.gitmemory.com/)

### 管理 Github Star

- [![](logo/github.svg)astral - Organize Your GitHub Stars With Ease | Github![](logo/star.svg)](https://github.com/astralapp/astral)
- [![](logo/star.svg)Astral](https://astralapp.com)
- [高效管理 GitHub Star，用这几个插件就能做到！| GithubDaily](https://mp.weixin.qq.com/s/xHXUbtmzlKX8TFm1KIEYug)

### fake 数据

- [![](logo/github.svg)idgen - 一个使用 golang 编写的大陆身份证生成器 | Github](https://github.com/mritd/idgen)

### Go 语言

- [![](logo/star.svg)Go 编写的一些常用小工具 | 漠然](https://mritd.me/2018/11/27/simple-tool-written-in-golang/)
- [![](logo/github.svg)grmon - Command line monitoring for goroutines | Github](https://github.com/bcicen/grmon)
- [![](logo/github.svg)halfrost/leetcode-go - LeetCode by Go | Github![](logo/star.svg)](https://github.com/halfrost/LeetCode-Go)

### Docker

- [![](logo/github.svg)ctop - Top-like interface for container metrics | Github![](logo/star.svg)](https://github.com/bcicen/ctop)

## Github 状态监控

?> [![](logo/github.svg)Github Status](https://www.githubstatus.com)

## 相关文章

- [![](logo/wechat.svg)30 分钟让你掌握 Git 的黑魔法 | 阿里巴巴中间件![](logo/star.svg)](https://mp.weixin.qq.com/s/PstnDFD7iFbdJ90z-lC6yw)
- [![](logo/wechat.svg)Git 自救指南 | 扣钉![](logo/star.svg)](https://mp.weixin.qq.com/s/kr0KrwpueC73PD8Ma_AuWg)