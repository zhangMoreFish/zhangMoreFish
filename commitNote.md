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