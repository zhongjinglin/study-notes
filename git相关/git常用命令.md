# git常用命令
### 提交添加到缓存区的文件：git commit -m '备注'
### 提交修改过，但是没有添加到缓存区的文件：git commit -a -m '备注'
### 本地库初始化：git init
### 查看本地分支：git branch
### 查看远程分支：git branch -r
### 创建本地分支：git branch [name]  // 注意新分支创建后不会自动切换为当前分支
### 切换分支：git checkout [name]
### 创建新分支并立即切换到新分支：git checkout -b [name]
### 删除分支：git branch -d [name]  // -d选项只能删除已经参与了合并的分支，对于未有合并的分支是无法删除的。如果想强制删除一个分支，可以使用-D选项
### 合并分支：git merge [name]  // 将名称为[name]的分支与当前分支合并
### 创建远程分支(本地分支push到远程)：git push origin [name]
### 删除远程分支：git push origin :heads/[name]
### git push origin test:master  // 提交本地test分支作为远程的master分支，注意这句命令会删掉远程的master分支，慎用

# 版本(tag)操作相关命令
### 查看版本：$ git tag
### 创建版本：$ git tag [name]
### 删除版本：$ git tag -d [name]
### 查看远程版本：$ git tag -r