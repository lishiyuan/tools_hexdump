一个大佬给我发了一个hexdump调试小工具的源码，用于【获取event事件信息数据】，比命令【hexdump /dev/input/event0】好用多了！这里非常感谢这位大佬！

原文：[如何读取Linux键值，输入子系统，key，dev/input/event，dev/event，C语言键盘【转】](https://www.cnblogs.com/sky-heaven/p/9358475.html)

---

# 一、使用方法

1. 拷贝源码保存在xxx.c中

2. 在Linux中将源码进行交叉编译，生成可执行文件read_event_key_value（名字看自己喜好了）

   ```c
   arm-linux-gnueabihf-gcc -o read_event_key_value xxx.c
   ```

3. 将生成的可执行文件拷贝到板卡，板卡中执行下述命令即可：

   ```c
   ./read_event_key_value 0      <----0表示设备event0
   ```

4. 效果如下：

   ```c
   root@imx6ulevk:~# ./read_linux_key_value 0
   /dev/input/event0
    evdev version: 1.0.1
    name: 20b8000.kpp
    features: unknown keys/buttons reserved repeat
   /dev/input/event0: open, fd = 3
   Thu Sep 21 17:27:47 2017.869136 type 0x0004; code 0x0004; value 0x00000000; Misc
   Thu Sep 21 17:27:47 2017.869136 type 0x0001; code 0x0069; value 0x00000001; Key 105 (0x69) press
   Thu Sep 21 17:27:47 2017.869136 type 0x0000; code 0x0000; value 0x00000000; 
   Thu Sep 21 17:27:47 2017.998944 type 0x0004; code 0x0004; value 0x00000000; Misc
   Thu Sep 21 17:27:47 2017.998944 type 0x0001; code 0x0069; value 0x00000000; Key 105 (0x69) release
   Thu Sep 21 17:27:47 2017.998944 type 0x0000; code 0x0000; value 0x00000000; 
   ```

   