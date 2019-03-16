# github上添加一个公钥
如果没有在github上添加公钥，用git clone下载代码的时候，可能会报错，是因为没有建立起起联系，此时需要先获取一个ssh的秘钥，然后再把这个秘钥添加到github中即可,密码可以设置，也可以不用设置

#
### 1、打开git bash使用ssh -T git@github.com命令测试是否有公钥
### 2、如果没有则使用ssh-keygen -t rsa -C 'testAccount'命令生成一个key，（testAccount是你的github账户名称）
### 3、生成成功之后找到.ssh/id_rsa.pub文件，把里面的key添加到你的github上