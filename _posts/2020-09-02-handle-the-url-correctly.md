---
layout: post
title: 正确的处理URL
date: 2020-09-02 23:55 +0800
---

# URL的定义

[RFC 1738](https://tools.ietf.org/html/rfc1738)是URL的定义，里面明确规定了URL的结构以及意义。

## URL的结构

![URL的语法图](https://en.wikipedia.org/wiki/File:URI_syntax_diagram.svg)

可以看到，scheme和path是必须要有的，其它的部分是附件是可选的。

举例子。。。什么部分大概代表什么

# 正确的对待URL

在编程中，URL不是字符串（String），它是一个对象。处理一个对象时，要使用对象提供的方法，或者对象相关的工具。

## 关于约定

前后端或者生产者和消费者在通过URL交换信息时，要明确哪些部分代表什么含义；处理URL时要正确、准确的处理对应的部分。

举例子。。。

## 关于解析

注意Encoding

举例子