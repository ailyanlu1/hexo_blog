title: "Install Mathjax for Hexo Blog"
tags:
  - hexo
date: 2014-10-16 23:24:02
catagories:
---
添加了一下[Mathjax插件](https://github.com/phoenixcw/hexo-renderer-mathjax)，添加方法里面的Readme已经说得很好了。虽然好像还是有些慢。准备有空再研究下[韩冬同学的](http://www.winterland.me/2013/12/hexo-mathjax/)
主要是后面机器学习方面的博客应该会写得很多吧……虽然Latex的写法还是有点不适应呢
[Latex参考](http://www.lsv.ens-cachan.fr/~markey/LaTeX/doc/Companion-chapter8.pdf)
$$
f\left(x\right) = \frac{1}{\sigma\sqrt{2\pi}}e^{-\frac{\left(x-\mu\right)^2}{2\sigma^2}}
$$

Mathjax和Markdown还是比较容易有冲突的，写公式的时候要注意：
- 下划线、空格前加上'\'
- 大括号之类的Markdown保留字需要这样写："\\\\{"
- ~符号不能用

另外Markdown本身要注意的点包括
- \*符之前记得加反斜杠
- 链接语法的链接url中不能有括号
- 每个列表后要空一行
