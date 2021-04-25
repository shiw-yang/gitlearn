# Git 学习笔记

## 1. 新建版本库

```Git
git init
把当前目录变成Git可以管理的仓库
```

```Git
git add filename1  filename2 ....
把一系列文件添加到git暂存区
```

```
git -commit -m "write someting message"
把添加到暂存区的文件提交到仓库
```



## 2.时光机穿梭

```
git status
查看仓库当前状态
```

```
git diff filename
查看filename内修改的内容
```



### 2.1 版本回退

```
git log
查看提交版本的历史记录
git log --pretty=oneline 
查看提交版本的历史记录的文字说明
```

```
git reset --hard HEAD^
回退到上一个版本 
上上个版本就是 HEAD^
上一百个版本就是HEAD~100
```

```
git reset --hard commit id
去向commit id 的版本
commit id是十六进制
可以指向过去和未来
```

```
git reflog
查看历史版本，可以看到过去未来的各个commit id和 message
```



### 2.2 工作区和暂存区

#### 2.2.1 工作区 Working Directory

电脑内可以看到的文件夹就是工作区

#### 2.2.2 版本库 Repository

版本库内有stage暂存区和 main分支



### 2.3 管理修改

* `git add`指令把工作区中的文件添加到暂存区

* `git commit`指令把stage中的文件添加到main分支



### 2.4 撤销修改

#### 2.4.1 撤销工作区Working DIrectory中的修改

```
git checkout -- filename
让文件回到最近一次 git commit或 git add时的状态
```



#### 2.4.2 撤销暂存区stage 中的修改

```
git reset HEAD filename
把暂存区的修改回退到工作区
```



### 2.4.3 撤销main分支中的修改

* 未提交到远程仓库的可以使用版本回退

### 2.5 删除文件

```
git rm filename
把文件从版本库中删除
删除后要记得
git commit -m "message"
版本库删除之后本地文件还没有删除，
rm filename

误删可以恢复
git checkout --filename
```

## 3.远程仓库

```
ssh-keygen -t rsa -C"youremail@example.com"
创建SSH Key
设置时一路回车
在目录文件里面可以看到.ssh文件夹
不要把.ssh文件上传到GitHub上！！！
```



### 3.1 添加远程仓库

```
git remote add origin ssh/https
origin是远程库名字，默认origin
```

```
git push -u origin main
首次把本地库的所有内容推送到远程库上
之后每次要推送到远程库上只需要
git push origin main
```

```
git remote -v
查看远程库版本
git remote rm origin 
删除远程库
```

### 3.2 从远程库克隆

```
git clone ssh/https
使用命令在网上克隆一个本地库
可能有代码库不开放ssh
https速度慢
然后要切换到对应的目录
```

## 4.分支管理

### 4.1 创建与合并分支

#### 4.1.1创建分支

```
git checkout -b dev
创建dev分支
```

```
git branch
查看当前所有分支
当前分支前面标一个 *
```

* 不同分支下的工作都是独立的

#### 4.1.2 合并分支

```
git merge dev
把dev分支的工作成果合并到main分支上
```

#### 4.1.3删除分支

```
git branch -d dev
删除dev分支
```

#### 4.1.4 switch 命令

```
git switch -c dev
创建并切换到新的dev分支
git switch main
直接切换已有的main分支
```

* Git 鼓励大量使用分支

### 4.2 解决冲突

* **两个分支有不同内容时，合并分支时会出现冲突 **

```
git merge dev
两个有冲突的分支合并 会有提示冲突
git status
可以看到文件存在冲突，需要手动解决冲突后再提交
手动修改冲突之后在把文件提交
```

### 4.3 分支管理策略

* ` main`分支应该是非常稳定的，用来发布新版本，平时不能在上面干活；
* `dev`版本是用来干活的。到某个时候要发布新版本的时候，再把`dev`分支合并到`main`分支上

### 4.4 bug分支

``` 
git stash 
把工作现场储藏起来，等恢复现场后继续工作
git stash list
恢复现场工作
```

