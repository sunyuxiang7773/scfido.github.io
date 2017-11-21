---
   layout: default
   title: 如何修改Git commit的信息
   tags: Git
---

# {{ page.title }}
{{ page.date | date: "%Y-%m-%d" }}

原文地址： http://xiguada.org/change-git-commit-message
 
Git commit信息push后，如何修改，amend可以修改最后一次commit信息，但对于历史提交信息，需要使用rebase命令。
 
1. 比如要修改的commit是倒数第三条，使用下述命令：
```
git rebase -i HEAD~3
```

![](/assets/misc/如何修改Gitcommit的信息/img/2017-11-21-11-14-56.png)


2. 把`pick`改为`edit`

![](/assets/misc/img/如何修改Gitcommit的信息/img/2017-11-21-11-15-14.png)
 


3. 然后 `:wq`出现如下信息：

![](/assets/misc/img/如何修改Gitcommit的信息/img/2017-11-21-11-15-26.png)
 


4. 执行 
```
git commit --amend
```
修改commit信息

 ![](/assets/misc/img/如何修改Gitcommit的信息/img/2017-11-21-11-15-36.png)


5. 退出保存 `:wq`
6. 执行 
```
git rebase --continue
```
7. 推送到服务端
```
git push -f
``` 
