# iOS中的Protocol

protocol类似java中的interface，主要是用来定义一套对象之间的通信规则。protocol也是我们设计时常用的一个东西，相对于直接继承的方式，protocol则偏向于组合模式。因为在设计对象的时候，如果基类东西很多，而不同的子类又不一定都需要基类的东西，或者在绝大部分需要的同时，又有特殊的要求，那这个时候就很混乱了。采用接口，可以将不同的功能归类为不同的接口，这样，子类需要什么功能，自己去实现这个接口，这样在保持继承性的同时，可以对功能进行扩展，而不影响其他类，也让子类保持自己的特有性。

### **protocol语法：**

```objective-c
@protocol protocolName

//method

//property

@end
```

和类的声明很相似,不仅可以声明方法，同样也可以声明property。如果某个类需要实现某个接口，则只需要在类的申明后面加上<>,在里面写上要实现的协议名字，多个协议以逗号隔开。

```objective-c
@interface Test : NSObject <delegate1, delegate2>

@end
```

### **protocol关键字：required，optional**

```objective-c
@protocol TestProtocol

@required
- (void)requiredMethod；
@optional
- (void)optionalMethod；
@end
```

protocol默认都是required的，一个类在实现协议的时候是必须要实现这些方法的。相对的，如果optional下面的方法，则表示类可以选择性的实现。判断这个类是否实现某个方法则只需调用`[self.delegate respondToSelector:@selector()]`

### **protocol的继承**

protocol和类一样，同样可以进行继承。

```objective-c
@protocol Test1Delegate
@end

@protocol Test2Delegate <Test1Delegate>
@end;
```

这个时候，如果类实现了Test2Delegate这个协议，那么也必须实现Test1Delegate里面的方法。 我们自己写的protocol的时候，一般Xcode都默认帮我们继承了NSObject这个协议。如果你不继承的话也没啥大的影响，因为我们的对象都是继承自NSObject，而NSObject也实现了`NSObject`这个协议。所以，当我们需要调用NSObject协议里面的方法的时候，也不会出错。不过苹果还是推荐继承NSObject这个协议。

### **protocol隐藏类的类型**

在我们iOS开发中也会出现这种形式，比如iOS7的导航栏动画，苹果只是需要你返回一个实现了`UIViewControllerAnimatedTransitioning`这个协议的对象就行了。

还有一个可能在和第三方sdk打交道的时候见得比较多。在别人实现的框架里面，有的时候，不希望把类的类型和里面方法暴露给你，而你也不太可能直接创建这个对象。这个时候就可以采用protocol这个方式，让调用者无需知道类的类型，一样可以完成自己想要的操作。

```objective-c
id <Test1Delegate>obj = [XXXX  createObj];
```

调用者只需要通过[XXXX createObj]这个方法，获取一个实现Test1Delegate而不知道类型的实例。在需要的地方，这个obj可以直接调用协议里面的方法，因为，这个对象都已经实现了。

**protocol 差不多就这么多内容，比较简单。**



[BackHome](http://ablexie.github.io/)