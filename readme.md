# Git 的常见命令

记录一些经常会用到的Git 命令



## 目录

* [创建初始仓库](#创建初始仓库)
* [删除第一个Commit提交](#删除第一个Commit提交)
* [查找Commit在哪个分支上](#查找Commit在哪个分支上)
* [查找某个文件在哪个Commit上被删除](#查找某个文件在哪个Commit上被删除)
* [查找某个文件被添加进repo时的Commit](#查找某个文件被添加进repo时的commit)
* [推送一个空提交的分支](#推送一个空提交的分支)
* [统计历史提交的Commit个数](#统计历史提交的Commit个数)
* [找到一个empty_tree对应的sha值](#找到一个empty_tree对应的sha值)
* [GitDiff时获取完整的file_sha](#GitDiff时获取完整的file_sha)
* [查看git_unpacked_object和磁盘占用空间](#查看git_unpacked_object和磁盘占用空间)





## 创建初始仓库

```bash
git init repo
```



## 删除第一个Commit提交

```bash
git update-ref -d HEAD
```



## 查找Commit在哪个分支上 

```bash
git branch -r --contains commitid
```



## 查找某个文件在哪个Commit上被删除

```bash
git log --oneline --full-history -- prospector
```



## 查找某个文件被添加进repo时的Commit

```bash
# 示例仓库(github.com/git/git)
git log --no-merges --diff-filter=A builtin-*.c 
```



## 推送一个空提交的分支

```bash
commit_id=$(git commit-tree -m 'Distribution branch' 4b825dc642cb6eb9a060e54bf8d69288fbee4904)
git push origin ${commit_id}:refs/heads/dist
```

```
4b825dc642cb6eb9a060e54bf8d69288fbee4904 is a special hash value in git which denotes an empty tree. And it does not change from repo to repo.
```



## 统计历史提交的Commit个数

```
git rev-list --all --count
```



## 找到一个empty_tree对应的sha值

```bash
git hash-object -t tree /dev/null
4b825dc642cb6eb9a060e54bf8d69288fbee4904

#the SHA-256 empty tree hash ID is:
6ef19b41225c5369f1c104d45d8d85efa9b057b53b14b4b9b939dd74decc5321
```



## GitDiff时获取完整的file_sha

```bash
git diff 946d60369589d6a269938edd65c0a6a7b1c3ef5c 3b990136bfab74249f166dd742fd8e61637e63d9 --full-index
```



## 查看git_unpacked_object和磁盘占用空间

```bash
git count-obbject -v —H
```

