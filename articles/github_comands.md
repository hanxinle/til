# GitHub 命令行
### 本地repo

* 设置姓名和邮箱

   ``` git config --global user.name "xxxx"```

   ```git config --global user.email "xxxx@yyy.zzz"```

* 创建并初始化本地空仓库

  ``` git init <repo_name>```

* 查看提交的状态

  ```git status```

* 暂存区中添加更改

  ```git add <file_name>```

* 记录一行提交信息

  ``` git commit -m "commit info"```

* 提交记录
 
  ``` git log```

* 忽略特定格式文件格式

   ```touch .gitignore  && vim .gitigonre ```

   ``` *.out *.py  # in .gitignore```

    原有创建的格式用 git rm --cached <file_name> 忽略
    [常用工程的ignore文件](https://github.com/github/gitignore)

* 回滚操作

  ``` git reset (--mixed --hard --soft ) HEAD~(可换)     #自己查询参数```

  ``` git commit --amend 轻微修改,不进行新的提交```
  
### 远程repo
  
* 查看分支
  
    ```git branch``` 
  
* 创建分支
  
     ```git branch <branch_name```
  
* 切换到分支
  
    ```git checkout <branch_name>```
  
* 创建并且切换
  
     ```git checkout -b <branch_name>```
  
* 分支合并(位于master)

  ```git merge <sub_branch_name>```
  
  同步后可以删除这个子分支
  
  ```git branch -d <sub_branch_name>```
  
* 分支同步

  ```git push origin <loacl_branch_name>```   将本地分支同步到服务器

* 分支删除与重命名
   
  ```git brach -D/-d ``` #删除 see git -h
  
  远端分支重命名(创建本地分支-->同步到远端-->删除远端同名分支-->原本地分支重命名-->推送到远端)
  
  ```git checkout -b <local_branch>```
  
  ```git push origin <local_branch>```
  
  ```git push --delete origin <local_name>```
  
  ```git commit -m <local_name> <new_branch_name>```
  
  ```git push origin <new_branch_name>```
  

* tag 管理

  网页端release中管理,和commit的哈希值相关.