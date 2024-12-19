---
title: "nmap"
date: 2024-12-19T21:25:05+08:00
draft: false
---

### nmap

```bash
nmap -sP [IP]
```
主机存活检测
```bash
nmap -p T:1-65535,U:1-65535 -sS -sU [IP]
```
主机全端口扫描
```bash
nmap -sV -O [IP]
```
主机程序版本和操作系统侦测
```bash
nmap -p 80 -sS [IP]
```
对主机80端口进行TCP SYN扫描。nmap向目标端口发送TCP SYN报文，如果目标机返回TCP SYN+ACK报文，则说明目标端口处于开放状态，同时nmap会紧接着向目标机发送TCP RST报文以重置此连接；如果目标机返回TCP RST+ACK报文，则说明目标端口处于关闭状态。
```bash
nmap -p 80 -sT [IP]
```
对主机进行TCP connect扫描。nmap向目标端口发送TCP SYN报文，如果目标机返回TCP SYN+ACK报文，则说明目标端口处于开放状态，同时nmap会紧接着向目标机依次发送TCP ACK、TCP RST+ACK完成三次握手和重置此连接；如果目标机返回TCP RST+ACK报文，则说明目标端口处于关闭状态。
```bash
nmap -p 80 -sA [IP]
```
对目标主机进行TCP ACK扫描。nmap向目标端口发送TCP ACK报文，无论目标端口是否处于开放状态，目标机都会返回TCP RST报文。如果nmap主机能收到此TCP RST报文，则说明目标端口未被防火墙屏蔽。TCP ACK扫描只能用于确定防火墙是否屏蔽某个端口，可以辅助TCP SYN的方式来判断目标主机防火墙的状况。
