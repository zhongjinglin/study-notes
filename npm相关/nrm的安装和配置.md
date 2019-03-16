# 什么是nrm
nrm 是一个 npm 源管理器，允许你快速地在 npm 源间切换

# 安装nrm
在命令行执行命令npm install -g nrm全局安装nrm

# 命令
nrm ls -- 查看可选择的源

nrm use [name] -- 切换源

nrm add registry http://127.0.0.1:8080/repository/npm-public -- 新增源

nrm test [name] -- 测试相应源的响应时间