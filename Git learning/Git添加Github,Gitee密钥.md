### Git添加Github,Gitee密钥

#### 清除git全局设置

```shell
git config --global --list    #进行查看你是否设置
git config --global --unset user.name "你的名字"
git config --global --unset user.email "你的邮箱"
```

#### 生成新的SSH Keys

GitHub

```shell
ssh-keygen -t rsa -f ~/.ssh/id_rsa.github -C "邮箱地址"
```

Gitee

```shell
ssh-keygen -t rsa -f ~/.ssh/id_rsa.gitee -C "邮箱"
```

在`~/.ssh/`目录下生成以下文件

```shell
id_rsa.github
id_rsa.github.pub
id_rsa.gitlab
id_rsa.gitlab.pub
```

#### 添加识别 SSH keys 新的私钥

```shell
ssh-agent bash
ssh-add ~/.ssh/id_rsa.github
ssh-add ~/.ssh/id_rsa.gitee
```

#### 多账号必须配置 config 文件

```shell
# gitHub 
Host github.com
User 注册github的邮箱
Hostname ssh.github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa
Port 443

# gitee
Host gitee.com
    Port 22
    HostName gitee.com
    User git
    IdentityFile ~/.ssh/id_rsa.gitee

```

#### 在 Github 和 Gitee 网站添加 SSH

GitHub

1. 登录 Github
2. 点击右上方的头像，点击 settings
3. 选择 SSH key
4. 点击 Add SSH key

Gitee

1. 登录 Gitee
2. 点击右上方的头像，点击 设置
3. 后续步骤如 Github添加过程 码云 会提示你输入一次你的 Gitee 密码 ，确认后即添加完毕

#### 测试是否连接成功

```shell
ssh -T git@github.com
ssh -T git@gitee.com     #出现successfully即是成功
```

