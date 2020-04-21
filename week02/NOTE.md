# week-02总结
**4月16日**
语言按语法分类 


- 非形式语言
  中文，英文
    
- 形式语言（乔姆斯基谱系）

    0型：无限制文法
  
    1型：上下文相关文法
  
    2型：上下文无关文法
  
    3型：正则文法（可以用正则表达式）

产生式（BNF）
    
           *表示重复多次
           |表示或
           +表示至少一次
           
       eg：
       <number> = "0" | "1" | ....."9"
        十进制数 
       <decimaNumber> = "0"  |  (("1" | "2" |........|"9") <number> *)
       加法
       <Expression> = <decimaNumber> | <Expression> + <DecimaNumber> 
       乘法表达式
       <Expression> = <decimaNumber> | <Expression> * <DecimaNumber>       


​        
       四则运算：1+2*3
       终结符：number + * /
       非终结符：表达式
       
       js   以  2型为主
练习：尽可能寻找知道的计算机语言，尝试分类

####图灵完备性
- 命令式————图灵机
       
       - goto
       - if 和 while
   
- 声明式————lambda
       
       - 递归
   

动态与静态
      
      - 动态：
       在用户的设备/在线服务器上；
       产品实际运行时；
       runtime
     - 静态：
       在程序员的设备上；
       产品开发时；
       complitetime

类型系统

      动态类型系统和静态类型系统
      强类型和弱类型
         带有隐式转换的语言类型都是弱类型
      复合类型
         结构体
         函数签名
      子类型      
         逆变/协变


​         
**4月18日**
unicode  知识

     "郑".codePointAt(0).toString(16)
     "90d1"

词法 InoutElement
        
    WhiteSpace  <TAB>   
                <VT>   纵向制表符
                <FF>   formfeed
                <SP>   普通空格
                <NBSP>   no_break
                <ZWNBSP>  零宽空格  (zero width no_break)  (bit order mask)
                <USP>   unicode
    
    LineTermiantor <LF>  \r
                   <CR>  \n   回车
                   <LS>  超出unicode编码之外
                   <PS>  超出unicode编码之外
    Comment  //   /****/
    Token   identifierName
                      keywords
                      identifier
                      future reserved key            
            
            punctuator   
            leteral
                 number'    sign(符号位) exponent（11） fraction（52）
                 string    ascii   unicode ucs   gb iso-8859   big5
                 boolean   true false
                 undefined  全局变量名
                 null
                 symbol
                 object


总结：先从语言方面学习，分析语句的语法，了解了什么是非形式语言，形式语言的几个类型，了解js属于形式语言中的型，第二次课讲的是词法，包括unicode编码，ASCII编码，utf-8
前端语言如何编码，计算机是如何解析的。

            


​        