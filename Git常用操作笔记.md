[TOC]

## 一、介绍

Git --- The stupid content tracker, 傻瓜内容跟踪器。Linus Torvalds 是这样给我们介绍 Git 的。

Git 是用于 Linux内核内核开发的版本控制工具。与常用的版本控制工具 CVS, Subversion 等不同，它采用了分布式版本库的方式，不必服务器端软件支持（wingeddevil注：这得分是用什么样的服务端，使用http协议或者git协议等不太一样。并且在push和pull的时候和服务器端还是有交互的。），使源代码的发布和交流极其方便。 Git 的速度很快，这对于诸如 Linux kernel 这样的大项目来说自然很重要。 Git 最为出色的是它的合并跟踪（merge tracing）能力。

Git 没有对版本库的浏览和修改做任何的权限限制。

目前GIT已经可以在windows下使用，主要方法有二：msysgit和Cygwin。

## 二、集中式和分布式版本控制工具的优劣

### 1.集中式

在管理项目时，存放的是项目版本与版本之间的差异，需要的硬盘空间会相对的小一点，可是回溯版本的速度会慢一点

（1）优点

代码放在单一的服务器上，便于项目的管理

（2）缺点

服务器宕机：写的代码得不到保障

服务器毁坏：整个项目的历史记录都会丢失

### 2.分布式

在管理项目时，存放的是项目版本的索引（项目的完整快照），每个客户端都可以放下整个项目的历史记录，需要的硬盘空间会相对大一点。

然而git团队对代码进行了极致的压缩，所以最终所需的实际空间比集中式大不了多少，而且回溯版本的速度更快

## 三、Git的基本配置

使用git config时，用--system选项，读写的是当前系统下的文件

使用git config时，用--global选项，读写的是当前用户下的文件

使用git config时，用--system选项，读写的是当前项目下的文件

可以使用 git config --list来展示当前配置信息

每个级别的配置都会覆盖上层的相同配置

## 四、Linux基础命令

### 1.echo

相当于js的console.log，打印输出指定内容

### 2.>文件名.文件格式

在当前文件夹中创建一个指定文件

echo '字符串' >文件名.文件格式	表示	创建一个指定文件并在文件中打印	指定字符串

### 3.touch 文件名.文件格式

在当前文件夹中创建一个指定文件

### 4.rm 文件名.文件格式

在当前文件夹中删除一个指定文件

### 5.ll

显示	在当前文件夹下的子文件和子目录

### 6.find

find ./	表示	显示	在当前文件夹下的子文件和子目录下的全部文件（包括子文件）

find ./ -type f	显示	在当前文件夹下的子文件和子目录下的全部文件（包括子文件）中的文件（不包括目录）

find ./路径 -type f表示在指定路径中查找所有文件

### 7.clear

清除命令行界面中的所有命令

### 8.mv

重命名文件

语法：mv	源文件.格式	修改后的名字.修改后的格式

### 9.cat

cat 文件.格式

查看指定文件的文本内容

### 10.vim

vim 文件.格式

进入指定文件的编辑模式

必须在英文模式下

（1）按	i	键才可以开始插入文本模式

（2）按	esc	键退出插入文本模式，进入命令模式

​					1）输入	:wq	保存并退出编辑模式

​					2）输入	:set nu 显示行号

​					3）输入	q!	强制退出编辑模式

## 五、git对象

git核心部分是一个简单的键值对数据库。你可以向该数据库插入任意类型的内容，它会返回一个键值，通过该键值可以在任意时刻再次检索该内容（key就是value对应的hash）

git对象指的是文件的每一个版本

要使用git命令先要将当前文件转为git对象

向数据库写入内容 并返回对应键值

命令：	echo ‘test’ | git hash-object -w --stdin

-w 选项指示 hash- - object 存储数据对象；若不指定此选项，则该命令仅返回对应的键值，而不会存储数据对像。

-stdin （ standard input ） 选项则指示该命令从标准输入读取内容（而返回的是一个内容的键值）；若不指定此选项 ，则须在命令尾部给出待存储文件的路径 ，表示将指定文件存入objects数据库中。

~~~markdown
$ echo 'test' | git hash-object --stdin//此处表示直接存储在git数据库中
9daeafb9864cf43055ae93beb0afd6c7d144bfa4
~~~

git hash- object -w 文件路径： 存文件	不只是返回键值，还将该对象写入数据库
git hash-object 文件路径：	
返回对应文本的键值9daeafb9864cf43055ae93beb0afd6c7d144bfa4
返回：
该命令输出一个长度为 40 个字符的校验和。 这是一个 SHA-1哈希值。



该命令自动判断内容的类型，并为我们显示格式友好的内容

~~~git
git cat-file -p 9daeafb9864cf43055ae93beb0afd6c7d144bfa4
test
~~~

获得键值对的类型，此处为blob类型

~~~git
$ git cat-file -t 9daeafb9864cf43055ae93beb0afd6c7d144bfa4
blob
~~~

将指定文件中的数据对象存入object中

~~~
git hash-object -w 文件名.格式
~~~

查看指定文件下的子文件

~~~
$ find .git/objects/ -type f
~~~

注：每次文件内容修改后，都要将修改后的文件数据放入git数据库中

## 六、树对象

每次操作都要获取文件的每一个版本对应的SHA-1值，再进行操作

并且只保存的文件内容并没有保存文件名

所以我们要用到树对象

树对象在版本控制中对应的是项目的版本，git对象对应的是文件内容

### 1.构建树对象

利用update-index命令为文件的首个版本创建一个暂存区。并通过write-tree命令生成树对象

~~~
git update-index --add --cacheinfo 100644  文件键值 自定义的文件名.格式
~~~

若再次操作暂存区时，不改文件名，会造成文件内容的覆盖，将最新的内容覆盖掉原有的内容

若想要加入新的文件，则必须添加--add

### 2.查看暂存区

git ls-files -s

### 3.树对象放入版本库

git write-tree

将暂存区快照生成一个树对象（项目的快照），并返回对应的树对象的键值，放到版本库中

## 七、提交对象

对树对象进行了封装，并附上个人信息

创建提交对象：

每一次git commit不仅生成提交对象，还会将对应快照（树对象）提交到版本库

创建	提交对象，并添加注释：

~~~markdown
echo 'first commit' | git commit-tree 1fa50d8ae802f73870dabd5e8b104e79b5bce365
~~~

将指定提交对象放入另一个提交对象中，并加上注释：

~~~
echo 'second commit' | git commit-tree e97f653e74dd2e10f3527e4304d132b9d0e6a094 -p 75b1a53fc203e30e7d63aebeb48330e1e8bb39b1
~~~

## 八、高层命令

每个命令都封装了多个底层命令

### 1.git add ./

将当前工作目录中的所有文件的修改做成git对象，放入版本库中，再从版本库中将git对象放入暂存区

修改一次add一次，就生成一次git对象

一次提交，必定会有一个提交对象，一个树对象，多个git对象

### 2.git commit -m '注释内容'

提交。生成一个树对象，一个提交对象

每当运行git commit命令时，git会创建一个新的提交，并移动HEAD所指向的分支来使其指向该提交

### 3.git status

查看当前状态

只要提示change to be commited	就说明是已暂存状态

一个文件可能有多个状态

红色表示已修改状态，绿色表示已放入暂存区

### 4.git diff --cached或者git diff --staged

查看	已经暂存起来准备提交的文件

### 5.git commit -a -m '注释'

跳过使用暂存区，将已经跟踪过的文件暂存起来一并提交，从而跳过git add的步骤（此时只能对跟踪文件操作）

对于修改后的文件可以直接跳过缓存区，直接提交

### 6.git rm

在工作目录中删除文件，再将修改放入暂存区

### 7.git mv

相当于保存原有文件内容并删除，然后生成一个新文件，并将内容放入新文件中

最后再将修改放入暂存区

### 8.git log

git log --pretty=oneline 将全部日志整齐压缩的放在一起

git log --oneline 将全部日志整齐压缩的放在一起，但是将哈希值值显示前八位

且可以查看当亲分支情况，如下行代码表示当前分支为test，master分支含有一个文件且注释为	’这时test.txt文件v1版本‘

~~~
26d0028 (HEAD -> test, master) 这时test.txt文件v1版本
~~~



## 九、git操作的最基本流程

git init	创建工作目录 对工作目录进行修改

git add ./ 

​	git hash-object -w 文件.格式（修改了多个文件，命令就执行多少）

​	git update-index...

git commit -m '注释内容'

​	git write-tree

​	git commit-tree

## 十、git分支

git的分支本质上是指向提交对象的可变指针，git的默认分支就是master

而.git/refs目录保存了分支及其对应的提交对象，分支中保存的是哈希值

.git/head中保存的是在命令行界面当前的分支名

每新建一个分支就相当于新建了当前项目的一个副本

每次对原项目进行修改都要在master分支下进行新建一个分支，对分支进行修改

### 1.git branch 名字

创建一个分支，并自定义名字

git branch 分支名，表示	显示分支列表

### 2.git checkout 名字

切换分支到指定分支

这样即使修改代码有问题，也可以回到master分支（最初的代码版本）

切换分支会导致head、暂存区、工作目录三个地方发生更改，所以每次切换分支前都要确保当前分支是已提交状态

如果当前分支有未暂存的修改或者有未提交的暂存。分支可以切换成功，但是这种操作可能会污染其他分支

### 3.git 别名

git  config --global alias.自定义语句名  命令语句

~~~
git  config --global alias.line 'log --oneline --decorate --graph --all'
~~~

将’log --oneline --decorate --graph --all‘语句替换为line

则要查看分支历史时，可以直接输入 git line就可以了

### 4.git branch -d 分支名

删除指定的已经被合并的分支

将d换成D，代表强制删除

### 5.git branch -v

查看每一个分支的最后一次提交

### 6.git branch 分支名 哈希值

表示新建一个分支指向指定的提交对象

注意：此命令后，还要将当前分支切换为新建的那一个分支（git checkout 分支名）

### 7.git checkout -b 分支名

新创建一个分支，并指向该分支

### 8.git merge合并分支

（1）快进合并

回到master分支，执行git merge 分支名，进行合并

只是简单的将指针向前推进（指针右移）

结果如下所示：

~~~markdown
* d4f9478 (HEAD -> master, quickbug) 第六次提交，为解决紧急bug
| * 43fb606 (issue53) 第六次提交
|/
* 40a0415 这是test.txt文件v2版本
* 3dbc671 这是test.txt文件v1版
~~~

此时，分支quickbug已经没有用了，可以直接git branch -d quickbug 删除

效果如下：

~~~markdown
* d4f9478 (HEAD -> master) 第六次提交，为解决紧急bug
| * 43fb606 (issue53) 第六次提交
|/
* 40a0415 这是test.txt文件v2版本
* 3dbc671 这是test.txt文件v1版
~~~

## 十一、git存储

当在当前分支上操作时，想要切换到一个分支上做一些事情，但这是不想要提交未结束的分支上的操作，这时可以将其存储起来

### 1.git stash

将修改后的文件存起来

### 2.git stash apply

将存储的操作应用到当前分支

### 3.git stash drop stash名

将存储的操作应用后，要将存储栈删掉

~~~markdown
git stash drop stash@{0}
~~~

## 十二、撤回操作

### 1.git checkout --文件名

撤回工作目录中对文件的修改的操作

新版本中可以用git restore代替

### 2.git reset HEAD 文件名.格式

将文件从暂存区中撤回到工作目录

### 3.git commit --amend

当前的提交代替上一次的提交

### 4.git reset --soft HEAD~

撤销了上一次git commit命令

将该分支移动回原来的位置，而不会改变索引和工作目录。此时可以再次运行git commit命令来完成git commit --amend所要做的事情（该命令只会动head）

### 5.git reset --soft 哈希值

指针移动到指定head

执行上述命令，结果如下：

~~~
a1f8784 (HEAD -> master) HEAD@{0}: reset: moving to a1f8784
c918448 HEAD@{1}: reset: moving to HEAD~
a1f8784 (HEAD -> master) HEAD@{2}: commit: 第三次提交file.txt，且为v3版本
c918448 HEAD@{3}: commit: 第二次提交file.txt，且为v2版本
5fbb6b0 HEAD@{4}: commit (initial): 第一次提交file.txt，且为v1版本
~~~

### 6.git reset --mixed 哈希值

用哈希值的内容重置HEAD内容	重置暂存区

### 7.git reset --hard HEAD~

撤销了最后的提交、git add和git commit命令以及工作目录中的所有工作

强制覆盖工作目录

减少该命令的使用，有风险

### 8.git branch xxx 哈希值

可以通过该命令，新建一个分支指向之前的提交，相当于回溯到了之前的操作

## 十三、tag

标签相当于不会改变的分支	只是一个特定提交的引用

### 1.git tag

列出所有的标签

### 2.git tag 标签名

给当前提交对象创建标签

### 3.git tag 标签名 指定对象的哈希值

根据哈希值来给指定对象创建标签

### 4.git show 标签名

查看指定标签

### 5.git tag -d 标签名

删除指定标签

### 6.git checkout 标签名

查看标签所指向的文件版本

但是会使仓库处于分离头指针状态。即head没有指向分支

在该情况下的修改，在提交后，标签不会变化，新的提交不属于任何分支导致无法访问（除非通过哈希值来访问）

### 7.git checkout -b 分支名

查看某标签指向的文件版本的同时，创建一个分支指向该文件版本

## 十四、远程仓库

### 1.将本地项目上传至远程仓库的基本流程

~~~
git init //初始化一个git的本地仓库
 
git add 文件.格式 //将我的文件放到暂存区
 
git commit -m “first commit” //提交
 
git remote add 指定名 your_first_git_address //将git address命名为指定名称
 
git push -u origin 分支（默认是master） //将本地的master分支推送到origin主机，同时指定origin为默认主机，后面就可以不加任何参数使用git push了
//同时会自动生成一个远程跟踪分支
 
git remote add Mars your_second_git_address //将第二个git address命名为Mars
 
git push -u Mars 分支（默认是master） //再次上传
~~~

注：origin是远程仓库别名，是通过 配置远程仓库设置而成的

~~~
git remote add origin http://xxxx@git.XXXX.com/scm/wbqa/xxxx.git
# origin 为远程仓库别名  后面http 为远程仓库地址
~~~

本地master上传到远程仓库分支下：

~~~
git push <远程主机名> <本地分支名>:<远程分支名>
git push origin master:djs
# origin为设置的远程仓库别名, master为本地分支名, djs为远程分支名
~~~

### 2.克隆远程仓库到本地

git clone url

克隆下来的项目默认orgin别名就是orgin

在克隆项目中，本地分支和远程跟踪分支是同步关系

### 3.更新项目

（1）git fetch 别名	从远程获取代码库

（2）get merge 远程跟踪分支	将服务器上的任何更新（假设有人这时候推送到服务器了）合并到你的当前分支

### 4.拉取数据

git pull 命令用于从远程获取代码并合并本地的版本。

git pull 其实就是 git fetch 和 git merge FETCH_HEAD 的简写。 命令格式如下：

```
git pull <远程主机名> <远程分支名>:<本地分支名>
```

将远程主机 origin 的 master 分支拉取过来，与本地的 brantest 分支合并。

~~~
git pull origin master:brantest
~~~

如果远程分支是与当前分支合并，则冒号后面的部分可以省略。

```
git pull origin master
```

### 5.显示远程仓库列表

```
git remote -v
```

### 6.显示当前的跟踪分支与提交信息

git branch -vv

### 7.git branch -v

显示每个（本地）分支当前指向的提交记录的哈希值，以及和其上游分支的相对位置（如果有的话）

### 8.远程分支

远程引用是对远程仓库的引用（指针），包括分支、标签等等

### 9.跟踪分支

它也是一个本地分支，只是它对应了一个远程分支，如果我们本地的某个分支对应了一个特定的远程分支，那么它就是追踪分支。

是本地仓库对远程仓库中的某个远程分支的状态的记录，它们以 `“(远程仓库名)/(分支名)”` 形式命名

在跟踪分支里输入 `git push`，Git 会自行推断应该向哪个服务器的哪个分支推送数据。同样，在这些分支里运行 `git pull` 会获取所有远程索引，并把它们的数据都合并到本地分支中来。

### 10.设置远程追踪分支

新建分支，并指定想要追踪的远程追踪分支：		git checkout --track 远程追踪分支名

将一个已经存在的本地分支 改成 一个 跟踪分支：	git branch -u 远程追踪分支名

### 11.删除远程分支

git push origin --delete 远程分支名	删除远程分支

git remote prune origin --dry-run	列出仍在远程跟踪但是远程分支已经被删掉的无用分支

git remote prune origin	清除上述命令列出的远程跟踪分支

### 12.pull request

当想更正别人仓库里的错误时，要走一个流程：

1. 先 fork 别人的仓库，相当于拷贝一份
2. clone 到本地分支，做一些 bug fix
3. 发起 pull request 给原仓库，让他看到你修改的 bug
4. 原仓库 查看这个 bug，如果是正确的话，就会 合并到他自己的项目中

至此，整个 pull request 的过程就结束了。

每次发起新的pull request时，要去拉取最新的原仓库的代码，而不是自己fork的那个仓库

git remote add 名称 url 

git fetch 远程仓库名

git merge 对应的远程跟踪分支







































































## 注意

（1）git命令行界面中 选中即复制