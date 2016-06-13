# GBUI
实现一套基于OpenGL[es]/DirectX渲染方式的UI引擎。


#如何实现界面引擎
一套完整的界面引擎应该包括以下几个子系统：
##窗口系统
  桌面操作系统(windows, linux)称之为control；
  嵌入式操作系统(android, iOS)称之为view。UI由各种类型和功能的control/view对象组成，并由统一的tree方式管理，z-order决定其渲染顺序。
##事件系统
  人机交互的复杂性和实时性，对于消息事件的响应非常敏感。需要异步且优先级区分。
  可以参考QT的signal/slot，WTL的消息映射，boost的signal。
##布局系统
  为了做各种自适应界面，需要有layout来管理界面布局。其中有一个难点是为了支撑频繁的界面需求更改，减少开发维护成本，做到界面与业务逻辑分离，需要做界面配置解析工具一般为xml形式，甚至是支持更高级语言比如lua,qml,html+css+js方式来轻松定义界面。同时需要开发对应的所见即所得的UI编辑器。
##渲染系统
  可以基于GDI/GTK/SDL等一些现成的图形渲染引擎，结合传统的Retained Mode GUI开发风格，即每一个control/view都是界面上的一个对象，由上面的窗口系统统一tree方式调用响应的onDraw回调进行绘制；另外一种方式Immediate Mode GUI基于OpenGL[es]/DirectX方式直接在分层渲染但没有每一个control/view在底层对应一个对象的概念，减少对象管理负责度，提高渲染效率。一般游戏系统通常采用后者方式比较多。
##动画系统
  为了实现比较炫酷的特效，需要开发动画系统，可参考iOS和android的animation模块SDK。

