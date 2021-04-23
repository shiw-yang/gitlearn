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
```







