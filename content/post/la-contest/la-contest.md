---
title: "龙芯杯讲座笔记"
date: 2025-01-25T11:45:07+08:00
draft: false
tags: ["COA"]
---

## 龙芯杯介绍
龙芯杯：CPU设计相关  
第9届  
loongarch类似于RISC-V  

初赛：CPU+L1 cache  
决赛配SoC外设和PMON BIOS  
团队赛发平台  

三月开始报名，八月上旬交初赛作品，八月中旬提交决赛作品  
个人赛名额不限  

按照官方接口实现指令集的正确性与性能，完全客观评分  
决赛：启动相关设施  
半天时间接一条指令  

三等奖以上可进行加分  
2022年第一次接触loongarch架构  

## 个人赛经验分享  

个人赛：决赛100分，基准测试运行70%，编程任务30%  
纯粹的性能比拼
比较运行时间，只要运行时间足够短就行  
运行时间=指令数/每秒指令数  

提升IPC的思路：
普通运算CPI=1，乘法CPI=2，访存CPI=3  
条件分支需要分支预测相关  

CPU微架构设计决定了IPC  

编码技巧，流水级数的划分，布线质量和资源占用数  
设计简单，频率反而高  
FPGA芯片的体质可能不同  
有些部件的加入可能反而使性能下降  

面向测试程序进行设计  
内存复制，矩阵乘法，哈希算法  
观察发现程序1访存极其规律，矩阵乘法也比较规律，第三个程序访存就具有很大的随机性了  
乱序多发射性价比不高，提升主频是有效的  
程序2可能需要stride进行预取  

大量的时间花在了访存上，数据预取  
使用1bit BHT 或者 BTB也可  

有可挖掘的指令并行性，但是性价比不高  
实现指令cache很有必要  
实现分支预测器，写缓冲器的性价比较高  
实现数据预测器、数据cache和乱序多发射的性价比较低，不如考虑提升频率  

提升频率？在vivado的PLL IP中设置  
但是由于触发器有setup time，在下一个数据到来之前数据必须保持稳定的时间  

WNS：时钟周期与满足所需约束的差值，当WNS < 0时电路时序可能无法保证  
超频：只能说是最后的手段  

使用时序分析工具  
implementation -> Report timing summary  
列出路径，理解是从什么部件到什么部件的关键路径  
使用vivado对路径进行画图  

更合理地划分流水等级  
选择在哪里切一刀进行划分  

数据cache：IPC↑，BRAM资源占用↑  
数据预取：IPC↑，逻辑复杂，不利于超频  
乱序多发射：IPC↑，逻辑变复杂，不利于超频  

编码技巧：vivado user guide  
使用更加激进的综合实现策略，最终还能带来10-20MHz的性能提升  
个人赛的优化思路已经被挖的差不多了  

## 团队赛经验分享

特等奖：性能/功能重大创新  
一等奖：Linux+性能优秀  
二等奖：能跑操作系统  
三等奖：能跑测试程序  

CPU：超大工作量，SoC：大工作量，系统软件：中等工作量  
正确性保证，性能调优，丰富功能  

比较推荐Chisel和Spinal，面向功能写代码，上手难度低  
基于其它语言的HDL扩展玩具性质较强，不太方便使用  
乱序执行，多级流水线，分支预测，cache，TLB，MMU  

参考往年开源方案，参考香山处理器微架构文档  

CPU实现要点：简化设计  
前端和后端实现，模块化实现  
尽量保证不同模块之间是黑盒  
分支预测和cache可以和cpu分开开发  
浮点指令集等到启动Linux之后再做  

参考书目：  
计算机体系结构教材，超标量处理器设计，CPU设计实战  

流程：
开学前4人现在chiplab完成CPU设计实战的实验部分  
开学后两人完成CPU设计，完成乱序和超标量部分  
一人完成SoC，使用现成的CPU做  
一人完成分支预测，cache和系统适配等  

官方的trace太弱，很多问题测不出来  
三步走：确保在最小的SoC上运行Linux  
做出自己的SoC，支持更多外设  
丰富系统软件  
只有CPU强制要求自行实现  

SoC：使用vivado block design  
外设控制器，重视扩展I/O口  

软件系统部署：
PMON/u-boot，片上ROM/片外flash  
只需要加载Linux内核elf即可  
Linux内核：载入内存，正确配置设备树和驱动程序  
根文件系统：busybox，buildroot，移植libc等运行库  
应用软件：编译开源代码  
推荐方向：物联网，网络应用，游戏应用  
AI应用，发行版Linux中前者算力受限后者板载内存受限    
24年特等奖的GUI界面  

