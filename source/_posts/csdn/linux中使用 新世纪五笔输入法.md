---
title: linux 中 使用 新世纪五笔输入法
date: 2015-03-04 10:51:11
tags: linux 五笔
---

正如新世纪五笔输入法在windows 下是收费的情况是一样的，
我们大linux 下没有一个可以让我们轻松使用的新世纪五笔输入法，
可以方便使用的只有我们的86版的五笔输入法，不过我是用的新世纪输入 ，
。。。。。。我又在扯了！！！
进入正题：
	--你人安上ibus-rime 输入法 
		以前用Fitcx -rime 切到英文的时候是全角，怎么切都回不来，
		这次就用了ibus 现在用着爽着呢
		

```
sudo apt-get install ibus-rime 
```

然后下载 
rime 的新世纪五笔的配置文件与码表，
http://download.csdn.net/detail/pioneerlinzi/9419943
下一步就是打文件 放到

```
~/.config/ibus/rime
```
就行了，不要放了重新部署！

