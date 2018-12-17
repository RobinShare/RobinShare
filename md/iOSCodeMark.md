---
layout: default
---

# iOS开发

```markdown
真正的编程并不是编写代码，编写代码只是肤浅的编程。
编程的真谛就是制定本意，其可以是一个人的自我管理，
一个部门的内部管理，一个企业的流程管理，
一个国家的顶层设计，一个世界的运作约束。
```



[BookTime](iOSCodeMark/Book.md)



[计算机术语传送门](iOSCodeMark/计算机术语传送门.md)



[HowToGetYourMacBook'sJenkinsAndTomcat](iOSCodeMark/Jenkins And Tomcat Setting On Your MacBook.md)



------



[ReactiveCocoa入门到实战篇之第二周](iOSCodeMark/第二周PDF.pdf)

[ReactiveCocoa入门到实战篇之第三周](iOSCodeMark/第三周PDF.pdf)

[ReactiveCocoa入门到实战篇之第四周](iOSCodeMark/第四周PDF.pdf)

[ReactiveCocoa入门到实战篇之第五周](iOSCodeMark/第五周PDF.pdf)



------



### [iOS在Xcode8用MagicalRecord实现本地数据库](iOSCodeMark/iOS在Xcode8用MagicalRecord实现本地数据库.md)

本篇记录的是关于在升级后的Xcode8以后，如何使用第三方库MagicalRecord实现本地数据库的初级篇。具体实现步骤如下：



### [如何在Xcode8搭建Python环境](iOSCodeMark/Xcode8搭建Python环境.md)

很多人苦恼于没有好的Python编译环境，其实Xcode已经为我们提供了这个条件。

第一步，打开Xcode创建项目，Cross-platform>>External Build System>>Next：



### [iOS的一对多回调GCDMulticastDelegate(多播委托)](iOSCodeMark/iOS的GCDMulticastDelegate多播委托.md)

iOS中通常的delegate模式只能有一个被委托的对象，这样当需要有多个被委托的对象时，实现起来就略为麻烦，在开源库XMPPFramework中提供了一个[GCDMulticastDelegate](https://github.com/euanlau/GCDMulticastDelegate)类，这个类实现的技术基础是OC的消息动态解析与转发，通过这些机制进行封装，很巧妙实现了一对多的delegate机制，避免了有这种需求的时候，都需要自己去维护这种逻辑的问题。代码不长，阅读难度也不是很大。调用的时候，核心是methodSignatureForSelector: -> forwardInvocation: -> doesNotRecognizeSelector逻辑的重写，关于这部分，可以参考我之前关于OC消息动态解析与转发的一篇博客，[iOS中的Rumtime](http://ablexie.github.io/md/iOSCodeMark/iOS中的Runtime.html)。这里需要注意的一点是，[GCDMulticastDelegate](https://github.com/euanlau/GCDMulticastDelegate)不能使用respondToSelector进行检测，但是其内部已经对不能实现调用的方法进行了处理，不会引发Exception。



### [Git使用](iOSCodeMark/Git使用.md)

Git团队协作实战



------



### [SSL/TLS协议运行机制的概述](iOSCodeMark/SSL和TLS协议运行机制的概述.md)

互联网的通信安全，建立在SSL/TLS协议之上。本文简要介绍SSL/TLS协议的运行机制。文章的重点是设计思想和运行过程，不涉及具体的实习细节。如果想了解这方面的内容，请参阅[RFC文档](http://tools.ietf.org/html/rfc5246)。



### [iOS安全系列之HTTPS](iOSCodeMark/iOS安全系列之HTTPS.md)

HTTPS从最终的数据解析的角度，与HTTP没有任何的区别，HTTPS就是将HTTP协议数据包放到SSL/TSL层加密后，在TCP/IP层组成IP数据报去传输，以此保证传输数据的安全；而对于接收端，在SSL/TSL将接收的数据包解密之后，将数据传给HTTP协议层，就是普通的HTTP数据。HTTP和SSL/TSL都处于OSI模型的应用层。



------



### [iOS线程使用Swift 3版](iOSCodeMark/iOS线程使用Swift 3版.md)

在 iOS 当中，苹果提供了两种方式进行多任务编程：*Grand Central Dispatch (GCD)* 和 *NSOperationQueue*。当我们需要把任务分配到不同的线程中，或者是非主队列的其它队列中时，这两种方法都可以很好地满足需求。Swift 3 当中 GCD【*Grand Central Dispatch*】 是最基础也是最重要的知识。



### [iOS线程使用Objective-C版](iOSCodeMark/iOS线程使用Objective-C版.md)

为了避免界面在处理耗时的操作时卡死，比如读取网络数据，IO,数据库读写等，我们会在另外一个线程中处理这些操作，然后通知主线程更新界面。用GCD实现这个流程的操作比前面介绍的`NSThread` 、 `NSOperation`的方法都要简单。



------



### [GATTProfile简介](iOSCodeMark/GATTProfile简介.md)

网上关于讲解 BLE 的内容比较少，看到这篇文章写的非常详细 [Introduction to Bluetooth Low Energy](https://learn.adafruit.com/introduction-to-bluetooth-low-energy?view=all)，作为 BLE 的入门时介绍是非常合适的。本文主要翻译了一下这篇文章。现在低功耗蓝牙（BLE）连接都是建立在 **GATT** (Generic Attribute Profile) 协议之上。GATT 是一个在蓝牙连接之上的发送和接收很短的数据段的通用规范，这些很短的数据段被称为属性（Attribute）。详细介绍 GATT 之前，需要了解 **GAP**（Generic Access Profile），它在用来控制设备连接和广播。GAP 使你的设备被其他设备可见，并决定了你的设备是否可以或者怎样与合同设备进行交互。例如 Beacon 设备就只是向外广播，不支持连接，小米手环就等设备就可以与中心设备连接。



### [iOS蓝牙的开发专题](iOSCodeMark/iOS蓝牙的开发专题.md)

-蓝牙常见名称和缩写
-蓝牙基础知识
-蓝牙和版本的使用限制



### [iOS蓝牙开发(1)app连接外设的代码实现](iOSCodeMark/iOS蓝牙开发首篇.md)

上一篇文章介绍了蓝牙的技术知识，这里我们具体说明一下中心模式的应用场景。主设备（手机去扫描连接外设，发现外设服务和属性，操作服务和属性的应用。一般来说，外设（蓝牙设备，比如智能手环之类的东西）， 会由硬件工程师开发好，并定义好设备提供的服务，每个服务对于的特征，每个特征的属性（只读，只写，通知等等），本文例子的业务场景，就是用一手机app去读写蓝牙设备。

### **central模式的流程**

```markdown
-建立中心角色
-扫描外设(discover)
-扫描外设中的服务和特征(discover)
		-获取外设的services
		-获取外设的Characteristics,获取Characteris的值,获取Characteristics的Descriptor和Descritor的值
-与外设做数据交互(explore and interact)
-订阅Characteristic的通知
-断开连接(disconnect)
```



### [iOS蓝牙开发(2)app作为外设被连接的实现](iOSCodeMark/iOS蓝牙开发中篇.md)

### **peripheral模式的流程**

```markdown
1. 打开peripheralManager，设置peripheralManager的委托
2. 创建characteristics，characteristics的description 创建service，把characteristics添加到service中，再把service添加到peripheralManager中
3. 开启广播advertising
4. 对central的操作进行响应
    - 4.1 读characteristics请求
    - 4.2 写characteristics请求
    - 4.4 订阅和取消订阅characteristics
```



### [iOS蓝牙开发(3)BabyBluetooth蓝牙库介绍](iOSCodeMark/iOS蓝牙开发末篇.md)

[**BabyBluetooth**](https://github.com/coolnameismy/BabyBluetooth) 是一个最简单易用的蓝牙库，基于CoreBluetooth的封装，并兼容ios和mac osx。

### 特色：

-  基于原生CoreBluetooth框架封装的轻量级的开源库，可以帮你更简单地使用CoreBluetooth API。
-  CoreBluetooth所有方法都是通过委托完成，代码冗余且顺序凌乱。BabyBluetooth使用block方法，可以重新按照功能和顺序组织代码，并提供许多方法减少蓝牙开发过程中的代码量。
-  链式方法体，代码更简洁、优雅。
-  通过channel切换区分委托调用，并方便切换。



------



### [不直接用NSLog](iOSCodeMark/不直接用NSLog.md)

摘要: 公司中不直接使用NSLog,而是利用宏定义自己的打印函数,将该打印函数写在项目的.pch文件中.调试的时候往往用到好多打印,但发布的时候确不需要.(以下是在公司中的一些处理方法)



### [常用的正则表达式](iOSCodeMark/常用的正则表达式.md)

正则表达式，一个十分古老而又强大的文本处理工具，仅仅用一段非常简短的表达式语句，便能够快速实现一个非常复杂的业务逻辑。熟练地掌握正则表达式的话，能够使你的开发效率得到极大的提升。



### [Cocoa中的位与位运算](iOSCodeMark/Cocoa中的位与位运算.md)

介绍.位操作是程序设计中对位模式或二进制数的一元和二元操作. 在许多古老的微处理器上, 位运算比加减运算略快, 通常位运算比乘除法运算要快很多. 在现代架构中, 情况并非如此:位运算的运算速度通常与加法运算相同(仍然快于乘法运算).（摘自wikipedia）OC作为c的扩展和超集，位运算自然使用的是c的操作符。c提供了6个位操作符，$，|，^，~，<<，>>。本文不打算做位运算的基础教学，只介绍一些开发中能用到的场景。



### [iOS与网页JS交互](iOSCodeMark/iOS与网页JS交互.md)

随着移动APP的快速迭代开发趋势，越来越多的APP中嵌入了html网页，但在一些大中型APP中，尤其是电商类APP，html页面已经不仅仅满足展示功能，这时html要求能与原生语言进行交互、相互传值。比如携程APP中一个热门景点的网页中，点击某个景点，可以跳转到原生中的该景点详情页控制器。

为此，我整理了三种最常用最便捷有效的OC与JS交互的方式，供大家学习交流。



### [iOS开发UI篇之使用Quartz2D绘制椭圆进度条](iOSCodeMark/iOS开发UI篇之使用Quartz2D绘制椭圆进度条.md)

-  Quartz 2D能完成的工作
-  -  绘制图形 : 线条\三角形\矩形\圆\弧等
   -  绘制文字
   -  绘制\生成图片(图像)
   -  读取\生成PDF
   -  截图\裁剪图片
   -  自定义UI控件

在iOS开发中的价值:

-  绘制一些系统UIKit框架中不好展示的内容，例如饼图
-  自定义一些控件
-  不添加UI控件的情况下，使UI内容更丰富
-  ……

------



### [iOS视频开发知识](iOSCodeMark/iOS视频开发知识.md)

手机比PC的优势除了便携外，我认为最重要的就是可以快速方便的创作多媒体作品。照片分享，语音输入，视频录制，地理位置。一个成功的手机APP从产品形态上都有这其中的一项或多项，比如instagram，微信。如果把Web2.0的交互体验照搬到手机上就是死路一条。 当智能手机遇上视频就像潘金莲遇上西门庆，各取所需一拍即合，想不发生点事情都难。他们的结晶就是微视频。微视频可以说把手机的视频录制和碎片时间两个特点发挥到了极致，视频相关的APP现在无温不火的原因我认为跟坑爹的运营商有关。虽然现在移动网络流量小速度慢，但是不妨碍我们先把技术积累做起来。



### [iOS开发自定义framework](iOSCodeMark/iOS开发自定义framework.md)

Framework是资源的集合，将静态库（iOS8以后可以是动态库）和其头文件包含到一个结构中，让Xcode可以方便地把它纳入到你的项目中。
分为真机—Debug（调试）版本、真机—Release（发布）版本、模拟器—Debug版本、模拟器—Release版本；开发中一般都打包Release（发布）版本，将真机和模拟器版本合并，提供外界。
在项目开发的过程中，例如两个公司之间业务交流，不可能把源代码都发送给另一个公司，这时候将私密内容打包成framework，别人只能调用接口，而不能知道其中实现的细节。



### [KVC(Key-Value-Coding) 几行代码打造一个万能容器对象](iOSCodeMark/KVC打造一个万能容器对象.md)

KVC(Key-Value-Coding)意思是键值编码。在iOS中，提供了一种方法通过使用属性的名称（也就是Key）来间接访问对象的属性方法,以下用KVC实现一个万能容器对象的方法。



### [将项目中的代码逐步转换为ARC，解决循环引用的问题](iOSCodeMark/解决循环引用的问题.md)

准备将项目中的代码逐步转换为ARC，存在MRC与ARC并存的情况，想用一个通用的办法来解决循环引用的问题，找到了这份代码，太好了，一劳永逸。使用方法见注释： 



### [iOS 中的nullable和nonnull](iOSCodeMark/iOS中的nullable和nonnull.md)

我们都知道在swift中，可以使用!和?来表示一个对象是optional的还是non-optional，如view?和view!。而在Objective-C中则没有这一区分，view即可表示这个对象是optional，也可表示是non-optioanl。这样就会造成一个问题：在Swift与Objective-C混编时，Swift编译器并不知道一个Objective-C对象到底是optional还是non-optional，因此这种情况下编译器会隐式地将Objective-C的对象当成是non-optional。

为了解决这个问题，苹果在Xcode 6.3引入了一个Objective-C的新特性：nullability annotations。这一新特性的核心是两个新的类型注释：**__nullable**和**__nonnull**。从字面上我们可以猜到，**__nullable**表示对象可以是NULL或nil，而**__nonnull**表示对象不应该为空。当我们不遵循这一规则时，编译器就会给出警告。



------



### [iOS 文件的操作](iOSCodeMark/iOS 文件的操作.md)

由于沙盒机制，应用只能访问自己应用目录下的文件。

**iOS**不像**Android**，没有SD卡概念，不能直接访问图像、视频等内容。iOS应用产生的内容，如图像、文件、缓存内容等都必须存储在自己的沙盒内。默认情况下，每个沙盒含有3个文件夹：Documents, Library 和 tmp。Library包含Caches、Preferences目录。



### [iOS中的Protocol](iOSCodeMark/iOS中的Protocol.md)

protocol类似java中的interface，主要是用来定义一套对象之间的通信规则。protocol也是我们设计时常用的一个东西，相对于直接继承的方式，protocol则偏向于组合模式。因为在设计对象的时候，如果基类东西很多，而不同的子类又不一定都需要基类的东西，或者在绝大部分需要的同时，又有特殊的要求，那这个时候就很混乱了。采用接口，可以将不同的功能归类为不同的接口，这样，子类需要什么功能，自己去实现这个接口，这样在保持继承性的同时，可以对功能进行扩展，而不影响其他类，也让子类保持自己的特有性。



### [iOS之代码块block攻关](iOSCodeMark/iOS之代码块block攻关.md)

代码块Block是苹果在iOS4开始引入的对C语言的扩展,用来实现匿名函数的特性,Block是一种特殊的数据类型,其可以正常定义变量、作为参数、作为返回值,特殊地,Block还可以保存一段代码,在需要的时候调用,目前Block已经广泛应用于iOS开发中,常用于GCD、动画、排序及各类回调。



### [iOS中的Runtime](iOSCodeMark/iOS中的Runtime.md)

看完本篇之后你将获得：

-  了解什么是runtime
-  知道可以利用runtime做到哪些事情
-  掌握用runtime开发的常用方法

Runtime是开源的，任何时候你都可以从http://opensource.apple.com获取。事实上查看 Objective-C 源码是我理解它是如何工作的第一种方式，在某些问题上要比读苹果的文档要好。



------



### [ObjectIve-C单例模式的正确使用(写法)](iOSCodeMark/单例模式的正确使用.md)

单例模式在iOS开发中可能算是最常用的模式之一了，但是由于oc本身的语言特性，想要写一个正确的单例模式相对来说比较麻烦，这里我就抛砖引玉来聊一聊iOS中单例模式的设计思路。

单例顾名思义就是说一个类的实例只能有一个，在java、C++这类语言中，可以通过将构造函数私有化来避免对象的重复创建，但是objective-c却不能够这样做，我们需要通过其他机制来达到这个目的。一般情况下，可能我们写的单例模式是这样的：



### [ViewController的生命周期](iOSCodeMark/ViewController的生命周期.md)

init、viewDidLoad、viewWillAppear、viewDidAppear、viewWillDisappear、viewDidDisappear的执行顺序





[BackHome](http://robinshare.github.io/)

