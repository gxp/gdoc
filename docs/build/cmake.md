# uninstall

cmake不提供uninstall支持，但可从文件install_manifest.txt中查看安装了哪些文件，可使用如下命令删除安装：
```
cat ./install_manifest.txt | xargs sudo rm
```
