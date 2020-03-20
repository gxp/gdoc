# PlantUML

## 标准库

It is also possible to use the command line java -jar plantuml.jar -stdlib to display the same list.

[æ ‡å‡†åº“](https://plantuml.com/zh/stdlib)

@startuml
stdlib
@enduml

@startuml
!include <tupadr3/common>

!include <office/servers/database_server>
!include <office/servers/application_server>
!include <office/Concepts/firewall_orange>
!include <office/Clouds/cloud_disaster_red>

' Used to center the label under the images
skinparam defaultTextAlignment center

title Extended Office Icons Example

package "Use sprite directly" {
	[Some <$cloud_disaster_red> object]
}

package "Different macro usages" {
	OFF_CLOUD_DISASTER_RED(cloud1)
	OFF_CLOUD_DISASTER_RED(cloud2,Default with text)
	OFF_CLOUD_DISASTER_RED(cloud3,Other shape,Folder)
	OFF_CLOUD_DISASTER_RED(cloud4,Even another shape,Database)
	OFF_CLOUD_DISASTER_RED(cloud5,Colored,Rectangle, red)
	OFF_CLOUD_DISASTER_RED(cloud6,Colored background) #red
}
@enduml

#  C4 Model样式

C4 Model 在我眼里更像是一个标准，一个方法论。让架构师、程序员、业务人员在讨论IT系统架构时候统一维度，统一标准，更方便的理解和沟通IT系统中的真实问题。强烈推荐！！！

C4 模型由一系列分层的软件架构图组成，这些架构图用于描述上下文（Context）、容器(Container)、组件(Component)和代码(Code)。C4 图的层次结构提供了不同的抽象级别，每种抽象级别都与不同的受众有关

[自定义PlantUML和C4 Model样式](https://www.cnblogs.com/xuanye/p/new-style-4-plantuml-and-c4model.html )

[使用VSCode+PlantUML+C4-Model快速画架构图](https://www.jianshu.com/p/0d1917cd04e3)

[C4-PlantUML](https://github.com/RicardoNiepel/C4-PlantUML)

# Text to UML tools  Fastest way to create your models

https://modeling-languages.com/text-uml-tools-complete-list/

A textual UML tool supports the use of textual notations/languages to describe UML models and automatically renders the corresponding graphical UML diagram from that textual description (a few tools also target other kinds modeling languages, like ER or BPMN, and we mention them here as well, but they are the exception).

Most promising UML textual modeling tools
    PlantUML
    yUML
    Nomnoml
    TextUML
    UML Graph
    Umple
    ZenUML
    Chart Mage
    USE
    Kroki
Other alternatives (only for UML sequence diagrams)
    WebSequencediagrams
    SequenceDiagram.org
    BlockDiag
    Swimlanes.io
    Sequins
LaTeX to UML
Beyond UML diagrams
Dead modeling tools
