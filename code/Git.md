# 本地部署
公钥私钥生成以及链接github/gitee仓库
https://blog.csdn.net/yanqiu12138/article/details/131497917

可能在ssh -T时遇见 git@gitee.com: Permission denied (publickey). 报错
参考 https://cloud.tencent.com/developer/article/1594769 使用ssh-add ~/.ssh/id_rsa命令即可


# github与gitee同步
https://gitee.com/help/articles/4284:?skip_mobile=true#article-header0
后续本地更改代码后只需要对gitee也推送一次即可。由于此时我们多了gitee的远程库，在push时要指定远程库
```git
git push 远程库名 分支名
eg：git push gitee master
```
在拉取时也要注意拉取的远程库
```git
git pull 远程库名 分支名
eg：git pull origin master
```