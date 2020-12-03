# 模块化


[Flutter包大小治理上的探索与实践](https://tech.meituan.com/2020/09/18/flutter-in-meituan.html)

[闲鱼Flutter混合工程持续集成的最佳实践](https://developer.aliyun.com/article/618599)

[京东技术中台的Flutter实践之路](https://zhuanlan.zhihu.com/p/96730987)

[Flutter动态化探索](https://www.jianshu.com/p/d193ce2c72c7)


# 插件

Flutter中的插件是这样定义的：
一种专用的Dart包，其中包含用Dart代码编写的API，以及针对Android（使用Java或Kotlin）和/或针对iOS（使用ObjC或Swift）平台的特定实现。
从这个定义来看，一个插件应该包括平台代码、dart代码。但是这两部分代码功能怎么关联？
官网写到：
“如果你想开发一个调用特定平台API的包，你需要开发一个插件包，插件包是Dart包的专用版本。 插件包包含针对Android（Java或Kotlin代码）或iOS（Objective-C或Swift代码）编写的特定于平台的实现（可以同时包含Android和Ios原生的代码）。 API使用platform channels连接到特定平台（Android或IOS）。”

## windows plugin

```
flutter create --platforms=windows --template=plugin win_maca_plugin
cd win_maca_plugin\example
flutter run -d windows -v 

or

flutter build windows

```

[Flutter Desktop Plugin](https://flatteredwithflutter.com/flutter-desktop-plugin/)

## 参考

[Flutter学习-插件开发](https://blog.csdn.net/skycnlr/article/details/86482169)

[Flutter插件汇总，总有一个用得着， 已收录：100+](https://www.jianshu.com/p/406672d4a0cd)

[awesome-flutter-plugins](https://github.com/jahnli/awesome-flutter-plugins)

[Flutter常用插件和对.yaml讲解](Flutter常用插件和对.yaml讲解)

[Flutter 插件的创建及使用](https://zhuanlan.zhihu.com/p/85849574)

[开发Flutter插件](https://book.flutterchina.club/chapter12/develop_plugin.html)

[flutter: SharedPreferences桌面插件](https://www.cnblogs.com/lindeer/p/11619811.html)

[使用平台通道编写平台特定的代码](https://flutterchina.club/platform-channels/)

# 参考

[Flutter 的编译模式](https://zhuanlan.zhihu.com/p/61903658)

[Flutter 与 Native 通信详解（上）：原理探究](https://www.jianshu.com/p/fafc6b3f3aa1)

[Flutter 与 Native 通信详解（下）：Platform Channel](https://www.jianshu.com/p/a467f02fb5ad)

[深入理解Flutter Platform Channel](https://www.jianshu.com/p/39575a90e820)

[揭秘Flutter Hot Reload（原理篇）](https://www.yuque.com/xytech/flutter/uhw8vw)

[重磅开源|AOP for Flutter开发利器——AspectD](https://www.yuque.com/xytech/flutter/aukvx8)

