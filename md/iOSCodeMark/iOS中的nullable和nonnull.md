# iOS 中的nullable和nonnull

我们都知道在swift中，可以使用!和?来表示一个对象是optional的还是non-optional，如view?和view!。而在Objective-C中则没有这一区分，view即可表示这个对象是optional，也可表示是non-optioanl。这样就会造成一个问题：在Swift与Objective-C混编时，Swift编译器并不知道一个Objective-C对象到底是optional还是non-optional，因此这种情况下编译器会隐式地将Objective-C的对象当成是non-optional。

为了解决这个问题，苹果在Xcode 6.3引入了一个Objective-C的新特性：nullability annotations。这一新特性的核心是两个新的类型注释：**__nullable**和**__nonnull**。从字面上我们可以猜到，**__nullable**表示对象可以是NULL或nil，而**__nonnull**表示对象不应该为空。当我们不遵循这一规则时，编译器就会给出警告。

我们来看看以下的实例，

```objective-c
@interface TestNullabilityClass ()
  
@property (nonatomic, copy) NSArray * items;
- (id)itemWithName:(NSString * __nonnull)name;

@end


@implementation TestNullabilityClass
  
...
  
- (void)testNullability {
    [self itemWithName:nil]; // 编译器警告：Null passed to a callee that requires a non-null argument
}

- (id)itemWithName:(NSString * __nonnull)name {
    return nil;
}
@end
```

不过这只是一个警告，程序还是能编译通过并运行。

事实上，在任何可以使用const关键字的地方都可以使用__nullable和__nonnull，不过这两个关键字仅限于使用在指针类型上。而在方法的声明中，我们还可以使用不带下划线的nullable和nonnull，如下所示：

```objective-c
- (nullable id)itemWithName:(NSString * nonnull)name
```

在属性声明中，也增加了两个相应的特性，因此上例中的items属性可以如下声明：

```objective-c
@property (nonatomic, copy, nonnull) NSArray * items;
```

当然也可以用以下这种方式：

```objective-c
@property (nonatomic, copy) NSArray * __nonnull items;
```

推荐使用nonnull这种方式，这样可以让属性声明看起来更清晰。

**Nonnull区域设置(Audited Regions)**

如果需要每个属性或每个方法都去指定nonnull和nullable，是一件非常繁琐的事。苹果为了减轻我们的工作量，专门提供了两个宏：NS_ASSUME_NONNULL_BEGIN和NS_ASSUME_NONNULL_END。在这两个宏之间的代码，所有简单指针对象都被假定为nonnull，因此我们只需要去指定那些nullable的指针。如下代码所示：

```objective-c
NS_ASSUME_NONNULL_BEGIN

@interface TestNullabilityClass ()

@property (nonatomic, copy) NSArray * items;
- (id)itemWithName:(nullable NSString *)name;

@end

NS_ASSUME_NONNULL_END
```

在上面的代码中，items属性默认是nonnull的，itemWithName:方法的返回值也是nonnull，而参数是指定为nullable的。

不过，为了安全起见，苹果还制定了几条规则：

-  typedef定义的类型的nullability特性通常依赖于上下文，即使是在Audited Regions中，也不能假定它为nonnull。
-  复杂的指针类型(如id *)必须显示去指定是nonnull还是nullable。例如，指定一个指向nullable对象的nonnull指针，可以使用”__nullable id * __nonnull”。
-  我们经常使用的NSError **通常是被假定为一个指向nullable NSError对象的nullable指针。

**兼容性**

因为Nullability Annotations是Xcode 6.3新加入的，所以我们需要考虑之前的老代码。实际上，苹果已以帮我们处理好了这种兼容问题，我们可以安全地使用它们：

-  老代码仍然能正常工作，    即使对nonnull对象使用了nil也没有问题。
-  老代码在需要和swift混编时，在新的swift编译器下会给出一个警告。
-  nonnull不会影响性能。事实上，我们仍然可以在运行时去判断我们的对象是否为nil。

事实上，我们可以将nonnull/nullable与我们的断言和异常一起看待，其需要处理的问题都是同一个：违反约定是一个程序员的错误。特别是，返回值是我们可控的东西，如果返回值是nonnull的，则我们不应该返回nil，除非是为了向后兼容。



[BackHome](http://ablexie.github.io/)