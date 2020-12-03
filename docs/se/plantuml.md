# 对齐框图

使用dot 节点的width属性

```

@startuml

digraph  g {
     label = " image=http://plantuml.com/logo3.png";
    compound=true;
    graph [width=7.65];
    rankdir=TB

    subgraph cluster_top {
        graph [color=black, label="Top", rank=same];
         
        nodeAI2 [style=invisible,fixedsize=true,width=1.65]
        nodeA; nodeB; nodeC
       
      cluster_top_DUMMY [shape=line,height=0.01, width=17,fontsize=1.0  ]
      nodeB -> cluster_top_DUMMY [style=invis]
    }

    subgraph cluster_service {
         cluster_bottom_DUMMY [shape=line,height=0.01, width=17,style=invis]

         subgraph cluster_service {
            graph [color=black, label="Bottom", rank=min];
            node1; node2; node3; node4; node5; extra_long_node
         }
      cluster_bottom_DUMMY -> node4 [style=invis]
    }
    
    cluster_top_DUMMY -> cluster_bottom_DUMMY [style=invis]

}
@enduml

```

是否也可用dot 表中，播放图片的方式?:

```
    imgnode1[image="E://temp//message_collecting.png", lable=""];
    imgnode2[style=box,image="E:\temp\message_collecting.png", lable=""];

```

使用表 加 img 嵌入图的方式：

```

@startuml
start
:Here is the result
|= |= table |= header |
| <img:http://plantuml.com/logo3.png> | <img:http://plantuml.com/logo3.png> | <img:http://plantuml.com/logo3.png> |
|<#FF8080> <img:http://plantuml.com/logo3.png> |<#80FF80> <img:http://plantuml.com/logo3.png> |<#8080FF> <img:http://plantuml.com/logo3.png> |
<#yellow>| <img:http://plantuml.com/logo3.png> | <img:http://plantuml.com/logo3.png> | <img:http://plantuml.com/logo3.png> |;
@enduml

```


# 布局

```
@startuml

class Bar1
class Bar2
together {
class Together1
class Together2
class Together3
}

Together1 - Together2
Together2 - Together3
Together2 -[hidden]--> Bar1
Bar1 -[hidden]> Bar2
@enduml

```

注意: -[hidden]-  -[hidden] 可以控制布局方向 

# 图

```
@startuml {myimage.png} "Image Caption" width=5cm
package "Images" {
    rectangle "<img:https://raw.githubusercontent.com/Roemer/plantuml-office/master/office2014/Servers/database_server.png>\r DB" as db2
    rectangle "<img:https://raw.githubusercontent.com/Roemer/plantuml-office/master/office2014/Servers/application_server.png>\r App-Server" as app2
    rectangle "<img:https://raw.githubusercontent.com/Roemer/plantuml-office/master/office2014/Concepts/firewall_orange.png>\r Firewall" as fw2
    rectangle "<img:https://raw.githubusercontent.com/Roemer/plantuml-office/master/office2014/Clouds/cloud_disaster_red.png>\r Cloud" as cloud2
    db2 <-> app2
    app2 <--> fw2
    fw2 <.left.> cloud2
}

rectangle "<img:http://plantuml.com/logo3.png>\r" as logo
rectangle "<img:http://plantuml.com/logo3.png>\r" as logo1
rectangle "<img:http://plantuml.com/logo3.png>\r" as logo2

logo -[hidden]- logo1
logo1 -- logo2

@enduml


# 同一文件生成多个图文件

参考手册 3.27 拆分大文件 作用是把同一个文件拆分成多个图保存.
[multiple diagrams in source file](https://forum.plantuml.net/5822/page-hpages-x-vpages-and-multiple-diagrams-in-source-file)