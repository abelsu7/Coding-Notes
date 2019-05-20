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

查看所有分支及版本信息

```bash
git branch -av
```

## git alias 别名

?> 参见 [配置别名 | 廖雪峰的 Git 教程](https://www.liaoxuefeng.com/wiki/896043488029600/898732837407424#0)<br>[![](logo/wechat.svg)技巧-Git Alias 让你事半功倍 | 逅弈逐码![](logo/star.svg)](https://mp.weixin.qq.com/s/IrkIeYlL9Hsysgq-RoMuVg)

### st -> status

```bash
git config --global alias.st status
```

### co -> checkout

```bash
git config --global alias.co checkout
```

### ci -> commit

```bash
git config --global alias.ci commit
```

### br -> branch

```bash
git config --global alias.br branch
```

### lg -> log

```bash
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

### unstage -> reset HEAD

```bash
git config --global alias.unstage 'reset HEAD'
```

## git 常见错误



### Another git process seems to be running in this repository

执行 `git commit -a` 在 VIM 界面输入信息时终端崩溃，再次执行 `git commit` 命令报以下错误

![](https://notes.abelsu7.top/_images/git-lock.png)

!> 进入 `.git/` 目录，手动删除 `index.lock` 以及 `.COMMIT_EDITMSG.swp`

## Git stash

?> 参见 [Git 工具 - 储藏（Stashing）](https://git-scm.com/book/zh/v1/Git-工具-储藏（Stashing）) 

```bash
git stash
git stash list
git stash apply
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

## Github 收集

- [![](logo/github.svg)The Fuck | Magnificent app which corrects your previous console command.![](logo/star.svg)](https://github.com/nvbn/thefuck)
- [gitMemory | Github 历史记录](https://www.gitmemory.com/)
- [![](logo/github.svg)Google 工程师 Hokein 的 Github Wiki 笔记](https://github.com/hokein/Wiki/wiki)