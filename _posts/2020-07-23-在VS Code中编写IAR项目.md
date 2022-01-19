---
categories:
  - Computer Science
tags:
  - Tool
---

[cnblogs链接](https://www.cnblogs.com/linkchen/p/13366742.html)

首先按照网上的教程，下载C/C++插件，以及IAR Eebedded Workbench插件，安装完成重启VS Code。

项目目录下新建.vscode文件夹，并新建iar.json和settings.json文件

iar.json内容示例

```json
{
    "version": 1,
    "path": "C:\\Program Files (x86)\\IAR Systems\\Embedded Workbench 8.0\\",
    "project": "C:\\Projects\\TEST\\TEST.ewp",
    "config": "Debug"
}
```

version默认1，path为IAR环境安装的目录，project为IAR项目中的.ewp文件，config为IAR项目的configuration的name，可以打开.ewp文件搜索configuration查看```<name>```标签注意此处最后一定要有```\\```，如果不加```\\```，path如下：

```json
 "path": "C:\\Program Files (x86)\\IAR Systems\\Embedded Workbench 8.0"
```

则在运行的时候，会报错，内容如下：

```
Building configuration: Debug
Error while starting IarBuild.exe. Open it with IAR Ide to fix it.
Something went wrong...
```

上网搜索很多内容，最终在该插件的作者politoleo的github项目issues中找到了回答：

https://github.com/politoleo/iar/issues/1

<img referrerPolicy="no-referrer" src="https://img2020.cnblogs.com/blog/1560524/202007/1560524-20200723154656480-364570565.jpg" alt="github">

其实就是环境的路径问题，所以一定要在path最后加上```\\```，意思就是递归所有子文件夹，最后settings.json内容：

```json
{
    "iar.enabled": true
}
```

最终通过快捷键Ctrl+Shift+B完成Build操作。
