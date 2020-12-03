# linux tar、xargs对目录下多个文件分别批量打包压缩

```
ls | xargs -i  tar zcvf {}.tar.gz {}
```

[linux tar、xargs对目录下多个文件分别批量打包压缩(原)](https://www.anbob.com/archives/905.html)


# find,xargs,tar有选择打包

```
find ./ -mtime 83 -exec sz {} \;

find . -type f -exec ls -l {} \;

\;表达 -exec 的结束。

==========================

[1]

find / -name "*.sh"|xargs tar -rf sh.tgz
[2]
find / -name "*.sh" -print > list
tar -T list -cvjf sh.tar.bz2

[3]

find . -name '*.sh' | xargs tar cvjf sh.tar.bz2

find . -name '*.sh' -print0 | xargs -0 tar cvjf sh.tar.bz2
```

[find,xargs,tar有选择打包](https://blog.csdn.net/weixin_34356138/article/details/86387221?utm_medium=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase)
