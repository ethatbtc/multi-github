# multi-github

## 生成 SSH
由于不同的 GitHub 不能使用同一个 SSH 公钥，所以要生成两个不同的 SSH 分别对应两个主账户和副账户。

生成 SSH 的命令如下：
```
ssh-keygen -t rsa -f ~/.ssh/id_rsa1 -C "mail1@gmail.com"
ssh-keygen -t rsa -f ~/.ssh/id_rsa2 -C "mail2@gmail.com"
```
-f 选项指定生成钥匙对的文件名。

## SSH 配置
编辑 `~/.ssh/config SSH` 配置文件，没有该文件则新建。
```
# mail1@gmail.com
Host github-1.com
HostName github.com
User git
IdentityFile ~/.ssh/id_rsa1

# mail2@gmail.com
Host github-2.com
HostName github.com
User git
IdentityFile ~/.ssh/id_rsa2
```
然后，以后使用 main 账户添加远程仓库需要这样添加：
```
git remote add origin git@github-1.com:username/demo.git
```
类似，使用 blog 账户时是这样：
```
git remote add origin git@github-2.com:username/demo.git
```
而非原来的：
```
git remote add origin git@github.com:username/demo.git
```
