# iOS蓝牙开发(3)BabyBluetooth蓝牙库介绍

[2016-08-14]

>  [**BabyBluetooth**](https://github.com/coolnameismy/BabyBluetooth) 是一个最简单易用的蓝牙库，基于CoreBluetooth的封装，并兼容ios和mac osx。

### 特色：

-  基于原生CoreBluetooth框架封装的轻量级的开源库，可以帮你更简单地使用CoreBluetooth API。
-  CoreBluetooth所有方法都是通过委托完成，代码冗余且顺序凌乱。BabyBluetooth使用block方法，可以重新按照功能和顺序组织代码，并提供许多方法减少蓝牙开发过程中的代码量。
-  链式方法体，代码更简洁、优雅。
-  通过channel切换区分委托调用，并方便切换。

### 来源

最近几个月都在做蓝牙项目，用CoreBluetooch感觉语句写的到处都是，不优雅。一整条链下来要近10几个委托方法，并且不断的在委托方法中调用方法再进入其他的委托，导致代码很零散。因此我就想让coreBluetooth使用更简单，语法更优雅，所以开始写这个BabyBluetooch蓝牙库。

**更新于：20150916,现在BabyBluetooth 已经有了96个star**

**更新于：20160129,现在BabyBluetooth 已经有了880个star**

### Quick Example

```objective-c
//导入.h文件和系统蓝牙库的头文件
#import "BabyBluetooth.h"

-(void)viewDidLoad {
     [super viewDidLoad];

     //初始化BabyBluetooth 蓝牙库
     baby = [BabyBluetooth shareBabyBluetooth];
     //设置蓝牙委托
     [self babyDelegate];
     //设置委托后直接可以使用，无需等待CBCentralManagerStatePoweredOn状态
     baby.scanForPeripherals().begin()
}

//蓝牙网关初始化和委托方法设置
-(void)babyDelegate{
    //设置扫描到设备的委托
    [baby setBlockOnDiscoverToPeripherals:^(CBCentralManager *central, CBPeripheral *peripheral, NSDictionary *advertisementData, NSNumber *RSSI) {
        NSLog(@"搜索到了设备:%@",peripheral.name);
    }];
    //设置设备连接成功的委托
    [baby setBlockOnConnected:^(CBCentralManager *central, CBPeripheral *peripheral) {
        NSLog(@"设备：%@--连接成功",peripheral.name);
    }];
    //设置发现设备的Services的委托
    [baby setBlockOnDiscoverServices:^(CBPeripheral *peripheral, NSError *error) {
        for (CBService *service in peripheral.services) {
            NSLog(@"搜索到服务:%@",service.UUID.UUIDString);
        }
    }];
    //设置发现设service的Characteristics的委托
    [baby setBlockOnDiscoverCharacteristics:^(CBPeripheral *peripheral, CBService *service, NSError *error) {
        NSLog(@"===service name:%@",service.UUID);
        for (CBCharacteristic *c in service.characteristics) {
            NSLog(@"charateristic name is :%@",c.UUID);
        }
    }];
    //设置读取characteristics的委托
    [baby setBlockOnReadValueForCharacteristic:^(CBPeripheral *peripheral, CBCharacteristic *characteristics, NSError *error) {
        NSLog(@"characteristic name:%@ value is:%@",characteristics.UUID,characteristics.value);
    }];
    //设置发现characteristics的descriptors的委托
    [baby setBlockOnDiscoverDescriptorsForCharacteristic:^(CBPeripheral *peripheral, CBCharacteristic *characteristic, NSError *error) {
        NSLog(@"===characteristic name:%@",characteristic.service.UUID);
        for (CBDescriptor *d in characteristic.descriptors) {
            NSLog(@"CBDescriptor name is :%@",d.UUID);
        }
    }];
    //设置读取Descriptor的委托
    [baby setBlockOnReadValueForDescriptors:^(CBPeripheral *peripheral, CBDescriptor *descriptor, NSError *error) {
        NSLog(@"Descriptor name:%@ value is:%@",descriptor.characteristic.UUID, descriptor.value);
    }];

    //过滤器
    //设置查找设备的过滤器
    [baby setDiscoverPeripheralsFilter:^BOOL(NSString *peripheralsFilter) {
        //设置查找规则是名称大于1 ， the search rule is peripheral.name length > 1
        if (peripheralsFilter.length >1) {
            return YES;
        }
        return NO;
    }];

    //设置连接的设备的过滤器
     __block BOOL isFirst = YES;
    [baby setFilterOnConnetToPeripherals:^BOOL(NSString *peripheralName) {
        //这里的规则是：连接第一个AAA打头的设备
        if(isFirst && [peripheralName hasPrefix:@"AAA"]){
            isFirst = NO;
            return YES;
        }
        return NO;
    }];


}
```

CoreBluetooch中实现上扫描，连接，发现服务和characteristic以及它的值相关方法调用是很麻烦啰嗦凌乱的。如下： centralManager启动->状态委托->调用扫描方法->进入扫描到设备的委托->调用连接设备方法->进入连接到设备的委托->发现服务方法->发现服务委托-> 发现characteristic方法->发现characteristic委托->读characteristic的value->读characteristic的value的委托->读description，读description的value-> ….的委托

而BabyBluetooth只需要一句话就执行了上面的内容。

```objective-c
 //扫描设备 然后读取服务,然后读取characteristics名称和值和属性，获取characteristics对应的description的名称和值
  baby.scanForPeripherals().connectToPeripheral().discoverServices()
  .discoverCharacteristics().readValueForCharacteristic().discoverDescriptorsForCharacteristic()
  .readValueForDescriptors().begin();
```

另一方面，BabyBluetooth所有的委托方法都紧凑的聚在了一起。此外，快速示例中没有包括channel的使用，如果包括了channel，那么ios几个页面或者组件的蓝牙 调用模块都可以写在一起，看起来就觉得很方便。

关于更多BabyBluetooth的介绍和使用示例已经api，请移步到[**BabyBluetooth主页**](https://github.com/coolnameismy/BabyBluetooth)查看





[BackHome](http://robinshare.github.io/)