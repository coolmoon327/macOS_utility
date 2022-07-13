---
title: macOS用户的自我修养
abbrlink: 10230
---

# macOS用户的自我修养

> **写在前面：**本文针对 macOS 系统给出了一些2021年的软件生态推荐，其中的部分软件在 Windows 10 系统下也有对应版本。所有推荐基于作者本人写论文、做开发的习惯出发，开发类生态偏向于实验仿真与iOS开发，如有更好的推荐，轻喷后务必留言分享。

## 一、基础篇

---

​	大多数小伙伴对苹果电脑的第一反应就是xxx不能用、xxx不能玩、花几万买个电子辣鸡云云，实则不然。这里讲给出一些软件推荐，帮助习惯于 win 生态的小伙伴早日适应 macOS ~~(脱离巨硬的魔爪)~~。

### 1. Parallels Desktop

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210822214858.png" style="zoom:50%;" />

> [Parallels Desktop](https://www.parallels.com)是一个强大的虚拟机挂载平台，强大到在m1芯片发布的第一时间进行了对win on arm虚拟机的适配。该软件是我用过bug最少、性能最强、功能最适合mac用户的虚拟机平台，对Windows与ubuntu系统有特殊优化，喜欢网络工程的小伙伴甚至能使用它在mac上配置低功耗的openwrt环境作为本机网关。

**游戏性能**

​	不同于vmware等常见的虚拟机平台，parrallel能够对gpu资源进行调度（而通常的虚拟机只能用cpu模拟gpu），从而在一定程度上能够在虚拟机内部“畅玩”大部分游戏，这也是其公司所大力宣传的。不过，PD并不能调度显存，它是用内存进行的显存模拟，并且最大只支持2GB的模拟显存，因此并不能对其游戏性能抱有太多期待。

**融合模式**

​	融合模式是PD的另一个主打功能。其本质就是将虚拟机中的窗口映射到macOS中，并能在macOS中使用虚拟机中的软件打开任何文件。话不多说，上图：

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210822221044.jpeg" style="zoom: 33%;" />

​	通过融合模式，我们可以在 mac 上同时使用 Windows 与 macOS 的应用程序，win 的活跃 app 将与 mac 的一同显示在程序坞中。通过多年实测，该模式的功耗需求极低（不需要渲染大量图形界面），并且能够完美运行 mac 文件夹中的 windows 程序（exe 可执行文件、bat 批处理脚本等），**对于小白而言绝对是上手 macOS 过程中最好的软件**。

​	除此之外，众所周知苹果因为授权的原因并未开放对 ntfs 文件系统的写入，也就是说，Windows 的移动硬盘挂载到 macOS 后是只读的。这里注意我的用词，“未开放”，苹果其实一直都是原生支持 NTFS 文件格式写盘的，只是需要用户手动进行命令行配置（详情请百度），而网络上一般建议 macOS 和 Windows 共用的硬盘格式化成 EXFAT 文件系统。 Parallels Desktop 的融合模式非常好的解决了这个问题，该软件能够直接将 NTFS 硬盘挂载到 win10 虚拟机下，但依旧能使用 macOS 中的软件运行虚拟机中的程序，这就是该软件主打的**“融合”**。

### 2. Tuxera NTFS for Mac / Paragon NTFS for Mac

​	Tuxera NTFS for Mac 和 Paragon NTFS for Mac 是 macOS 中用于挂载 ntfs 文件系统的两个~~强大~~插件。前面我们说了，一般情况下 macOS 上挂载 NTFS 文件系统的硬盘是只读的，要想变成“完全控制”需要使用 Terminal 运行一些命令行代码，而这俩软件实际上就是一个自动进行挂载过程的后台插件。因此，这俩插件只能说体验不错，但究其功能而言完全配不上“强大”一词，再加上高昂的定价，本着不推荐盗版的基本道德修养，我还是建议码农们从网上找点自动挂载 NTFS 的脚本，有钱并且懒得折腾的同学可以考虑购买。

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210822224900.png" style="zoom: 50%;" />

​	顺带说一句，上述在 Terminal 中挂载 NTFS 命令行工具需要对每个硬盘都执行一遍，因此本懒人选择直接使用插件。喜欢折腾的同学可以配合 Toggle Alfred 工具配置自己的自动化挂载脚本。

### 3. TotalFinder & Easy New File

​	TotalFinder 是用来扩展“访达”的小插件，配合拓展右键菜单的 Easy New File 使用时，可以将 macOS “访达”中的文件管理操作变得像 Windows 一样丰富。

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210822225644.png" style="zoom: 33%;" />

​	上图中，TotalFinder 让“访达”拥有了标签页，并且具有更丰富的菜单栏，而 Easy New File 在右键菜单中拓展了“新建文件”、“拷贝路径”、“在终端中打开”等功能（没错，mac甚至不支持直接新建文件）。“拷贝路径”是复制被选中对象的文件路径，比如“/Users/coolmoon/Desktop”，“在终端中打开”则是相当于在 Terminal 中输入 “cd /Users/coolmoon/Desktop”，这俩是对程序员非常有用的功能。除此之外，macOS 实际上是不支持“剪切”操作的，只能在拷贝后使用快捷键实现“移动”操作，非常反常识。上述插件不仅在右键中增加了“剪切”选单，还补充了“cmd + x”的“剪切”快捷键，让文件处理逻辑变得和 Windows 一样亲切。

​	*<u>截止2021年底，TotalFinder还未完成M1芯片macOS的适配。</u>*

### 4. Bartender

​	Bartender是用于设置macOS菜单栏的插件。他可以将菜单栏中的控件隐藏起来，并随意调整各控件的位置。在Preference中，用户可以将菜单栏划分成“显示”、“隐藏”、“始终隐藏”三种类别。其中，“显示”的控件将保持原样，“隐藏”的控件将被放到菜单栏的第二页中，“始终隐藏”的控件将不在菜单栏中显示。

![](https://github.com/coolmoon327/picBed/raw/master/pictures/20210824182029.png)

​	显示的菜单栏，基本保持和macOS原有风格一致：

![](https://github.com/coolmoon327/picBed/raw/master/pictures/20210824182555.png)

​	在我的菜单栏中，为了将QQ音乐的控件居中到屏幕中央，使用Bartender添加了一个Spacer控件，该控件用来增加控件之间的距离，该距离是可任意设置的，也能在其中填入文字，并且Spacer可以被设置成无法被点击：

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824182832.png" style="zoom:50%;" />

​	隐藏的菜单栏，通过点击菜单栏中的“...”控件或者使用自定义的快捷键进行菜单栏翻页：

![](https://github.com/coolmoon327/picBed/raw/master/pictures/20210824183042.png)

​	红框标出了切换“显示”/“隐藏”的菜单栏的控件。Bartender是比较强大、好用的，支持非常详细的自定义样式，并且不局限于菜单栏切换，也可以把“隐藏”的控件放在一个单独的Bar中来显示，更多玩法值得深入摸索。

### 5. Neat Download Manager

​	NDM是一款非常好用的下载软件。很多互联网老人可能比较熟悉IDM，可以说，NDM就是IDM的免费替代品，并且同时支持Windows与macOS操作系统，性能强大的同时完全不需要付费。

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824183627.png" style="zoom:50%;" />

​	NDM可以支持32线程的下载，即使是GitHub，不挂载梯子的情况下也能跑到3～5MBps，而ubuntu等大众资源更是能跑满30+MBps的速度。相较于Aria2，它不需要配置RPC的可视化界面，使用方式也非常简单，甚至支持Mac上所有的主流浏览器，要知道对于插件玩家来说，Safari可是浏览器中的毒瘤。

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824184236.png" style="zoom:33%;" />

### 6. Acrobat

​	macOS自带的pdf浏览器“预览”使用体验并不佳，这种轻量级的软件更适合在iPad与iPhone这些移动端平台上使用。为了高效的阅读、修改、制作pdf，Adobe家的Acrobat无疑是职业键盘侠的最佳伴侣。不同于Windows版本，macOS的Acrobat拥有极其现代化的UI风格，并且各种功能Button也更加人性化，除了高昂的价格都非常有吸引力。

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824184810.png" style="zoom: 25%;" />

​	值得一提的是，Acrobat具有强大的OCR功能，能够直接从图片中提取出文字，而在2021年新的macOS系统中，苹果将从系统层面植入OCR工具来发挥M1等芯片的AI核心计算性能，二者孰强孰弱我们拭目以待。

### 7. iShot

​	iShot是一款非常实用的截图工具。它拥有QQ截图的全部功能，并能轻松实现录屏，且对系统资源的占用极低，基本不会出现QQ截图的卡顿现象。

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824185250.png" style="zoom: 50%;" />

​	同时，iShot可以轻松进行取色，不仅能将色块的RGB值或Hex值保存到剪切板中，还能直接以代码的形式储存譬如`[UIColor colorWithRed:54/255.0 green:59/255.0 blue:64/255.0 alpha:alpha/1.0]`，对程序员与设计从业者来说是十分便利的工具。

### 8. MacZip

​	MacZip，一款好用的解压软件，十分轻量化，UI美观，使用体验不错，功能比苹果自带的强大不少。

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824190137.png" style="zoom:50%;" />

### 9. App Cleaner & Uninstaller

​	App Cleaner & Uninstaller是用来清理、卸载macOS程序的软件。在macOS中，软件的安装方式与Windows有很大不同，是以.app格式的文件包的形式放在"/Applications"路径中的。得益于macOS软件打包的特性，苹果并未提供统一的APP卸载方式，而是推荐用户直接从Application目录中删去对应的软件。

​	从表面上看，直接删除就能完成APP的卸载，然而，APP的很多关联文件都会保存在"/Library"路径中，直接删除.app包并不是完全清除了所有残留文件。这就导致了一个现象，在iOS、安卓、macOS乃至Linux等基于unix内核的系统中，往往系统使用的越久，残余文件就越多，表现出来是有大量的“未知”或“其他”分类的文件。这时候，我们通常只有重装系统才能解决掉这部分空间。

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824191207.png" style="zoom:33%;" />

​	App Cleaner & Uninstaller在卸载软件时，会将与之相关的所有文件一并清理，并会还原一部分被修改了的系统设置。在我们日常使用中，可能遇到APP崩溃后，不管怎么重装都无法正常使用该APP，这可能是由于部分配置文件出错所导致的。直接删除.app包并不能还原一个干净的系统环境，这时候就建议使用这类软件进行深度卸载。

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824190803.png" style="zoom:33%;" />

​	除了程序清理外，App Cleaner & Uninstaller还能调整用户登录项与扩展程序，对于拥有计算机运行环境洁癖的码农而言非常实用。

### 10. IINA

​	当你要在macOS中播放高质量视频时，十个人中有九个人都会给你推荐IINA这一款视频播放软件。它不仅功能强大，通过扩展能支持视频补帧与HDR，并且还是一款免费的软件，UI具有十足的苹果风格，值得推荐。

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824191957.png" style="zoom: 50%;" />

## 二、整活篇

---

​	聊完了能够直接影响用户使用体验的macOS软件，现在让我们丰富一下自己电脑的功能，把它玩出花来。

### 1. Alfred 4

​	Alfred是Spotlight的高强度替代品。作为一个快捷操作软件，Alfred比系统原生的Spotlight功能强大许多，但凡懂点代码都能玩出花来。

​	快捷搜索：

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824192940.png" style="zoom:33%;" />

​	文件搜索：

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824193004.png" style="zoom:33%;" />

​	计算器：

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824193034.png" style="zoom:33%;" />

​	查看剪切板历史：

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824193125.png" style="zoom:33%;" />

​	自定义Workflow——有道词典：

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824193316.png" style="zoom:33%;" />

​	在上图中，我们演示了Alfred的Workflow功能。其本质就是快速执行一系列的用户脚本，这些脚本或系统命令可以通过流程图的方式连接起来，最后实现诸如翻译、快速以某种参数打开某些程序、自动执行宏命令等功能。它支持Shell、PHP、Ruby、Python、Perl、Osascript等主流脚本语言，并为用户包装了大量的系统操作接口，许多复杂的处理过程不需要写一行代码即可完成。

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824193428.png" style="zoom: 25%;" />

### 2. Dynamic Wallpaper

​	Dynamic Wallpaper是一款对标Windows上Wallpaper Engine的动态壁纸软件。比起Wallpaper Engine，它只能以视频的方式播放壁纸，但相较而言更加节省系统资源。同时，Dynamic Wallpaper也可以设置动态屏保，对于喜欢二次元动态壁纸的同学而言还具有不少折腾价值。

<img src="https://github.com/coolmoon327/picBed/raw/master/pictures/20210824194424.jpeg" style="zoom: 33%;" />

