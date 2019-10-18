# gitflow-test

#### 新建工程
```
echo "# gitflow-test" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/diaozhaji/gitflow-test.git
git push -u origin master
```

### 使用git-flow
#### 初始化
初始化一个现有的git本地仓库。
```
git flow init
```
接着回答几个关于分支的问题。不用担心，使用默认值即可，直接按回车键。
```
No branches exist yet. Base branches must be created now
Branch name for production releases: [master]
Branch name for “next release” development: [develop]
How to name your supporting branch prefixes?
Feature branches? [feature/]
Release branches? [release/]
Hotfix branches? [hotfix/]
Support branches? [support/]
Version tag prefix? []
```
#### feature

创建一个新的feature分支，可以使用以下命令：
```
git flow feature start test
```
执行以下命令后，feature/test分支会被创建。
当特性开发完毕，需要将此分支合并到develop分支，可以使用以下命令实现：
```
git flow feature finish test
```
上面的命令会将feature/test分支的内容merge到develop分支，并将feature/test分支删除。

feature分支只是存在于本地仓库，如果需要多个人共同开发此特性，也可以将feature分支推送到过程仓库。
```
git flow feature publish test
```
feature 分支的生命周期持续到特性的开发完毕，当完成特性的开发，你可以使用git的分支管理命令将此feature分支删除。


#### release

通过以下命令来创建release分支：
```
git flow release start v.1.0
```
执行过完上面的命令，release分支release/v.1.0会被创建出来 ，并且切换到该分支。

当完成release分支功能的完善或者bug的修复后，执行以下命令来完成release分支：
```
git flow release finish v.1.0
```
这个命令会执行以下的操作：

- 分支release/v.1.0 merge回master分支
- 使用release/v.1.0分支名称打tag
- 分支release/v.1.0 merge回develop分支
- 删除release/v.1.0分支

#### Hotfix
可以使用以下命令来创建hotfix分支：
```
git flow hotfix start v.1.0
```
使用以下命令来结束hotfix分支的生命周期：
```
git flow hotfix finish v.1.0
```
这句命令会将hotfix分支merge到master分支和release分支，并删除该hotfix分支。
值得注意的是，如果bug修复时，正存在着release分支，那么hotfix分支会merge到release分支，而不是develop分支。




