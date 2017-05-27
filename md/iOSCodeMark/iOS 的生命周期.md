# iOS 的生命周期

init、viewDidLoad、viewWillAppear、viewDidAppear、viewWillDisappear、viewDidDisappear的执行顺序：

 从程序的log来看：

```objective-c
2012-10-19 15:51:44.811inHyron[483:b903] init

2012-10-19 15:51:54.081inHyron[483:b903] viewDidLoad

2012-10-19 15:51:54.082inHyron[483:b903] viewWillAppear

2012-10-19 15:51:54.084 inHyron[483:b903] viewDidAppear

```



插曲：

应用沙盒，归档，解档，偏好设置，plist存储，NSData，自定义对象归档解档  这些都能存  只是哪种比较方便 /性能好



[BackHome](http://ablexie.github.io/)