## ssh 密钥
-   创建密钥
```bash
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
-  获取密钥内容
```bash
$ cat ~/.ssh/id_rsa.pub
```
-   将密钥添加到github账户
    -  settings > new ssh key
-   测试连接
```bash
$ ssh -T git@github.com
```

## 设置Git用户
```bash
$ git config --global user.name [username]
$ git config --global user.email [email]
```

## 确认远程仓库分支
```bash
$ git remote show origin
```
## 推送新分支
```bash
$ git push -u origin main
```
-   将https改为ssh
```bash
git remote rm origin
git remote add origin ssh_url
git push -u origin main