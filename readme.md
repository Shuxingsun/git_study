### 配置git环境

***

**添加配置**

```
git config [--local | --global | --system] user.name 'Your name'
git config [--local | --global | --system] user.email 'Your email'

```

**查看配置**

```
git config --list [--local | --global | --system]
```

**区别**

```
local：区域为本仓库
global: 当前用户的所有仓库
system: 本系统的所有用户
```

**git add . 和 git add -u区别**

```
git add . ：将工作空间新增和被修改的文件添加的暂存区
git add -u :将工作空间被修改和被删除的文件添加到暂存区(不包含没有纳入Git管理的新增文件)
```

**将文件复制到仓库**

```
cp 被拷贝文件名 新建文件名 ; 复制一个新的文件
cp -r 被拷贝目录 新建目录 ; 拷贝目录
```

**查看文件操作**

- clear   清空cmder窗口内容

- cd   进入某个文件夹

- cd  ../  返回上级目录

- pwd   查看当前的绝对路径

- ls   查看当前目录的文件列表   默认不显示以‘ . ’开头的文件
  - ls -l  ;  查看文件列表并显示更新时间
  - ls -al;查看所有文件
- ls  路径  ; 查看指定路径文件的内容列表

- cat    路径   ;  查看指定文件的具体内容(文字，代码)   内容过多会一直滚动页面  因此不常用

- head    路径  ;   查看指定文件的具体内容(文字，代码)  默认前10行   可通过 -n  数字  修改

**增加文件**

* mkdir   文件夹名/  ;  创建指定名称的文件夹

- mkdir  -p  文件名/文件名/文件名......  ；   创建多层级的目录文件
- 创建同一目录的多个目录只需要加空格隔开即可  例 ： mkdir  a  b  c

- cp  被拷贝文件名  新建文件名  ;   复制一个新的文件
  
- cp  -r  被拷贝目录  新建目录  ;   拷贝目录
  
- touch 文件名加后缀 ;   创建一个指定文件名的空的文件

  - 创建同一目录的多个文件只需要加空格隔开即可   例 : touch  1.js  2.js  3.js

- echo  内容  >   文件名  ;  创建并添加指定内容的文件   如果已经有这个文件则覆盖此文件内容
  * 如果想要追加要写两个   >     例如 ： echo  内容  >>   文件名
  * 追加两行内容 ;  例 :  echo   -e    "1\n2"   >>   1.txt

  

### 文件命令

***

复杂命令：

```
mv oldfilename newfilename
git add newfilename
git rm oldfilename
```

简单命令：

```
git  mv  [old file name]  [new file name]
git commit -m 'some information'

```

### git log 查看版本历史

***

```
git log --all 查看所有分支的历史
git log --all --graph 查看图形化的 log 地址
git log --oneline 查看单行的简洁历史。
git log --oneline -n4 查看最近的4条简洁历史。
git log --oneline --all -n4 --graph 查看所有分支最近4条单行的图形化历史。
git help --web log 跳转到git log 的帮助文档网页

```

```
git branch -v 查看本地有多少分支
```



### 图形界面工具来查看版本历史

***

```
gitk
```



### 探秘.git目录

***

查看`.git`文件夹下的内容：

```
ls .git/ -al
```

如下

```
drwxr-xr-x 1 sunchanghui 197121   0 Sep 11 01:25 ./
drwxr-xr-x 1 sunchanghui 197121   0 Sep 11 00:53 ../
-rw-r--r-- 1 sunchanghui 197121  16 Sep 11 00:53 COMMIT_EDITMSG
-rw-r--r-- 1 sunchanghui 197121  23 Sep 10 23:57 HEAD
-rw-r--r-- 1 sunchanghui 197121 162 Sep 11 00:02 config
-rw-r--r-- 1 sunchanghui 197121  73 Sep 10 23:57 description
-rw-r--r-- 1 sunchanghui 197121 175 Sep 11 01:25 gitk.cache
drwxr-xr-x 1 sunchanghui 197121   0 Sep 10 23:57 hooks/
-rw-r--r-- 1 sunchanghui 197121 137 Sep 11 00:53 index
drwxr-xr-x 1 sunchanghui 197121   0 Sep 10 23:57 info/
drwxr-xr-x 1 sunchanghui 197121   0 Sep 11 00:33 logs/
drwxr-xr-x 1 sunchanghui 197121   0 Sep 11 00:53 objects/
drwxr-xr-x 1 sunchanghui 197121   0 Sep 10 23:57 refs/
```

```
cat命令主要用来查看文件内容，创建文件，文件合并，追加文件内容等功能。
cat HEAD 查看HEAD文件的内容
git cat-file 命令 显示版本库对象的内容、类型及大小信息。
git cat-file -t b44dd71d62a5a8ed3 显示版本库对象的类型
git cat-file -s b44dd71d62a5a8ed3 显示版本库对象的大小
git cat-file -p b44dd71d62a5a8ed3 显示版本库对象的内容
```

`.git`里几个常用的如下:

```
HEAD：指向当前的工作路径
config：存放本地仓库（local）相关的配置信息。
refs/heads: 存放分支
refs/heads/master/: 指向master分支最后一次commit
refs/tags: 存放tag，又叫里程牌 （当这次commit是具有里程碑意义的 比如项目1.0的时候 就可以打tag）
objects：核心文件，存储文件
```

`.git/objects/` 存放所有的 git 对象，对象哈希值前 2 位作为文件夹名称，后 38 位作为对象文件名, 可通过 git cat-file -p 命令，拼接文件夹名称+文件名查看。

