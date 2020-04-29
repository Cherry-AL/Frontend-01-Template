# week-03
找出 JavaScript 标准里所有的对象，分析有哪些对象是我们无法实现出来的，这些对象都有哪些特性？

    JavaScript中几个特殊的对象：

    1）window对象：
        在全局作用域中声明的变量、函数都是window对象的属性和方法。

    2）this对象：
        this对象是在运行时基于函数的执行环境绑定的：在全局函数中，this等于window；当函数被作为某个对象的方法调用时，this等于那个对象。
        特别注意：匿名函数的执行环境具有全局性，因此匿名函数中的this对象通常指向window对象!!!

           例子1：
            var name = "the window";
       var obj = {
           name : "my object",
           getName : function(){
               return function(){
                   return this.name;
               }
           }
       };
       var nameValue = obj.getName()();
       alert(nameValue);       // the window

       解析：
                var nameValue = obj.getName()();     即：
                var nameValue = function(){
                    return this.name;
                }();
       注意：匿名函数function(){return this.name;}的执行环境具有全局性，故匿名函数中的this对象指向window对象

       例子2：
            var name = "the window";
       var obj = {
           name : "my object",
           getName : function(){
               // 把匿名函数的外部(函数)作用域中的this对象保存在一个闭包能够访问到的变量里。
               var that = this;
               return function(){
                   return that.name;
               }
           }
       };
       var nameValue = obj.getName()();
       alert(nameValue);       // my object

       解析：
                var nameValue = obj.getName()();     即：
                var nameValue = function(){
                    return that.name;
                }();
       说明：that不是关键字，只是一个普通的变量。闭包访问变量的顺序：闭包中的局部变量、外部函数的局部变量、全局变量！！！


    3）Global对象：
        1)所有在全局作用域内定义的属性和方法，都是Global对象的属性。
        2)Global对象不能直接使用，也不能用new运算符创建。
        3)Global对象在JavaScript引擎被初始化时创建，并初始化其方法和属性。
        4)浏览器把Global对象作为window对象的一部分实现了，因此，所有的全局属性和函数都是window对象的属性和方法。

        Global对象的属性；
            Object      构造函数Object
       Function    构造函数Function
       Date        构造函数Date
       Array       构造函数Array
       RegExp      构造函数RegExp
       Error       构造函数Error
       String      构造函数String
       Boolean     构造函数Boolean
       Number      构造函数Number

       undefined   特殊值undefined
       NaN         特殊值NaN

       Global对象的方法：

            encodeURI()：
                1)对整个URI进行编码。
                2)只对空格进行编码，不会对冒号、正斜杠、问号、井号等进行编码。
                3)编码后的结果：除了空格被替换成了%20之外，其它的都没有发生变化。
                4)对应的解码方法：decodeURI()

       encodeURIComponent()：
                1)对部分URI(指除去协议、主机地址、端口后的部分)进行编码。
                2)对任何非标准字符进行编码。
                3)对应的解码方法：decodeURIComponent()

       URI编码方法说明：
                1)有效的URI中不能包含某些字符(例如：空格等)。
                2)用特殊的UTF-8编码替换所有无效的字符，从而让浏览器能够接受和理解。

            eval()：当解析器发现代码中调用eval()方法时，它会将传入的参数当作实际的JavaScript语句来解析。