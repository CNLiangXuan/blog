# Git

版本控制： 记录文件内容变化，方便查看版本修改情况，方便版本切换

设置用户签名

若未设置则代码无法提交，邮箱仅代表本地

$ git config --global user.name LX       
$ git config --global user.email LX@3513148304qq.com

查看文件

$ ll
$ ll -a //查看隐藏文件

git查看本地库命令与linux一致

vim快捷键

yy      复制

p        粘贴

git 命令

```
git status  //查看当前文件状态
git add 文件名 //把状态发生改变的文件加进暂存区
git commit -m "日志信息" 文件名     //提交代码
git reflog                        //查看版本信息
git log                           //查看版本详细信息
git reset --hard 版本号           //穿梭到对应版本
git branch 分支名                 //创建分支
git branch -v                     //查看分支
git checkout 分支名                //切换分支
git merge 分支名                   //把指定的分支合并到当前分支上
git push                          //将代码推送至远程库
git pull                          //从远程库更新代码到本地
git remote add 远程库（网址）      //绑定远程仓库
git clone 远程库（网址）           //克隆别人的仓库到本地
```