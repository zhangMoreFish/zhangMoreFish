1.克隆远端代码到本地
git clone http://xxx.xxxx
2.查看本地分支
git branch
3.查看远端分支
git branch -r
4.提交
git commit -m "这里写备注"
5.推送本地到远程 branchName 分支名称
git push origin branchName
6.拉取远端代码到本地 拉取远端test分支与本地test分支合并
git pull origin test
拉取远端main分支与本地test分支合并
git pull origin main:test
7.删除远端分支 branchName 要删除的分支名称
git push origin --delete branchName
8.添加文件 filename.suffix文件名称+后缀名 多个文件空格隔开，然后commit+push
git add filename.suffix
8.删除文件 filename.suffix文件名称+后缀名 然后commit+push
git rm filename.suffix
9.暂存（解决pull后git无法自动merge）将本地修改暂存，pull后再重新合并 commit push
git stash save 'comment'
查看stash列表
git stash list
查看改动，查看第几个后面加 stash@{0}，从0开始，不加默认显示第一个
git stash show
应用某个存储，默认第一个，应用其他后面加 stash@{0}，从0开始
git stash apply
应用某个存储并删除，默认第一个，应用其他后面加 stash@{0}，从0开始
git stash pop
删除某个缓存，默认第一个，应用其他后面加 stash@{0}，从0开始
git stash drop
删除所有缓存的stash
git stash clear