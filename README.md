## Git 的常见标志
-   U:未跟踪
-   A:新增文件
-   D:删除的文件
-   M:修改的文件
-   C:文件内有冲突

## 设置Git用户
```bash
$ git config --global user.name [username]
$ git config --global user.email [email]
```
## 查看提交日志
```bash
git log
git log --oneline 单行查看简略版日志
git log -n 查看最近 n 次提交
git log --reflog 可以查看到当前版本之后的日志
git log --reflog --oneline 也可以这样配合使用
```
-   q 键退出
## 撤销相关
```bash
git reset --hard 版本号     # 在历史版本中穿梭
git reset --hard           # 最后一次提交的内容 => 暂存区/工作区（相当于重制）
git reset < file >         # 仓库 => 暂存区
git reset .                # 仓库 => 暂存区
git checkout < file >      # 暂存区 => 工作区
git chectout .             # 暂存区 => 工作区
```

# 创建远程仓库
## ssh 密钥
-   创建密钥对
```bash
$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
![](https://cdn.jsdelivr.net/gh/baoblei/imgs_md/20230304203709.png)
-  获取公钥内容
```bash
$ cat ~/.ssh/id_rsa.pub
```
-   将公钥添加到github账户
    -  settings > new ssh key
-   测试连接
```bash
$ ssh -T git@github.com
```
## 添加远程仓库地址到本地
```bash
$ git remote add origin SSH地址   # origin 为远程仓库别名，可更换
```
## 查看/删除关联的仓库
```bash
$ git remote -v
$ git remote rm origin
```

## 分支
```bash
git branch          # 查看本地所有分支
git branch 新分支    # 创建新分支
git checkout 分支名  # 切换分支
git branch -d 分支名 # 删除分支，只能删除当前工作分支外的分支  -D 为强制删除
git checkout -b 分支名 # 创建并直接切换分支
git merge 分支名       # 合并分支
```
  
-   确认远程仓库分支
```bash
$ git remote show origin 
```
## 推送（新）分支
```bash
$ git push -u origin main   # “-u” 会创建新分支
```
- 设置忽略文件
  .gitignore
  语法规范:.gitignore 可以使用标准的 glob 模式匹配（glob 模式是指 shell 所使用的简化了的正则表达式）：

    -   所有空行或者以注释符号 # 开头的行都会被 Git 忽略；
    -   星号（*）匹配零个或多个任意字符；
    -   [abc] 匹配任何一个列在方括号中的字符；
    -   问号（?）只匹配一个任意字符；
    -   [a-z] 匹配所有在这两个字符范围内的字符；
    -   匹配模式最后跟反斜杠（/）说明要忽略的是目录；
    -   匹配模式以反斜杠（/）开头说明防止递归；
    -   要忽略指定模式以外的文件或目录，可以在模式前加上惊叹号（!）取反。
- git清除本地缓存（改变成未track状态），然后再提交
```bash
git rm -r --cached .
git add .
git commit -m 'update .gitignore'
```
-   在每个clone下来的仓库中手动设置不要检查特定文件的更改情况
```bash
git update-index --assume-unchanged PATH                  //在PATH处输入要忽略的文件
```
-   将https改为ssh
```bash
git remote rm origin
git remote add origin ssh_url
git push -u origin main
```

## clone/fetch/merge/pull
### clone 
- 自动将远程主机命名为 origin，拉取它的所有数据。

- 创建一个指向它的 master 分支的指针，并且在本地将其命名为 origin/master。

- 创建一个与 origin 的 master 分支在指向同一个地方的本地 master 分支。
![](https://cdn.jsdelivr.net/gh/baoblei/imgs_md/20230304211628.png)
  
### fetch




参考：
-   https://blog.csdn.net/Henry_ID/article/details/118615158?ops_request_misc=&request_id=&biz_id=102&utm_term=vscode%E8%81%94%E7%BB%93%E8%BF%9C%E7%A8%8B%E4%BB%93%E5%BA%93&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-2-118615158.nonecase&spm=1018.2226.3001.4187
-   https://blog.csdn.net/itworld123/article/details/120220097