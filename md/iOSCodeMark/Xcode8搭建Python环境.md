# Xcode 8中搭建Python环境

很多人苦恼于没有好的[**Python**](http://lib.csdn.net/base/python)编译环境，其实Xcode已经为我们提供了这个条件。

第一步，打开Xcode创建项目，Cross-platform>>External Build System>>Next：

![1BuildProj](mdSource/image/TogetherAll/1BuildProj.png)

第二步，打开终端，

defaults write com.apple.finder AppleShowAllFiles Yes && killall Finder //显示隐藏文件

defaults write com.apple.finder AppleShowAllFiles No && killall Finder //不显示隐藏文件

终端输入以上命令，显示隐藏文件，然后继续输入命令`whereis python`查看Python工具位置，如图：

![Terminal](mdSource/image/TogetherAll/Terminal.png)

返回Python工具位置：/usr/bin/python ，文件夹前往，找到 python后将其copy到你能够找到的地方

![python](mdSource/image/TogetherAll/python.png)

并把位置路径/usr/bin/python 填写到Build Tool中，如图：

![2BuildProj](mdSource/image/TogetherAll/2BuildProj.png)

紧接，创建文件夹创建工程项目，如图：

![Newfoler](mdSource/image/TogetherAll/Newfoler.png)

![CreatProj](mdSource/image/TogetherAll/CreatProj.png)

完成项目创建，如图：

![ProjCreated](mdSource/image/TogetherAll/ProjCreated.png)

  第三步，Produce >> Scheme >> Edit Scheme

![EditScheme](mdSource/image/TogetherAll/EditScheme.png)

第四步，进入Edit Scheme 进行设置  Run  >> info 中的Executable 选中other   添加一开始从/user/bin/python 文件夹下复制出来的 python 并且debug executable的勾一定要去掉，否则会抛出意外退出的错误。

![Executable](mdSource/image/TogetherAll/Executable.png)

![Catch](mdSource/image/TogetherAll/Catch.png)

第五步，在Arguement >> Arguement Passed On Launch 中添加自己的 .py文件名字，否则将不会出现提示并且无法输出。在Options >> Working Directory 中对第一项勾选选择保存路径

![ArguementOption](mdSource/image/TogetherAll/ArguementOption.png)



第六步，选中工程名，command+n  创建一个如图的工程，同时要将名字改成  在Arguement >> Arguement Passed On Launch 中的名字，创建完成后，输入print会有相应的提示，输入printf “Hello,world” 编译运行可以输出，说明已经配置成功。接下来就可以开启你的爬虫之路了。

![1mainPyCreat](mdSource/image/TogetherAll/1mainPyCreat.png)

![2mainPyCreat](mdSource/image/TogetherAll/2mainPyCreat.png)

创建后，开启Python编程，如图：

![CreatedOk](mdSource/image/TogetherAll/CreatedOk.png)



运行结果：

![RunResult](mdSource/image/TogetherAll/RunResult.png)

[BackHome](http://ablexie.github.io/)

