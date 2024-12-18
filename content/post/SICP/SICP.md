---
title: "关于一些网络热门课程"
date: 2024-12-15T13:38:47+08:00
draft: false
---

事先声明，锐评不代表讨厌，相反，正是因为你有了足够的了解之后你才能知道为啥人家的课程好，我们的为什么烂。我感谢它们，在无数节水课中带我消磨时间，做有趣的事情。

### SICP

SICP这个课可就有点儿历史了，上世纪80年代，Abelson和Sussman这俩人用他们编写的教科书改造了MIT的计算机入门课程。它主要使用Lisp的一门方言——MIT Scheme进行编程，讲解关于计算机思维与计算方法的基础知识。现在网上流传的始祖SICP实质上是两个教授去惠普公司进行的讲座，不过内容大同小异就是了。说是基础，但是这个课联同这本书都是极其折磨的。

首先，Scheme，或者说Lisp系的语言只能写递归不能写迭代。这门课程的起初就在不断地教你如何递归展开。随后便是一些时至今日也在使用的编程语言设计理念的雏形——数据结构，面向对象，流，乃至并发。不要用你学某个现代化程度很高的编程语言的经验简单套用在这里，Lisp的bare metal程度某种意义上不亚于C，许多的现有的知识要先有一层抽象才能转化成Lisp的东西。以及这本书会大量地造轮子。造图片编程语言，造小型SQL，造基于Lisp-Like汇编语言的寄存器机器。对，某种意义上你现有的对于计算机的知识都被颠覆了，这本书告诉你只要有了Lisp你能造出来所有东西！

当时学的时候我用了先看课再看书的策略，结果发现书上的题目和前头的知识完全就是雕花和切冻肉的关系（笑）。经常有第一题“来，仿照那个加法程序造一个乘法程序”，第二题“来，刚才用迭代写的同学转化成递归来写，刚才用递归的同学用迭代来写！”，第三题“你看，加法和乘法可以抽象成XXX，这个程序怎么写呢？”，第四题又是迭代换递归，递归换迭代，第五题又再抽象一层，抽象到最后还不忘问你一句“嘿，你觉得你的设计真的合理吗？”，绝大多数情况下我做到第三题就破大防去抄答案了。

第四章和第五章虽说是讲evaluator，SQL和寄存器机器这种显而易见的东西，但是在书里头这玩意儿又被一层又一层抽象了。后来我转念一想“估计这点儿玩意儿我这辈子都用不上了”，就去做了一下“Build your own Lisp”，把第四章和第五章的课程录像看完了就跑了。

现在想想UCB和MIT把这个课程改成Python，SQL和Lisp真是明智的选择。他们从函数入手而不是递归，大大降低了这门课程的门槛，第四章原来的造轮子变成了摆在眼前的SQL，之于更高层次的抽象则交给了Lisp。Sussman曾经暗讽过这个课程改变是让人做脱离系统的调包侠，但是调包不也是优化程序的一种有效手段吗？何况这个课程的教授方式也大变了，先让你熟悉终端，相关硬件的下载和从网站上获取压缩包。这个知识屏蔽已经到极致了。没有git，没有链接，没有过于繁杂的命令行，总之个人认为这个课程进步了很多。

有人会问推不推荐学CS61A，我说你要是大佬休闲想学学无所谓。至于老版的SICP和配套的那本书，实在话，还是直接进入历史的故纸堆就好。我读过了，不建议你走同样的路。顺带一提，负责原始版本SICP翻译的HIT IBM俱乐部今日也某种意义上“半死不活”了。

### Algorithms

最初接触这玩意儿的时候是我淘书的时候发现的人民邮电出版社的中译本，“与TAOCP相媲美的神作”，豁，那可得看看咯。结果第一章就看不懂了，作者居然自己搓了个Java标准库用，还得自己配，然后就是极其痛苦的配环境，最后环境没弄成，这本书就吃灰了。

后来听人说Sedgewick的课比书好，我就去看课，看完就用C++尝试把示例代码重构了。但是有一整章的代码我都重构失败了，就是图算法。这本书绝大多数的代码都依赖于作者自己搓的标准库中的API，这就导致图算法重构的时候源代码毫无参考性，你就只能去诸如OI wiki的地方寻找。我严重怀疑这个所谓的“抽象数据结构”的思想给国内诸如严蔚敏《数据结构》一类的差评如潮的教材开了个坏头。如果我都无法将你的算法思维进行有效的迁移，那你这个课又有什么用呢？

有！确切来讲是另一种意义上的。这门课会告诉你专业人士是怎么研究算法的。而且这个课很“新”。2007年Sedgewick将Red-Black BST进行了简化，变成了LLRB-BST，2012年，这个研究就被写入了教材。某种意义上这门课程给了你一种“这个算法牛逼吗？我发明的！”的一种震撼。

于你而言这门课其实只需要看四个地方：开头的并查集优化，快速排序在大量重复关键字下的优化，左斜红黑树和3-Way Trie。这几个算法各有特色，而且有Sedgewick教授的原创成分。相信我，当你看见demo中的红黑树就像被赋予生命了一样自动平衡的时候你会发自内心大吼一句“卧槽”的。