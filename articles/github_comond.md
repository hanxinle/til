# GitHub 命令行

* 设置姓名和邮箱

  git config --global user.name "xxxx"

  git config --global user.email "xxxx@yyy.zzz"

* 创建并初始化本地空仓库

  git init <repo_name>

* 查看提交的状态

  git status

* 暂存区中添加更改

  git add <file_name>

* 记录一行提交信息

  git commit -m "commit info"

* 提交记录

  git log

* 忽略特定格式文件格式

  touch .gitignore  && vim .gitigonre 

  *.out *.py  # in .gitignore

    原有创建的格式用 git rm --cached <file_name> 忽略
    [常用工程的ignore文件](https://github.com/github/gitignore)

* 回滚操作

  git reset (--mixed --hard --soft ) HEAD~(可换)     #自己查询参数

  git commit --amend 轻微修改,不进行新的提交
