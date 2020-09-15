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

```wiki
以https://zh.wikipedia.org:443/w/index.php?title=Special:随机页面爲例, 其中：
https，是协议；
zh.wikipedia.org，是Host；
443，是Port；
/w/index.php，是Path；
?title=Special:随机页面，是Query。
```

# 正确的对待URL

在编程中，URL不是字符串（String），它是一个对象。处理一个对象时，要使用对象提供的方法，或者对象相关的工具。

## 关于解析

URL中，关键字或者敏感字符是需要被Encoding的。因为这些字符涉及到URL各部分的解析判断，比如一个URL中出现了两个问号（？），怎么才能确定哪一个问号后面才是Query呢？很明显，没法确定。所以URL有一套转码方法将容易引起误会的值转成特定排列的文字。

### Query

query中的内容一般来说是要被转码的。这是最保险的，你无法知道什么时候会有一个叫做url=xxx的参数被扔进来，恰好这个url还是一个极为完整的url。解析时，解析器会问你在玩植物嫁接吗。

## 关于约定

前后端或者生产者和消费者在通过URL交换信息时，要明确哪些部分代表什么含义；处理URL时要正确、准确的处理对应的部分。

> 当然在你确定一个约定的时候，你正确的规定转码与解析。

## 例子

假设现在我们有一个universal link的约定：`https://www.unko.fun/universal-link/{link}`。

我们规定link部分会被解析为一个deeplink的path部分。

那么问题来了。如果这个universal link带上了query，形如`https://www.unko.fun/universal-link/home?scrollTo=menu`，那这个query部分是属于universal link还是deeplink呢？

如果我们把它归到deeplink，那这个universal link实际上就失去了query的部分。

如果是deeplink真的需要这个query，那么将`{link}`部分转码就好了。

所以把它归到universal link是最好的。

## 使用标准行为定义自己的URL的好处

一个项目如果非常短，那怎么折腾都可以，反正也不需要维护。

但项目生命周期长到需要维护旧代码，那么不管开发人员是否会变动，都会有一个规范的需求。使用标准行为的好处在于新来一个人可以快速的融入项目进行开发，而不需要确认是否有坑。如果不换人，在查找问题时，标准行为在互联网上也能很快找到解决方案。





