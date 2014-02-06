---
layout: post
title: 字符串匹配的Boyer-Moore算法
category : lessons
tagline: "转载"
tags : [字符串, Boyer-Moore]
---
原作者：[阮一峰](http://www.ruanyifeng.com/blog/2013/05/boyer-moore_string_search_algorithm.html)

上一篇文章，我介绍了KMP算法。但是，它并不是效率最高的算法，实际采用并不多。各种文本编辑器的"查找"功能（Ctrl+F），大多采用Boyer-Moore算法。

Boyer-Moore算法不仅效率高，而且构思巧妙，容易理解。1977年，德克萨斯大学的Robert S. Boyer教授和J Strother Moore教授发明了这种算法。

下面，我根据Moore教授自己的例子来解释这种算法。

![Alt text](/images/20130505/1.png)

假定字符串为"HERE IS A SIMPLE EXAMPLE"，搜索词为"EXAMPLE"。

![Alt text](/images/20130505/2.png)

首先，"字符串"与"搜索词"头部对齐，从尾部开始比较。

这是一个很聪明的想法，因为如果尾部字符不匹配，那么只要一次比较，就可以知道前7个字符（整体上）肯定不是要找的结果。

我们看到，"S"与"E"不匹配。这时，__"S"就被称为"坏字符"（bad character），即不匹配的字符。__我们还发现，"S"不包含在搜索词"EXAMPLE"之中，这意味着可以把搜索词直接移到"S"的后一位。
