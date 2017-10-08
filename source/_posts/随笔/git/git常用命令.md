## 强制同步版本

// 将develop分支覆盖到master
git push origin develop:master -f
git push origin release:ui-template -f



git checkout master
git reset --hard develop  //先将本地的master分支重置成develop
git push origin master --force //再推送到远程仓库

## 生成秘钥
$ ssh-keygen -t rsa -C “lio@163.com”

## 命令缩写

git config --global alias.por 'pull origin release'
git config --global alias.st 'status'
git config --global alias.co 'checkout'
git config --global alias.aa 'add -A'
git config --global alias.cm 'commit -m'