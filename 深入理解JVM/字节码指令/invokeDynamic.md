## invokeDynamic字节码指令
#### Java方法的构成
1. 方法名
2. 方法签名--这里指的是:参数列表+返回值
3. 定义方法的类
4. 方法体(代码)
#### 方法的调用
一次方法的调用，除了需要方法的实体之外，还需要方法的调用者(caller，即方法调用语句所在的类),和方法的接收者(reciver,一个对象，如隐藏的this。即xxx.方法名();，xxx就是一个方法调用时的接收者)。
#### 从代码中看方法的构成和方法的调用的接收者&调用者    
```java
package link.bosswang.study;

import java.lang.invoke.MethodHandles;
import java.lang.invoke.MethodType;

public class MethodHandle {

    static class ClassA {
        private String name = "  Wang";

        public void println(String s) {
            System.out.println(s + this.name);
        }
    }

    public static void main(String[] args) throws Throwable {

        getPrintlnMH(System.out).invokeExact("System.out Hello World"); //System.out Hello World

        getPrintlnMH(new ClassA()).invokeExact("ClassA Hello World"); // ClassA Hello World  Wang

    }

    private static java.lang.invoke.MethodHandle getPrintlnMH(Object reveiver) throws NoSuchMethodException, IllegalAccessException {

        //获取方法描述符
        /**
         * 在这里，MethodType:代表“方法的类型”，包含了方法的返回值(methodType()第一个参数代表方法的返回值)
         * 和具体的参数(methodType()方法第二个以及之后的参数)
         */
        MethodType methodType = MethodType.methodType(void.class, String.class);

        /**
         * MethodHandles.lookup():代表调用者,也就是当前类。调用者决定有没有权限去调用该方法
         */
        MethodHandles.Lookup lookup = MethodHandles.lookup();

        /**
         *loopup.findVirtual()的三个参数分别代表:定义方法的类，方法名，签名(描述符)
         */
        java.lang.invoke.MethodHandle mh = lookup.findVirtual(reveiver.getClass(), "println", methodType);

        /**
         * 确定方法的接收者
         *
         * 因为这里调用的是一个虚方法，按照Java语言规则，方法第一个参数是隐式的，代表该方法的接收者，也就是this指向的对象。这个参数之前是放在参数列表中的，
         * 而现在提供了bindTo方法来完成这件事情
         */
        java.lang.invoke.MethodHandle methodHandle = mh.bindTo(reveiver);

        return methodHandle;
    }


}
```
+  其实，方法getPrintlnMH()中模拟了invokevirtual指令的执行过程

#### MethodHandle与Reflection的区别
1. Reflection和MethodHandle机制都是在模拟方法的调用，但是Reflection是模拟Java代码层次的方法调用，而MethodHandle是在模拟字节码层次的方法调用。MethodHandle.loop中的三个方法分别对应了不同字节码指令的执行权限校验行为。
   + MethodHandle.lookup().findStatic  对应 invokestatic
   + MethodHandle.lookup().findVirtual 对应 invokevirtual & invokeinterface
   + MethodHandle.lookup().findSpecial 对应 invokeSpecial 
2. Reflection中的java.lang.reflect.Method 对象远比MethodHandle机制中的java.lang.invoke.MethodHandle对象包含的信息多。Reflection包含了方法的签名，描述符，方法属性表中各种属性的Java端表示方法，包含了执行权限等的运行期信息。而MethodHandle仅仅包含了与执行该方法相关的信息。即：Reflection是重量级，MethodHandle是轻量级
3. 由于MethodHandle是对字节码的方法调用的模拟，所以理论上虚拟机在这方面做的各种优化，在MethodHandle上也应当可以采用类似思路去支持
4. Reflection仅仅是为了给Java使用，MethodHandle是可服务于所有运行于Java虚拟机之上的语言
#### invokeDynamic指令
+ 在某种程度上，invokeDynamic指令与MethodHandle机制的作用是一样的，都是为了解决原有4条**invokeXX**指令方法分派规则固化在虚拟机之中的问题，把如何查找目标方法的决定权从虚拟机转嫁到具体用户代码之中，让用户(包含其他语言的设计者)有更高的自由度。
+ 或者说这样来理解:为了达到同一个目的，一个采用上层Java代码和API来实现;另一个则是用字节码指令和Class中的其他属性、常量来完成。
##### invokeDynamic指令原理
+ 每一处由invokedynamic指令的位置都称为动态调用点，这条字节码指令的第一个参数不再是代表该方法符号引用的CONSTANT_Methodref_info常量，而是CONSTANT_InvokeDynamic_info常量。从这个常量中可以得到信息:
1. 引导方法(Bootstrap Mehthod ，BSM),此方法存放在新增的BootstrapMethods属性中。
    - 引导方法有固定的参数(是什么)，并且返回值是java.lang.invoke.CallSite对象，代表着真正要执行的目标方法调用。根据CONSTANT_InvokeDynamic_info常量提供的信息，虚拟机可以找到并执行引导方法，从而获得一个CallSite对象，最终调用要执行的方法。
2. 方法类型(MethodType)
3. 名称