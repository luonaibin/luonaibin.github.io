---
layout:     post
title:      "Java知识"
date:       2017-05-04
---

<style type="text/css">
p{
	text-indent: 2em;
}
.post img {
  margin-bottom: 0rem;
}
</style>

## Class.forName 与 ClassLoader.loadClass区别

* Class.forName和ClassLoader.loadClass咋一看作用都一样，都是把类加载进来。

* 但是实际上他们是有区别的。

* 第一，ClassLoader.loadClass可以显式指定装载class的ClassLoader，但是Class.forName就不行了，他会默认使用调用类的ClassLoader来装载class。

* 第二，ClassLoader.loadClass仅仅加载class进来，但是不会初始化类，而Class.forName不仅会加载class而且还会初始化类。我们可以做个试验。

    package levi;  
      
    public class TestClassLoader {  
             
            public static void main(String [] args) throws ClassNotFoundException{  
                   Class c = Class.forName( "levi.TestClassLoader$UnderTestClass1" );  
                    
                  TestClassLoader. class.getClassLoader().loadClass("levi.TestClassLoader$UnderTestClass2" );  
           }  
             
            public static class UnderTestClass1{  
                   public static String testStr;  
                    
                   static {  
                          testStr = "test1" ;  
                         System. out.println(testStr );  
                  }  
           }  
             
            public static class UnderTestClass2{  
                   public static String testStr;  
                    
                   static {  
                          testStr = "test2" ;  
                         System. out.println(testStr );  
                  }  
           }  
      
    }  

>这段代码运行后，执行结果是只输出了test1而没有test2，说明Class.forName事实上还做了初始化的工作。