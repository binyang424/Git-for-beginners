# Git Tutorial for Beginners - GitHub Version Control

This git tutorial for beginners will show you how to manage your code using remote repositories on GitHub. I will be showing how to use git and all of its commands. This video is geared towards beginners just learning how to use git as it only shows the basics of git. 

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

Note that we use forward slash (/) as the path separator rather than backward slash (\\) in git Bash. Then we can initialize the repository by:

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

此时文件夹下的`readme.md`文件已经不被追踪了，但还需要手动删除。如果想还原该文件则可以：

```
git checkout -- readme.md
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

## Step 3: Create and merge branches[^2]

[^2]:[Git Tutorial for Beginners - GitHub Version Control - YouTube](https://www.youtube.com/watch?v=PWqS4NBhEY8)

create and switch to the branch named `login`:

```bash
git branch login
git checkout login
```

此时我们可以在本地文件夹下对文件做任意修改或者创建新文件，并添加and commit to the repository。然后我们在切换回原来的master分支，会发现文件并没有被更改：

```bash
git branch master
```

If we want to merge the changes in branch login to the master, we need to switch to `master` and simply type:

```
git merge login
```

## Step 4: Set up a remote repository

注意，`git remote add <name> <url>`中的`<name>`一旦确定，不能更改，对任何分支都是一样的！

```
git remote add gittutorial https://github.com/binyang424/CollaborationTest.git
```

使用`git push -u <name> <branch>`将本地内容推送到远程仓库：

```bash
git push -u gittutorial master
git push -u gittutorial login
```

此时，远程仓库里应该有了和本地一样的文件。使用以下方式可以使每次推送都包含推送人的信息：

```bash
git config --global user.name Bin Yang
git config --global user.email bin.yang@polymtl.ca
```



>修改库`url`地址可以使用以下方式:
>
>```bash
>git remote set-url gittutorial https://github.com/binyang424/test.git
>```



#### 版本回退

```bash
git log
```

or

```
 git log --pretty=oneline
```

退回到上一个版本：

```bash
git reset --hard HEAD^
```

还可以根据版本号再选择回到最新的版本，如果不记得版本号可以使用`git reflog`查看所有的操作命令及其对应版本号。

```bash
git reset --hard 62dcc
```

> Git在内部有个指向当前版本的`HEAD`指针，当你回退版本的时候，Git仅仅是把HEAD从指向`append GPL`，因此实际操作起来速度很快。





## Step 5: Clone a repository to local machine

创建文件夹

```>
mkdir chess
cd chess
git init
git pull <url>
```



## Rename or move files in git[^3]

[^3]:[How to rename or move files in git](https://www.educative.io/edpresso/how-to-rename-or-move-files-in-git)

We can use the **`git mv`** command in git to rename and move files. The syntax is shown below.

### Syntax

#### Rename file

```bash
git mv <options> oldFilename newFilename
```

-   `oldFilename`: The name of the file that we rename
-   `newFilename`: The new name of the file

> **Options**
>
> The options we can use with the `mv` command are:
>
> -   \[-f\]: Force move or rename operation. Moves or renames the file even if another file of the same name exists.
> -   \[-n\]: Does not do the actual operation; only shows what would happen.
> -   \[-k\]: Skips operation that can cause an error.
> -   \[-v\]: Report the filenames as they are renamed or moved.
>


#### Move file

```bash
git mv filename foldername
```

-   `filename`: The name of the file that is moved
-   `foldername`: The name of the folder where the file is moved

### Code

Consider the code snippet below which demonstrates the use of the `mv` command:

```bash
git mv file1.txt file2.txt
git commit -m "file1.txt renamed to file2.txt"
```

Note that although the code snippet above renames the file `file1.txt` to `file2.txt` using the `mv` command, it actually deletes the file `file1.txt` and creates a new file `file2.txt` that has the same contents as `file1.txt`.

## Reference:

