# Jdk命令行工具&可视化工具
## jps （Jvm process Status Tool） 显示指定系统内所有的HotSpot虚拟机**进程**
### 使用方式
+ jps [ options ] [ hostid ]
  - options: 选项
  - hostid: RMI注册表中注册的主机名
+ 输出：正在运行的虚拟机**进程**
   - 进程的本地虚拟机唯一ID(Local Virtual Machine Identifier.LVMID)，对于本地虚拟机进程来说，LVMID **等于** PID
   - 虚拟机执行主类(Main Class .main方法所在的类)
+ 选项  

|选项|作用|
|---|---|
|-q|**仅**输出LVMID，省略类的名称|
|-m|输出虚拟机进程启动时传递给主类main()方法的参数|
|-l|输出主类的全名，如果进程执行的jar包，输出jar路径|
|-v|输出虚拟机进程启动的jvm参数|

### 原理
+ 当java进程启动，会在System.getProperties("java.io.tmpdir);(在Linux中为/tmp/hsperfdata_{userName}/)下生成文件。文件名就是java进程的PID.至于类名、JVM参数等都可以通过解析这个文件来获取
## jstat(JVM Statics Monitoring Tool)虚拟机统计信息监视工具
+ 用于监视虚拟机各种运行状态信息的命令行工具。可以显示本地或者远程虚拟机进程中的类加载、内存、垃圾收集、JIT编译等运行数据
+ 格式： jstat [ option lvmid [ interval [s|ms] [ count ]]]
   - lvmid 虚拟机进程ID
   - interval:查询间隔
   - count:查询数量
#### option
+ 类装载
  - -class 
    + 输出:Loaded、Bytes、Unloaded、Bytes、Time
    + 解释:已加载Class数量、所占空间大小、未加载Class数量、所占空间大小、时间
+ 垃圾收集
  - -gc
+ 运行期编译状况
## 
##