# polyfill & shim

`javascript`, `browser`, 

在JavaScript的世界里,有两个词经常被提到,shim和polyfill.它们指的都是什么,又有什么区别?

一个shim是一个库,它将一个新的API引入到一个旧的环境中,而且仅靠旧环境中已有的手段实现

一个polyfill就是一个用在浏览器API上的shim.我们通常的做法是先检查当前浏览器是否支持某个API,如果不支持的话就加载对应的polyfill.然后新旧浏览器就都可以使用这个API了.

术语polyfill来自于一个家装产品Polyfilla:Polyfilla是一个英国产品,在美国称之为Spackling Paste(译者注:刮墙的,在中国称为腻子).记住这一点就行:把旧的浏览器想象成为一面有了裂缝的墙.这些[polyfills]会帮助我们把这面墙的裂缝抹平,还我们一个更好的光滑的墙壁(浏览器)

Paul Irish发布过一个Polyfills的总结页面“HTML5 Cross Browser Polyfills”.es5-shim是一个shim(而不是polyfill)的例子,它在ECMAScript 3的引擎上实现了ECMAScript 5的新特性,而且在Node.js上和在浏览器上有完全相同的表现(译者注:因为它能在Node.js上使用,不光浏览器上,所以它不是polyfill).


# IoC

控制反转（Inversion of Control，英文缩写为IoC）是框架的重要特征，并非面向对象编程的专用术语。它与依赖注入（Dependency Injection，简称DI）和依赖查找（Dependency Lookup）并没有关系。

IoC可以认为是一种全新的设计模式，但是理论和时间成熟相对较晚，并没有包含在GoF中。


# VCL

Visual Component Library的缩写（可视组件库）VCL是Visual Component Library的缩写，即可视组件库，它是Delphi,C++Builder等编程语言的基本类库。

它拥有封装纯粹，可扩展性强，操作方便等特点。如果是一个非常繁杂的Win32API，在经过VCL封装后，使用也是非常简便的。VCL支持类的嵌套，过程及函数的嵌套，如果你想在一个过程里声明一个类，或是声明另一个过程，那是完全可行的。过程内部的过程或是函数被称为局部过程或是局部函数。
