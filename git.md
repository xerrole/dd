# 使用多个github账号

## windows篇

### 第一个账号，此例使用github desktop，因此按照git desk的默认操作安装完毕即可。(假设账号为account1@github.com)

### 第二个账号

**1. 生成密钥对并为github账号添加新的授权。**

    ssh-keygen -t rsa -C account2@github.com

输入密钥的文件名`account2_rsa`后两次回车（如需更高安全级别这里的两次回车可设定口令），在`~\.ssh`文件夹下生成公钥和密钥文件`account2_rsa.pub`和`account2_rsa`。

登录您的github账号，将公钥account2_rsa.pub中的key添加到账号的`SSH key`列表中进行授权。

**2. 配置ssh**

在`~\.ssh\config`文件中配置以下内容

    Host account1
      HostName github.com
      IdentityFile ~/.ssh/github_rsa  (这是git desk默认使用的密钥文件)
      User account1
    Host account2
      HostName github.com
      IdentityFile ~/.ssh/account2_rsa
      User account2

