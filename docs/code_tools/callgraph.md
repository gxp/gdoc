# calltree

在linux下能够将代码中函数调用关系生成调用树，并可以选择生成dot语言文件，通过dot工具生成调用关系图

calltree基本命令：
calltree -gb -np –m *.c

备注：
calltree 比较老，ubuntu上都没有安装包了。


# call-graph

Library to generate call graph for cpp functions (for emacs)

https://github.com/beacoder/call-graph

Installation

Clone the repo, then in your Emacs init file:

(add-to-list 'load-path "/path/to/repo")
(require 'call-graph)
(call-graph) ;; to launch it

Or install from melpa.

较新、更新慢

# cflow

The cflow utility analyzes a collection of source files written in C programming language and outputs a graph charting dependencies between various functions.

调用关系显示：

cflow whoami.c

被调用关系显示：

cflow --reverse whoami.c

https://www.gnu.org/software/cflow/manual/cflow.html


# 参考

https://www.xuebuyuan.com/3234973.html
