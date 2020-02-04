# 拉取大仓库失败的解决方法

## Fetch

```
git init

git fetch git://…..git

*branch           HEAD                -> FETCH_HEAD
git checkout FETCH_HEAD


``` 

## 手动建立本地仓库，再拉取

```
  git init linux
  cd linux
  git remote add origin http://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
  GIT_SMART_HTTP=0 git fetch -vv 
```  