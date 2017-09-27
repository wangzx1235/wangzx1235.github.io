#CGLIB简介、原理与应用 


CGLIB介绍与原理(部分节选自网络)

一、什么是CGLIB?

CGLIB是一个功能强大，高性能的代码生成包。它为没有实现接口的类提供代理，为JDK的动态代理提供了很好的补充。通常可以使用Java的动态代理创建代理，但当要代理的类没有实现接口或者为了更好的性能，CGLIB是一个好的选择。

关于Java动态代理，请参见我的另一篇文章：Java动态代理详解 http://shensy.iteye.com/blog/1698197

二、CGLIB原理

CGLIB原理：动态生成一个要代理类的子类，子类重写要代理的类的所有不是final的方法。在子类中采用方法拦截的技术拦截所有父类方法的调用，顺势织入横切逻辑。它比使用java反射的JDK动态代理要快。

CGLIB底层：使用字节码处理框架ASM，来转换字节码并生成新的类。不鼓励直接使用ASM，因为它要求你必须对JVM内部结构包括class文件的格式和指令集都很熟悉。

CGLIB缺点：对于final方法，无法进行代理。

三、CGLIB的应用

广泛的被许多AOP的框架使用，例如Spring AOP和dynaop。Hibernate使用CGLIB来代理单端single-ended(多对一和一对一)关联。

四、CGLIB的API

1、Jar包：

cglib-nodep-2.2.jar：使用nodep包不需要关联asm的jar包,jar包内部包含asm的类.

cglib-2.2.jar：使用此jar包需要关联asm的jar包,否则运行时报错.

2、CGLIB类库：

由于基本代码很少，学起来有一定的困难，主要是缺少文档和示例，这也是CGLIB的一个不足之处。

本系列使用的CGLIB版本是2.2。

net.sf.cglib.core:底层字节码处理类，他们大部分与ASM有关系。

net.sf.cglib.transform:编译期或运行期类和类文件的转换

net.sf.cglib.proxy:实现创建代理和方法拦截器的类

net.sf.cglib.reflect:实现快速反射和C#风格代理的类

net.sf.cglib.util:集合排序等工具类

net.sf.cglib.beans:JavaBean相关的工具类
