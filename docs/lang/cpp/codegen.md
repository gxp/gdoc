# 测试

## docker 编译SakuraAutoCoder or cppast

docker run -name myllvm ubuntu -it -v /data1/gxp/opensources:/opt/opensources

apt update

apt install llvm clang libclang1 clang-tools cmake make libboost-all-dev git libclang-dev libc++-dev libc++abi-dev libstdc++-10-dev

export VCPKG_ROOT=/opt/opensources/pkg/vcpkg

cd SakuraAutoCoder
mkdir build_dir
cd build_dir
cmake ..     //ok
make   

测试要用clang10 用系统自带的libboost-all-dev 链接时有问题。
用vcpkg 安装boost测试
./vcpkg install boost-filesystem boost-iostreams boost-serialization

未成功，应该是libstdc++ 与libc++库冲突. vcpkg 使用libstdc++, SakuraAutoCoder使用libc++ ?


cd cppast
mkdir build_dir
cd build_dir
cmake ..     //ok
make  

注意：
  出错 test 相关 build_dir/test/catch.hpp 文件是否下载成功(https://raw.githubusercontent.com/catchorg/Catch2/master/single_include/catch2/catch.hpp)
  可以 git clone https://github.com/catchorg/Catch2， 然后把文件复制过去。注意是tag v2.x
  or
  wget https://github.com/catchorg/Catch2/raw/v2.x/single_include/catch2/catch.hpp

  注释掉CMakefiles.txt 中test相关开关，编译成功

  测试 tools/cppast  

  # 参考

  [用LLVM开发新语言](https://llvm-tutorial-cn.readthedocs.io/en/latest/index.html)

  [使用llvm实现一门语言 —— cava](https://developer.aliyun.com/article/569216)

  [flex与bison](https://blog.csdn.net/CrazyHeroZK/article/details/87359818)



