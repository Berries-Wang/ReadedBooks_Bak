# 读书笔记
+ 好好学习，天天向上

## 学习方式方法
### 学习方法
+ 自顶向下的学习方法
   - 场景(什么时候用) -> 用法(怎么用) -> 原理(为什么是这么用)

### 学习方式
1. 以问题为驱动
2. 以书本为驱动

### 学习来源
1. 书本，官方文档是最可靠的
2. 博客只能提供参考，不能全信，需要自己考证

### 源码如何分析？（探索阶段）
1. 了解当前学习的部分所涉及到的数据结构
2. 以相应的demo来进行探索源码
3. 例如：学习ThreadPoolExecutor
   + 首先 
       - 学习该类的成员属性，了解有哪些属性以及作用是什么。
       - 学习内部类，了解内部类的作用。如Worker
   + 其次，学习该类的构造方法。了解每个构造方法所带来的效果
   + 最后，编写demo。以某一个入口来进行对源码的探索
      - 如：通过线程池的submit方法来进行源码的分析