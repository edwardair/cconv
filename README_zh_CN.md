# 简介 #

由于现行的简繁转换工具中，大数只是支持单字之间的一一对应转换，即使像word这样的工具中，有一些简单的转换功能，但效果也不是很想理。

cconv正致力于解决这样的问题。

cconv的用法与iconv相关，对于不太了解iconv的朋友，可以先看看
http://www.gnu.org/software/libiconv/documentation/libiconv/iconv.1.html


# 安装 #
到 http://code.google.com/p/cconv/downloads/list 下载最新的源代码文件
```
$tar zxvf cconv-x.x.x.tar.gz
$cd cconv-x.x.x
$ ./configure --prefix=/usr/local
$ make
$ make install
```

# 使用 #
```
$ echo "美发现号航天飞机, 上头发奖金；头发应该剪了，后天，皇后" | cconv -f utf-8 -t utf8-tw
美發現號航天飛機, 上頭發獎金；頭髮應該剪了，後天，皇后

```

# php扩展模块的安装 #
值得注意的是. php扩展模块依赖于二进制版本的动态链接库，若安装扩展模块，请先安装二进制版本, 确认ldconfig -p能够找到libcconv.so 以及cconv.h头文件能被找到.
```
$tar zxvf cconv-php-x.x.x.tar.gz
$cd cconv-php-x.x.x
$phpize
$./configure
$make
$sudo make install

在php.ini中增加一行:
extension=cconv.so

<?php
$str = "干什么也比干等着要好\n这一只只是受了点轻伤，只不过这样而已\n";
echo cconv("utf-8", "utf8-tw", $str);
?>
output:
幹什麼也比乾等着要好
這一隻只是受了點輕傷，只不過這樣而已
```

目前还有一些词语对照表需要整理

对于扩展模块，现在只做了php的， 现在计划陆续推出python perl的。
只是没有太多精力花在支持windows方面,如有兴趣朋友愿意帮忙我将不胜感激。

我的msn：xiaoyjy@hotmail.com

cconv 的相关接口文档将在我的个人网站
http://www.yyyun.com/topics/cconv
中公布。