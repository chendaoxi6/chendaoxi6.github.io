---
categories:
  - Computer Science
tags:
  - Tool
---

[cnblogs链接](https://www.cnblogs.com/linkchen/p/13633568.html)

看以往的教材中R.java都是在项目的\app\build\generated\source\r\debug\包名下的

通常AS会自动在项目的R.java中创建代表项目中资源的资源ID，大致格式如下

```java
public final class R
{
    public static final class layout
    {
        public static final int activity_main = 0x7f040017;
    }

    public static final class mipmap
    {
        public static final int ic_launcher = 0x7f030000;
    }

    public static final class string
    {
        public static final int app_name = 0x7f0b0011;
        public static final int hello_world = 0x7f0b0012;
    }
}
```

结果今天在使用AS4.0.1新建Helloworld项目，发现\generated\source目录下不存在\r\debug\，在文件管理其中搜索有关R的文件发现R.java变为了R.txt

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200908164920086-1915147508.png" alt="1">

并且R.txt在D:\Android\HelloWorld\app\build\intermediates\runtime_symbol_list\debug目录下

stackoverflow上面有这样的操作：

https://stackoverflow.com/questions/28522144/where-is-the-r-java-file-in-android-studio

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200910114812374-273506569.jpg" alt="2">

再右键就能show bytecode就能看见了

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200910114829172-1398197341.png" alt="3">

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202009/1560524-20200910114837261-1710159582.png" alt="">
