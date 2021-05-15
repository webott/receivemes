QQ：2645542961
本节主要找接收消息的hook地址，需要用到CE和OD工具。附加微信之后，用另外一个微信，给已经登陆的微信发送一条信息，然后用CE 点击：New Scan ，注意不要选 UTF-16，搜索之后，出来了几条结果，再用一个微信发送一条信息，这时看有哪些地址是刚才的发送的内容，把他选到下面去。
![image](https://user-images.githubusercontent.com/73727649/118346344-565e1080-b56d-11eb-91ae-c1c201096679.png)
然后把下面的value值的长度调长，可以看到最长的里面有msg之类的，基本确定是这个地址
![image](https://user-images.githubusercontent.com/73727649/118346347-5b22c480-b56d-11eb-917f-3d6a5fdceb12.png)
然后把这个地址复制下来，在OD里面下个断点，
![image](https://user-images.githubusercontent.com/73727649/118346353-60800f00-b56d-11eb-8ed0-0bb741013ca8.png)
然后发送一个消息，此时就断下来了，然后删除断点，在右下角的窗口找，找到出现msg类似的信息，点击右键，选“反汇编窗口中跟随”，然后在上面汇编里面下断点，
![image](https://user-images.githubusercontent.com/73727649/118346356-670e8680-b56d-11eb-88d4-9b4309f87ee8.png)
![image](https://user-images.githubusercontent.com/73727649/118346357-68d84a00-b56d-11eb-850c-50d5fc2fdc82.png)
然后现在发送一个消息，看下断下来了，然后看esp里面东西，可以看到微信id和一些信息，然后计算 esp与wxid和发送内容之间的相对地址，即：[[esp]]+0x40 是微信id或者群id 的地址，[[esp]]+0x68 是消息内容 ，然后也把偏移地址记录下来。![image](https://user-images.githubusercontent.com/73727649/118346363-6ece2b00-b56d-11eb-8858-f3615d653376.png)
这样就可以得到各种消息通知。
目前已经实现了发送各种消息，群管理，接收各种消息，加好友，清理僵尸粉等等有趣的功能，更多功能一直更新中，欢迎技术交流
QQ：2645542961
![image](https://user-images.githubusercontent.com/73727649/118346377-80afce00-b56d-11eb-85d0-3a9c4d2fc82c.png)

