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



