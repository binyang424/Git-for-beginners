# Git Tutorial for Beginners - GitHub Version Control

This git tutorial for beginners will show you how to manage your code using remote repositories on github. I will be showing how to use git and all of its commands. This video is geared towards beginners just learning how to use git as it only shows the basics of git. 

## Step 1: Installation

Download and install GIT:

> https://git-scm.com/downloads. 

It is good to keep the default settings unless you know what you are changing.

## Step 2: Local repository creation

If you are on Microsoft Windows, you will find git CMD and git bash on you computer:

![image-20220429212554851](https://s2.loli.net/2022/04/30/T3dZPmVXz28Helx.png)

本教程采用git Bash，其界面如下。

![image-20220429213831007](https://s2.loli.net/2022/04/30/fh9MjDyWtzVS3IE.png)

首先，我们进入需要创建为库的文件夹（本教程中以路径 `D:\04_coding\Python\00_Projects\00_gitTutorial\gitTutorial`为例），在git Bash中输入以下commands to change our working directory to the target one：

```bash
cd d:/
cd 04_coding/Python/00_Projects/00_gitTutorial/gitTutorial/
```

Note that we use forward slash (/) as the path separator rather than backward slash in git Bash. Then we can initialize the repository by:

```bash
git init
```

命令执行后，git Bash将返回以下内容：

![image-20220429215431016](https://s2.loli.net/2022/04/30/b68seSVOiXgYl3D.png)

Now you should see a hidden folder named `.git` in the target directory if the `show Hidden items` is activated as below:

<img src="https://s2.loli.net/2022/04/30/IBK6be92twy8PgH.png" style="zoom:67%;" />



创建文件命令：

```bash
touch readme.md
```

文件创建但并不意味这在repository里面，而是需要将文件添加进去后才能有效执行commit. 我们使用以下命令将目录下所有文件添加进去并查看git的状态:

```bash
git add ./
git status
```

![image-20220429220326378](https://s2.loli.net/2022/04/30/KAbf3pVX5gYIWUr.png)

这是，我们就可以提交修改了：

```bash
git commit -m "first change"
```

![](https://s2.loli.net/2022/04/30/8qx5vY7kzfAitPZ.png)

删除现有文件(for example, the `readme.md` file)：

```
git rm --cached readme.md
git status
```

we've delete the file and we can commit it to the repository then:

```
git commit -m "delete readme.md"
git status
```







查看git状态命令：

```bash
git status
```





> **Difference between git Bash and git CMD**[^1]
>
> [^1]:[Difference between Git GUI, Git Bash, Git CMD - Stack Overflow](https://stackoverflow.com/questions/45034549/difference-between-git-gui-git-bash-git-cmd)
>
> **Git CMD** is just like regular Windows command prompt with the `git` command. It lets you use all of Git features through command line. Useful if you are already familiar with `Windows cmd` and you only work on Windows.
>
> **Git Bash** emulates a bash environment on windows. It lets you use all git features in command line plus most of [standard unix commands](https://ss64.com/bash/). Useful if you are used to Linux and want to keep the same habits.