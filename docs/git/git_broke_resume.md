# 拉取大仓库失败的解决方法

## Fetch

备注：fetch无法断点续传

```
git init

git fetch git://…..git

*branch           HEAD                -> FETCH_HEAD
git checkout FETCH_HEAD


``` 

### 手动建立本地仓库，再拉取

```
  git init linux
  cd linux
  git remote add origin http://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git
  GIT_SMART_HTTP=0 git fetch -vv    # 有问题，github不支持http了
```  

## reop

安装:

下载

curl https://mirrors.tuna.tsinghua.edu.cn/git/git-repo -o repo
chmod +x repo

为了方便可以将其拷贝到你的PATH里。
更新

repo的运行过程中会尝试访问官方的git源更新自己，如果想使用tuna的镜像源进行更新，可以将如下内容复制到你的~/.bashrc里

export REPO_URL='https://mirrors.tuna.tsinghua.edu.cn/git/git-repo'

并重启终端模拟器。

[Git Repo 清华镜像使用]（https://mirror.tuna.tsinghua.edu.cn/help/git-repo/）

使用:

```
mkdir mydroid
cd mydroid
repo init -u git://android.git.kernel.org/platform/manifest.git
repo sync

```

备注：好像也不行

## gitee

可以先fork 到gitee再 clone到本地.