---
title: "OSTEP为什么好"
date: 2025-04-28T14:33:15+08:00
draft: false
tags: ["COMMENT", "Operating System"]
---

断断续续把OSTEP看完了，最开始看内存虚拟化的时候弃掉了一段时间，后来又捡了回来，因为别的OS textbook太烂了😂  
为什么OSTEP好？说实话，免费反而是最后要提及的有点，除了美国那边课本死贵死贵之外感觉国内的课本基本上要么用二手要么直接下电子版的了。一本Operating System Concepts哪怕是国内的大黑书也要158一本，不过又有多少人会买呢？  
首先一个好的地方是这本书没有过分聚焦到COA或者ICS应当聚焦的部分，直截了当地告诉你操作系统在哪儿，解决了你在COA或者ICS中没碰见的什么问题。OSC和MOS两本书都是要先给你满嘴口水地讲COA和ICS中嚼烂的内容，估计也就学唐XX计组没学明白的人需要这些内容了吧......当然，硬盘的基本原理它还是给你讲了讲，防止你文件系统直接抓瞎（但其实这个部分可以砍掉，既然你第一章推荐了csapp那这部分可以默认讲过）  
其次就是真实。告诉你历史上怎么做的，怎么演化成如今的样子的。几乎所有的示例都会附上对应的在真实世界中能用的API示例代码。这里的一个反例就是MOS，过分地“又臭又长”，而且示例代码还不那么make sense。重点是每章后方的参考文献都给了你阅读指导，告诉你你不仅应该看这本书，还应该再看看这些内容的相关一手消息。  
至于文风的幽默什么的，也在“真实”和“参考文献”面前不值一提了。既然一本书能够告诉你正确的案例为什么正确，错误的案例是怎么一步一步走向bug的，那你为什么还要选别人呢？OSDP书后的Minix代码已经在网上开源了，而OSDP在国内也停售很久了，再往后就是OSC，没了。交大的那本书还没推开，总之OSTEP从现在的视角看也许算是“独孤求败”的典型代表？  
OSTEP之后呢？其实你应该看看apue，水课或者别的时候翻翻看看，然后看看Great Ideas in Computer System Design，也是书后多次推荐的好文章。最后书后的minilab很多（也许近两年jyy就是受此启发把OSlab干掉了？），看看源码，再看看xv6-riscv，不想做实验看看源码也行，毕竟不是所有人都想做那样的脏活累活，不是吗？或者如果你真有兴趣可以看看分布式系统相关的内容，不过那部分太难了，我也没学多少，就不说了。