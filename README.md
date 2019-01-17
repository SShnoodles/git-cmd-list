# git-cmd-list
写给自己的git命令清单。

只列命令作用，不涉及太多概念和流程讲述。





## 常用命令

### 查看文件状态

```js
git status
```

### 把修改的文件添加到暂存区

```js
git add <file name>  // 添加单个文件
git add .    // 添加全部
```

### 提交
```js
git commit -m "初次提交"  // 注释
```

### 推送远端

```js
git push origin <branch name>
```

### 拉取更新

```js
git pull
```

### 克隆远端仓库到本地

```js
git clone <git@github.com:SShnoodles/review-git-cmd.git>
```

### 本地已有仓库初始化到远端

```js
git remote add origin <git@github.com:SShnoodles/review-git-cmd.git>
git push -u origin master
```



## 分支

```js
// 创建分支
git checkout -b <new branch> // -b 创建并且直接切换到新分支
// 查看分支
git branch
// 切换分支
git checkout <branch name>
// 删除分支
git branch -d <branch name>
// 强删
git branch -D <branch name>
```



### 合并分支

#### merge

```js
// 如当前分支为master，把dev分支合并到master。
// Fast-forward 模式，这种模式会丢掉分支信息
git merge dev

// 不使用Fast-forward，生成一个新的commit。
git merge --no-ff -m "提交注释" dev

```

#### rebase（变基、衍合）

```js
// dev打补丁到master
git rebase master server

// 如当前分支为dev，把在dev里提交的改变移到master里重演一遍。
git rebase master

// 出现冲突(conflict)，再解决完冲突后，add => continue 继续rebase
git add <file>
git rebase --continue

// 终止rebase
git rebase --abort
```



## 版本回退

`HEAD`表示当前版本

上一个版本就是`HEAD^`

 [操作错误情况处理(建议看此篇)](https://github.com/k88hudson/git-flight-rules/blob/master/README_zh-CN.md)

### 暂存回退

```js
git checkout -- <file>
```

### 提交回退

```js
// 回退上一个版本，commit的更改会保留
git reset –-soft HEAD^
// 彻底回退上一个版本
git reset --hard HEAD^
// 彻底回退某次提交,可以用log查看commit id
git reset --hard <commit id>

// 回退会产生一个新的提交
git revert HEAD^
git revert <commit id>
```



## 临时储藏

```js
// 存 
git stash
// 取
git stash apply <指定编号>
// 删
git stash drop <指定编号> 
// 取+删
git stash pop <指定编号> 
// git stash list
```



## 标记

```js
// 打标记
git tag <tag name>
// 切换到标记，类似只读模式
git checkout <tag name>
// 已此标记切出一个新分支
git checkout -b <branch name> <tag name>
```



## 日志

### 查看

```js
// 简单
git log
// 删除的记录也可以看到
git reflog

// 好看的模板
git log --graph --pretty=oneline --abbrev-commit
```

### 搜索

```js
// 作者
git log --author <name>
// 提交关键字
git log --grep <keywords>
// 文件修改记录
git log -p -- README.md
```



## 参考文献

一些概念或者流程不明白的可以参考这两个。

[廖雪峰](https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

[gitbook](https://0532.gitbooks.io/progit/content/index.html)

