# 查看文件信息

file

## Linux查看文件依赖库

ldd filename

cat /proc/298(pid)/maps

xxx-linux-objdump -x "filename" | grep "NEEDED"

xxx-linux-readelf -a "filename" | grep "Shared"

[Linux查看可执行文件依赖库](https://blog.csdn.net/JoshYueby/article/details/105528682)