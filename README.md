althttpd
SQLite 作者最新开源的 Web 服务器 althttpd，可以先来看下这个项目的时间线。
可以看出来开源工作是最近才开始的，但是实际上 althttpd 从 2004 年开始就在支撑 https://sqlite.org/ 网站的运行，althttpd 的设计目标就是为了简单、安全同时低资源消耗。
在 2018 年，http://sqlite.org 每天要响应 50 万的 HTTP 请求，而只用了价值 40 美金的服务器，而且服务器处于很低的负载（0.1 或者 0.2），可以看出其性能还是不错的。
我们来看下 althttpd 的代码，项目实际只有一个 c 文件，整体行数也不多，是一个非常不错的学习项目。
从 althttpd 的设计哲学可以看出来，作者是一个很克制的人，并不是希望去做一个功能非常丰富的 Web 服务器，而是希望 althttpd 在满足功能要求的前提下，能够尽量保持代码的简洁。
https://sqlite.org/althttpd/doc/trunk/althttpd.md

Source Code
The complete source code for althttpd is contained within a single C-code file with no dependences outside of the standard C library. The source code file is named "althttpd.c". To build and install althttpd, run the following command:

 gcc -Os -o /usr/bin/althttpd althttpd.c
The althttpd source code is heavily commented and accessible. It should be relatively easy to customize for specialized needs.

To build althttpd with built-in TLS support using libssl:

gcc -Os -o /usr/bin/althttpd -fPIC -DENABLE_TLS \
althttpd.c -lssl -lcrypto

Use：
althttpd -root $PWD/www/ -port 8088 -user bb