https://github.com/DiaosSama/SCUT_IS_Study

### 什么是信息安全？信息的三个基本安全属性是什么？

信息安全，顾名思义，是为了维护信息的安全，实质上是为了维护信息的价值。信息安全是对信息的保密性、完整性和可用性的保持。信息安全的三个基本安全属性是保密性、完整性、可用性。

### 什么是软件安全？三大典型软件安全威胁是什么？

软件安全就是使软件在受到恶意攻击的情况下依然能够继续正确运行的工程化软件思想。三大经典软件安全威胁是：

- 软件缺陷与漏洞（正常软件）
- 恶意软件：实现恶意目的
- 非法破解，知识产权被侵害（正常软件）

### 什么是软件缺陷？

软件缺陷，常常又被称作Bug，是指计算机软件或程序中存在的某种破坏正常运行能力的问题、错误，或者隐藏的功能缺陷。

### 什么是软件漏洞？主要威胁体现？

软件漏洞，是指软件在设计、实现、配置策略及使用过程中出现的缺陷，其可能导致攻击者在未授权的情况下访问或破坏系统。

### 什么是恶意软件？

“恶意软件”是指那些设计目的是为了实施特定恶意功能的一类软件程序。最典型的恶意软件包括：计算机病毒、特洛伊木马、后门、僵尸、间谍软件等。

### 了解stuxnet、duqu和flame（火焰）病毒

- Stuxnet：破坏伊朗核设施（2010年被发现，4个系统漏洞，+2个WinCC漏洞）
- Duqu：窃取伊朗工业控制系统数据（2011年被发现）
- Flame：窃取伊朗石油部门的商业情报（2012年5月被卡巴斯基发现，部署于至少4年以前）

### 什么是勒索软件？

勒索软件是一种流行的木马，通过骚扰、恐吓甚至采用绑架用户文件等方式，使用户数据资产或计算机资源无法正常使用，并以此为条件向用户勒索钱财。

### 什么是软件破解？

软件破解。即通过对软件自身程序进行逆向分析，发现软件的注册机制，对软件的各类限制实施破解，从而使得非法使用者可以正常使用软件。

### 为保障软件安全，目前典型的防护手段有哪些？

1. 强化软件工程事项，将安全问题融入到软件的开发管理流程之中，在软件开发阶段尽量减少软件缺陷和漏洞的数量
2. 保障软件自身运行环境，加强系统自身的数据完整性校验
3. 加强系统自身软件的行为认证——软件动态可信认证
4. 恶意软件检测与查杀
5. 黑客攻击防护——主机防火墙、HIPS
6. 系统还原
7. 虚拟机、沙箱隔离技术等

### 软件静态可信和动态可信？

- 静态可信是软件的数据完整性
- 动态可信是在确保软件数据完整性的前提下，确保软件的行为总是以预期的方式，朝着预期的目标运行

### Safety与Security的区别是什么？

Safety指保证安全免受自然的，物理上的实际的损害，比如自然灾害，物理设备宕机，破损等灾害的侵害。
Security指保证安全免受人为的，主观故意的侵害，相对于Security比较抽象，比如保护计算机系统免受恶意攻击使信息系统的保密性，完整性和可用性受到破坏。

### 系统引导与恶意软件关系（恶意软件如何在系统重启、系统重装、以及硬盘更换之后继续获得控制权？）

（1）恶意软件需要在系统重启之后继续获得控制权，首先就要了解系统启动需要经过的步骤。首先，CPU从固定位置启动BIOS，启动之后，BIOS执行带电自检，检查硬件是否满足启动条件。紧接着，BIOS会从磁盘等物理设备中读取引导程序MBR，并将控制权交给引导程序，在这一步，恶意软件就可以获取控制权，例如MBR病毒，它可以感染引导区，重写引导记录，使得在正常的引导程序运行之前先将病毒加载入内存，起到在系统重启时仍能继续获得控制权的效果。相似的病毒还有Dos引导区病毒，它是在加载其他分区的引导程序时将病毒代码注入到内存中，起到在系统重启之后仍能继续获得控制权的效果。另外，还有病毒是通过篡改操作系统的启动项，使得操作系统启动时将病毒程序当做系统启动项一起加载，起到在系统重启之后可以继续获得控制权的效果。

（2）恶意软件想要在系统重装后继续获得控制权，就不能将病毒程序存放在操作系统之中。所以前面提到的MBR病毒，Dos引导区病毒这种不依赖于操作系统本身的病毒就可以在系统重装后仍获得控制权。

（3）恶意软件想要再硬盘更换之后继续获得控制权，就不能将病毒程序存放在操作系统之中，那么只剩下一个选择，则是感染BIOS程序。所以只有BIOS病毒可以在硬盘更换之后继续获得控制权。但是由于BIOS一般是固化在主板的ROM之中的，所以只能通过物理方式一开始便将恶意程序烧录到主板装载BIOS的ROM中，才能起到感染的效果。这样的病毒在BIOS启动时就会通过挂钩加载执行恶意程序，起到获得操作系统控制权的作用。

### Ring0，Ring3和内核模式，用户模式的关系

Intel的CPU将特权等级分为4级，RING0-3，Windows只使用其中的RING0和RING3，RING0只给操作系统用，也就是内核模式，RING3谁都能用，也就是用户模式

### Windows系统虚拟空间和物理空间的映射机制

二级页表

页目录索引（CR3寄存器获得基址）、页表索引、字节索引

### 什么是PAE（physical Address Extension）模式？开启后处理器的寻址能力可以提高到多少GB？

物理地址扩展 (PAE) X86 允许软件使用地址窗口扩展 (AWE) API 集并在具有 Intel Pentium Pro 或更高版本处理器的计算机上运行，而 4 GB 以上物理内存允许将更多物理内存映射为应用程序的虚拟地址空间。从原来的4GB扩展到64GB。

### 了解WinDbg工具



### 比较磁盘的CHS参数寻址和LBA寻址

- CHS（老式磁盘：每个磁道扇区数相等）

  - 磁头数（Heads）：0 - 255
  - 柱面数（Cylinders）：0 - 1023
  - 扇区数（Sectors）：1 - 63**（注意是从1开始）**一个扇区一般是512字节

  CHS参数寻址可以寻址的磁盘最大容量：256 * 1024 * 63 * 512 / 1048576 = 8064 MB（1M = 1048576 Bytes）

- LBA（现代硬盘：等密度结构）

  - 寻址方式采用线性逻辑块寻址LBA，即以扇区为单位进行线性寻址

    LBA  =  (C - CS) * PH * PS + (H - HS) * PS + (S - Ss)

    - C为当前柱面号
    - CS为起始柱面号（一般为0）
    - PH表示每柱面有多少个磁道（本质上就是磁头数）（一般为255）

### 比较磁盘的两种分区格式：MBR和GPT

- MBR最大支持2TB的硬盘大小，而GPT可以支持2TB以上的硬盘大小。
- MBR中最多支持四张分区表，而GPT理论上可以支持无限的分区。
- MBR仅一个扇区，破坏之后很难回复，而GPT的分区表和表头有备份。

### 了解主引导扇区结构（主引导记录程序+DPT+结束标志）

主引导扇区总共512字节，主引导记录MBR占446字节，分区信息占64字节，剩余2字节为结束标记0xAA55（主引导扇区以小端模式存放）

### 了解DPT分区项各个字段含义，估算存储容量

![DPT分区各字段含义](E:\Desktop\2017级SCUT\大三上学期\软件安全\DPT分区各字段含义.png)

### Fat32文件系统结构？什么是簇？FAT表？簇链？文件目录项首簇和文件大小的位置。删除文件与源文件差异？

- Fat32文件系统结构：（DBR+保留扇区） + FAT1 + FAT2 + DATA（全为小端模式）

- 簇：文件系统将磁盘空间以一定数目的扇区为单位进行划分，这样的单位称为簇。簇是进行文件空间分配的最小单位

- FAT表：文件分配表，功能：1. 记录数据存储区每一个簇的使用情况（是否被使用，或坏簇）；2. 形成每个文件的簇链表

- 簇链：一个文件所占用簇的序号形成的单向链表

- 文件目录项：
  - 首簇偏移：0x14开始的2字节为文件起始簇号的高16位，0x1A开始的2字节位文件起始簇号的低16位
  - 文件大小偏移：0x1C开始的4字节为文件长度（倒数4字节）
  
- **删除文件与源文件差异**：文件目录项的首字节被修改为0xE5（标志该文件已删除），首簇高位被清零；FAT表中的簇链被释放（从0xFFFFFF0F变为全0）；但DATA区中文件的数据仍保存

  ![FAT32目录项](E:\Desktop\2017级SCUT\大三上学期\软件安全\FAT32目录项.png)

### NTFS文件系统结构？什么是MFT？MFT项的两部分组成？

- NTFS文件系统结构：
  1. 1个引导扇区 + 15个扇区的NTLDR区域
  2. MFT元数据文件
  3. MFT分配的空间（2+3=MFT）
  4. 文件存储区
  5. MFT前几个数据文件的备份（元数据备份）
  6. 文件存储区
- MFT：主控文件表，是NTFS卷结构的核心，它记录了除文件数据以外的所有属性，甚至小文件的数据本身也包含在MFT中。MFT是以文件记录数组来实现的，每个文件记录的大小固定为1KB（**MFT中每个文件记录的结束标记为0xFFFFFFFF**）
- MFT项的两部分组成为：
  - **表头（文件记录头）**
    - 长度和偏移处的数据含义不变
  - **属性列表**
    - 属性是File具体信息的载体，一个File的所有信息（包括文件的内容）都通过属性体现
    - 不同的属性列表对应偏移对应着不同的含义

### 什么是PE文件？如何判断是PE文件？（MZ文件标志、PE文件头4字节字串）

- PE文件：可移植的可执行文件（PE，Portable Executable File），Win32平台可执行文件使用的一种格式
- 如何判断是PE文件：
  1. MZ文件标志：PE文件的MZ文件头最开始的两个字节为0x4D5A（即MZ）
  2. PE文件头的4字节字串：“PE \0 \0” 即 “ \50 \45 \00 \00"（PE文件头的起始位置可以在DOS程序头中的偏移0x3C处找到 ）

### 了解PEView、Stud_PE、Ollydbg工具使用



### PE文件格式（Dos头+PE文件头+节表+节）

- Dos头 = MZ文件头（0x40 Bytes）+ Dos Stub（不定长）
- PE文件头 = PE字串（“PE \0 \0”）+ 映像文件头（FileHeader）（0x14 Bytes） + 可选文件头（OptionalHeader）
- 节表
- 节

### 映像文件头中哪几个字节给出节数和可选映像头的大小

- 节数（NumberOfSection）：偏移0x02处给出，大小2字节
- 可选映像头大小：偏移0x10处给出，大小2字节

### 可选映像头的数据目录中哪两项是必须保留的

- Import Table（1）
- Import Address Table（12）

### 几个概念：ImageBase、RVA、节的对齐粒度

- ImageBase：PE文件在内存中的优先装载地址
- RVA：Relative Virtual Address，相对虚拟地址，它是相对内存中ImageBase的偏移位置
- 对齐粒度（文件中、内存中）：文件中的对齐值，文件中每个节都起始于这个值的整数倍处。  

### 为什么PE文件中会有很多0x00字节

由于有一些节的大小小于PE文件规定的对齐粒度，不足的部分会用0x00填充，所以PE文件中会有很多0x00字节

### 节表中元素个数是如何确定的？每个元素占多少字节？

节表（实际上为一个结构数组）中的元素个数由之前映像文件头中的NumberOfSection字段确定，**每个元素占0x28个字节**

### 为什么需要引入函数节？Image_Import_Descriptor结构数组的元素个数如何确定？

引入函数节用于从其他（系统或第三方写的）DLL中引入那些程序中需要调用的，但是又不在调用者模块中的函数，例如user32.dll、gdi32.dll等

Image_Import_Descriptor结构数组的长度不定，但是它的最后一项是全0，可以以此判断数组的结束，然后用数组长度除以每个数组元素的大小即可获得数组长度（该数组中成员结构的个数取决于程序要使用的DLL文件的数量，每个结构对应一个DLL文件）**（数组元素的大小为0x14字节）**

### 引出函数节的作用

引出函数节是本文件向其他程序提供调用函数的列表所在的“索引”及具体代码实现，使得其他函数可以调用本文件中的API函数

### 比较计算机病毒与蠕虫

计算机病毒与蠕虫的不同点在于：

- 蠕虫是一个完整，可以独立运行的独立个体；病毒是一串代码，需要依附在宿主程序上运行
- 蠕虫的传播方式是通过自我复制，并在网络上传播感染不同的主机；病毒的传播方式主要是通过代码寄生感染不同的程序，进而感染不同的主机
- 漏洞利用型蠕虫传播不依赖于计算机用户，而是依赖于网络上存在漏洞的主机；病毒的传播依赖于计算机用户的操作
- 蠕虫的再次执行可以通过系统的自启动机制；病毒的再次执行一般依赖于宿主的执行
- 蠕虫的传播目标是网络中存在漏洞的主机；病毒传播的目标一般是本地文件或系统
- 病毒的主要影响在于本地的主机系统，蠕虫不仅会对本地主机系统造成影响，还会极大的影响网络及系统性能

### 计算机病毒的四个阶段（潜伏、传播、触发、执行）

- 潜伏阶段：病毒最终要通过某个事件来激活，例如一个日期，另一个程序或文件的存在，或者磁盘的容量超出了某个限制，并不是所有的病毒都有这个时期
- 传播阶段：病毒将与自身完全相同的副本放入其他程序或者磁盘上的特定系统区域。每个受感染的程序将包含病毒的一个克隆。这个病毒本身便进入了一个传播阶段
- 触发阶段：病毒被激活来进行它想要完成的功能。和潜伏阶段一样，触发阶段可能被不同的系统事件所引起
- 执行阶段：功能被完成。这个功能可能是无害的，例如显示在屏幕上的一个消息；或者是破坏性的，例如破坏程序和数据文件

### 什么是Cookie？带来的安全问题是什么？如何防范？

Cookie是一种小型文本文件，是某些网站为了辨别用户身份，进行Session跟踪而储存在用户本地终端上的数据，由用户客户端计算机暂时或永久保存的信息。

Cookie欺骗、Cookie截获

对接收到的Cookie进行验证，不再Cookie中存放敏感信息

### 什么是网站挂马攻击？跨站脚本攻击XSS？APT（Advanced Persistent Threat）？网络钓鱼攻击？Bots？间谍软件？流氓软件？

- 网页挂马是结合浏览器或浏览组件的相关漏洞来触发第三方恶意程序下载执行的，攻击者通过在正常的页面中插入一段漏洞利用代码，浏览者在打开该页面的时候，漏洞被触发，恶意代码被执行，然后下载并运行木马的服务端程序。
  
- XSS指攻击者将恶意脚本代码嵌入到正常用户会访问到的页面中，当正常用户访问该页面时，会导致嵌入页面的恶意脚本代码执行，从而达到恶意攻击用户的目的

- APT，即高级可持续威胁攻击，也称为定向威胁攻击，指某组织对特定对象展开持续有效的攻击活动，是一种有极强隐蔽性和针对性、先进的、持久的且有效的威胁和攻击
- 网络钓鱼攻击是攻击者利用欺骗性的电子邮件和伪造的Web站点来进行网络诈骗活动，诱使被攻击者给出敏感信息（如用户口令，身份证号等）的一种攻击方式
- Bots是一种能执行外部命令的自动运行型木马，黑客可以利用这些木马在被感染计算机上偷窃数据，或者利用受感染机器攻击其他计算机等等
- 间谍软件是一种能够在用户不知情的情况下，在其电脑上安装后门、收集用户信息的软件。它能够搜集、使用、并散播用户的个人信息或敏感信息
- 流氓软件指在未明确提示用户或未经用户许可的情况下，在用户计算机或其他终端上强行安装运行。侵犯用户合法权益的软件

### 说明获取API函数地址的多种方法

1. 直接在Kernel32.dll的引出函数表中搜索给定的API地址
2. 先在Kernel32.dll的引出函数表中搜索出GetProcAddress和LoadLibrary两个API函数的地址，然后利用这两个API函数得到需要的API函数地址：通过LoadLibrary加载API所在的动态链接库，然后调用GetProcAddress根据API名来获取函数地址

### 动态获取Kernel32.dll基地址的方法

1. 通过PEB（process environment block）获取，这是最可靠的一种方法，原理是在NT系统内核中FS寄存器指向TEB结构，TEB+30h指向PEB结构，PEB+0ch指向PEB_LDR_DATA结构，PEB_LDR_DATA+1ch处存放相关动态链接库地址，其中第二个就是kernel32.dll的地址
2. 通过SEH（structured exception handling）获取，原理是默认情况下SEH链表的末端结构会指向Kernel32.UnhandledExceptionFilter函数地址。所以可以通过遍历异常处理链表来找到系统默认的异常回调函数地址，再通过该地址向低地址以64KB的对齐单位查找MZ文件头，该标志所在地址通常即为Kernel32.dll的基地址
3. 通过TOPSTACK获取，这种方法只适用于Windows NT操作系统，每个执行的线程都有它自己的TEB（线程环境块），该块中存储着线程的栈顶的地址，从该地址向下偏移0x1c处的地址肯定位于Kernel32.dll中，则可通过该地址向低地址以64KB为单位来查找Kernel32.dl的基地址

### 添加新节感染文件的基本步骤

1. 判断目标文件开始的两个字节是否为“MZ”
2. 判断PE文件标记“PE”
3. 判断感染标记（如果已感染则跳出）
4. 获得DataDirectory的个数（一个数据目录信息占8个字节）
5. 计算节表起始位置（DataDirectory偏移+数据目录占用的字节数=节表起始位置）
6. 获得最后节表的末尾偏移（= 节表起始地址+节数*0x28）
7. 写入节表
8. 修改映像文件头中的节表数目
9. 修改AddressOfEntryPoint（程序入口地址），同时保存旧的入口地址，以便返回
10. 更新SizeOfImage（内存中整个PE映像尺寸=原SizeOfImage+病毒节经过内存对齐后的大小）
11. 写入感染标记
12. 写入病毒代码到新添加的节中
13. 将当前文件位置设置为文件末尾

### 什么是宏病毒？宏病毒的特点？

宏病毒是使用宏语言编写的程序，可以在一些数据处理系统中运行，存在于数据文件之中，可以利用宏语言的功能将自己复制并繁殖到其他数据文档里。

宏病毒的特点：1. 传播极快 2. 制作、变种方便 3. 破坏性可能极大 4. 多平台交叉感染

### 什么是VBS脚本病毒？

用VBScript编写，能够进行自我传播的破坏性程序，其需要人工干预触发执行

### 影响网络蠕虫传播速度的主要因素？网络蠕虫的四个传播阶段？

- 主要因素：
  1. 存在漏洞的主机被发现的速度
  2. 有多少潜在“脆弱”主机可以被利用
  3. 网络蠕虫对这些目标的感染速度
- 四个阶段：慢启动期、快速传播期、慢结束期、衰亡期

### 木马程序和一般后门程序的区别？木马的植入方式？网络木马的连接方式和各自优缺点？

- 区别：从原始本质上来讲，后门并不直接对系统进行攻击，也没有直接恶意行为，其本身并不是一个攻击实体，它的存在目的仅仅是为其他的恶意代码或攻击者提供通道，在此基础之上，木马或病毒等恶意代码就可以通过它来入侵系统，实施恶意行为。  
- 植入方式：
  1. 通过网页植入，比如网页挂马攻击
  2. 通过程序的下载进行植入
  3. 通过攻击存在漏洞的系统，攻破之后在系统中植入木马
- 连接方式及各自优缺点：
  - 正向连接：木马服务器端在被感染主机上打开特定端口等待连接。
    - 优点：可以较好地隐藏攻击者
    - 缺点：容易被防火墙阻断导致连接失败。同时由于服务端的IP地址可能会经常变化，服务端的上线时间也并不确定，会给攻击者带来一定困难。
  - 反向连接：木马服务器端主动向客户端程序发起连接。
    - 优点：可以有效规避防火墙的过滤，并且可以随时获取服务端的动态，有较好的实时性。
    - 缺点：服务端中会存有木马客户端的连接信息
  - 通过第三方主机的反向连接：在反向连接的基础上，两个主机间不直接进行通信，而是通过第三方主机来中转
    - 优点：反向连接优点+可以较好地保护攻击者真实的主机地址
    - 缺点：必须拥有稳定的第三方“肉鸡”

### 恶意软件的检测技术

1. 特征值检测技术
2. 校验和检测技术：病毒检测工具校验、程序自校验
3. 虚拟机检测技术：先采用特征值方式，如果发现隐蔽式病毒或多态性病毒，启动软件模拟模块，监视病毒运行
4. 启发式扫描技术：根据软件的行为判断是否为恶意软件

### 什么是dll劫持

将与系统同名的dll文件存放在程序运行目录下，程序运行调用dll时会优先加载当前目录下的dll，那么程序就会调用该dll中的操作，再跳转到系统dll同名函数里执行，这个过程就叫做DLL劫持

### CVSS通用漏洞评估方法

CVSS，通用安全漏洞评估系统，是一个开放的行业标准。CVSS 的发布为信息安全产业从业人员交流网络中所存在的系统漏洞的特点与影响提供了一个开放式的评价方法。  

### 为什么引入CVE标准？

因为在网络安全发展的早期，不同厂商对漏洞的披露没有一个标准可供参考，漏洞的定义多而杂。为了应对这种情况，所以建立了CVE“通用漏洞列表”，提供了一个漏洞评估的标准，也使得不同的漏洞库和安全工具容易共享数据。

### CNVD，CNNVD标准的发起方

- CNVD，国家安全漏洞共享平台，发起方是国家计算机网络应急技术处理协调中心（中文简称国家互联应急中心，英文简称CNCERT）
- CNNVD， China national vulnerability database of information security，中国国家信息安全漏洞库，发起方是中国信息安全评测中心

### 什么是缓冲区溢出攻击？Shellcode的定义、特点和功能？NOP雪橇？

- 缓冲区溢出攻击：攻击者通过特制的数据进行缓冲区溢出覆盖，利用缓冲区溢出漏洞修改内存数据，改变程序执行流程，劫持进程，执行恶意代码，最终获得主机控制权
- Shellcode
  - 定义：在缓冲区溢出攻击中植入到目标进程中的，用来获取shell的代码
  - 特点：
    1. 是一段机器码，植入目标进程后CPU可以直接运行
    2. 具备代码重定位和API自搜索功能，不严重依赖于系统或进程
    3. 长度受限，不能使用特定字符
  - 功能：
    1. 正向连接
    2. 反向连接
    3. 下载程序并执行
    4. 生成可执行文件并运行
- NOP雪橇：用来绕过堆栈随机化的缓冲区攻击技术

### 缓冲区溢出攻击的步骤？

### 什么是SQL注入攻击？

所谓SQL注入，就是攻击者通过把SQL命令插入到Web表单或页面请求的查询字符串，使得最终达到欺骗服务器执行恶意的SQL命令的目的。

### 什么是Dword shoot堆溢出？Heap spray堆喷射？

- 堆溢出：堆溢出就是在堆的操作过程中寻找一次向内存任意地址写入任意数据的机会，这种机会就叫做Dword shoot
- 堆喷射：向堆中注入大量数据，使得数据填满特定内存地址空间，当栈溢出时可以引导EIP到堆的空间，执行shellcode。堆喷射是使用栈溢出和堆结合的一个技术

### 什么是虚拟补丁？

虚拟补丁是指在不修改应用程序源代码、二进制代码或重新启动应用程序的情况下，能够即时建立一个安全策略实施层，用来防止对已知漏洞的攻击。

### 什么是0-day，1-day，n-day漏洞？

- 0-day漏洞：未被公布、未被修复的漏洞
- 1-day漏洞：已被公布、但由于大部分人未修补导致脆弱性依然存在的漏洞
- N-day漏洞：已被公布、大部分人也已经通过补丁修补的漏洞

### 什么是exploit？漏洞利用的目标有哪些？

- exploit：用于触发漏洞并完成恶意操作的程序
- 漏洞利用的目标：未能及时更新补丁的用户

### 什么是Ret2libc？ROP技术？

- Ret2libc：一种无Shellcode的漏洞利用技术，即不直接跳转到shellcode，而是调用用系统库中特定函数，当调用的库属于C运行库时，称为libc
- ROP：是Ret2lib的升级版，当漏洞触发时不跳转到shellcode，而是通过拼接内存中的返回指令，实现控制程序执行流程到内存中的任何指令序列

### Metasploit架构MSF

是一个通用化漏洞测试和利用平台。他对漏洞利用的几个相对独立的过程进行了很好的封装，将一次完整的入侵过程简化为对几个模块的选择和若干参数的填写

### 源代码安全审计方法

### 静态切片和动态切片？

- 切片技术是将程序简化为和某个特殊计算相关的语句的技术，来源于数据流分析方法
- 静态切片：被定义为”可能影响“一个值的所有语句，其相关计算只利用静态获得的信息，并且是从切片的标准开始，以向后遍历的方式收集语句和控制谓词
- 动态切片：采用动态的数据流和控制流分析方法，而程序语句间的依赖关系是在以特定数据为输入的程序执行后确定。

### Fuzzing测试

Fuzzing测试是一种特殊的黑盒测试法（更关心鲁棒性而并非软件功能），是一种利用大量的计算资源自动化地进行程序异常和漏洞发现的方式

### 绕过DEP方法

1. DEP通过使可写内存不可执行，可执行内存不可写防止溢出修改返回地址的行为。
2. ret2libc绕过DEP
3. WPM与ROP技术绕过DEP
4. 关闭进程的DEP
5. 一些简略的方法：
   - 利用ret-to-libs执行命令或进行API调用
   - 将包含Shellcode的内存页面标记为可执行，然后再跳过去执行。
   - 通过分配可执行内存，再将shellcode复制到内存区域然后跳过去执行
   - 先尝试关闭当前进程DEP保护，然后再运行Shellcode。

### 什么是栈溢出检查方法？Security cookie是如何保证不可仿造的？

- 栈溢出检查方法就是在程序运行开始时，通过向函数的开头和结尾添加代码来阻止针对典型栈溢出漏洞的利用
- 不可仿造的原因是cookie很少是一个静态值，即使是静态值，但其中可能包含一些不利的字符而使得很难使用它

### 地址空间布局随机化ASLR的缺陷？

- ASLR保护机制进行随机化的对象主要包括以下几个方面：
  - 映像随机化：改变可执行文件和DLL文件的加载地址
  - 栈随机化：改变每个线程栈起始地址
  - 堆随机化：改变已分配堆的基地址
- 缺陷：
  - 随着系统重启，ASLR在整个系统里生效。如果采用特定DLL所有进程都卸载该DLL，下次加载时它能被加载到新的随机位置，但由于许多系统DLL总是由多个进程加载，导致只有在操作系统重启时才能再次随机化。因此对于本地的攻击，攻击者很容易获取所需要的地址。
  - 返回地址部分覆盖法可以绕过ASLR。
  - 还有就是很多程序和dll模块未采用/DYNAMICBASE连接选项进行分发，在系统重启后并没有地址空间分布随机化。

### 什么是EMET？理解EMET在黑客攻击检测中作用

1. 含义：微软推出的一套用来缓解漏洞攻击、提高应用软件安全性增强型体验工具。
2. 增强型DEP、升级版SafeSEH、强制性ASLR、HeapSpray防护。









