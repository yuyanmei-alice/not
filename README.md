# 笔记

# 第一章 ：java 开篇


主要是告知如何提问的技巧（尽量使用专业术语以及提供详细的资料以及截图说明)，以及遇到问题后如果通过网络去搜索解决方案


# 第二章：java初步

介绍java的来源以及发展以及语言优势，搭建java环境，能通过记事本完成编译、执行java代码，了解java API，了解注释、反编译工具的使用

java代码的执行过程：

java源程序 : .java 后缀 ；

通过编译javac命令，可得到该文件的字节码文件, .class文件

通过 java 文件名 会找到该字节码文件进行执行

**classpath**: 执行javac命令时，会默认从classpath下找到对应的class文件进行执行，如果未配置classpath路径，就默认在当前所在路径下查找class文件

**java_home**: 配置java jdk所在位置，后续启动tomcat时需要使用该路径

**path**: java提供的相关命令的路径
