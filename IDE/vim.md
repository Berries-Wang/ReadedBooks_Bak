# Vim 编辑器
## Vi
+ vi 即vim前身
+ Vim = Vi + IMproved
### 相比于Vi的，更高级的功能
+ 多行撤销
+ 语法加亮和自动补全
+ 支持多种插件(通过vimrc配置)
+ 通过网络协议（HTTP/SSH）编辑文件
+ 多文件编辑
+ 编辑压缩格式文件(zip , gzip )
## vimrc
+ rc(RUN Command)
+ 系统级vimrc与用户级vimrc
+ vimrc文件每一行都代表一个命令
### vimrc的使用
+ 查看版本  ：version
+ 编辑vimrc文件  ：e  ~/.vimrc
+ 注释  双引号引号(")
### 编辑vimrc文件，定制更高级功能
除了在vimrc文件中设置，在命令行中也可以设置(例如:set number 设置行号)
+ 在命令号模式下，:set number?(注意，是这个问号) 会返回这个功能的状态是什么
+ 关闭功能  在option前面加no，例如关闭行号显示 set nonumber
+ set history  保存命令行中的历史记录，向上向下查看历史
+ set ruler 光标的位置（vim 右下显示的信息 第几列第几行）
+ set hlsearch 查找的时候，匹配的值高亮显示（敲了回车才高亮显示）
+ set incsearch  查找的时候，匹配的值高亮显示(边输入，匹配的值就高亮显示 。只有第一个才会边输入边高亮)
+ set ignorecase  查找时忽略大小写
+ set number 显示行号
+ set autoindent 复制上一行的缩进到下一行
+ set smartindent 
+ map &lt;F3> i&lt;ul>&lt;CR>&lt;Space>&lt;Space>&lt;li>&lt;/li>&lt;CR>&lt;Esc>I&lt;/ul>&lt;Esc>kcit 
  - map 即 定制快捷键。如上 定义了一个快捷键F3.**F3后面就是一系列的操作** 首先 i,进入插入模式，在输入&lt;ul&gt;在按回车(CR)........
  - 即:在默认模式下按F3就是输出：
```html
<ul>
   <li></li>
</ul>
```
+ let mapleader=","  赋值操作 
+ map &lt;leader&gt;w :w!<CR> 配合let mapleader="," 则在普通模式下，输入逗号(,)及w就可以对文档进行保存了。 &lt;leader&gt;就是一个前缀，输入命令时要加这个前缀然后是&lt;leader&gt;后面的指令（自定义的，这里定义的是w）.这个&lt;leader&gt;的是可以配置的，在脚本里面这样写，let mapleader=','，然后下次你输入,w就执行命令了(这里是w!)。
### 删除、复制、粘贴 
windows中与vim中的区别：
<div><img src = "./pics/vim_d_c_c.jpg" style="text-align:center" alt="复制、粘贴、删除"/></div>
+ 在vim中，复制、粘贴、删除都是使用操作的首字母

#### Vim模式
<div><img src = "./pics/vim_mode.jpg" style="text-align:center" alt="模式"/></div>

##### 普通
   vim filename 打开文件后的模式
##### 可视
|---|---|
|---|---|
|v|字符选择，会将光标经过的地方反白选择|
|V|行选择，会将光标经过的行进行反白选择|
|[Ctrl] + v|块选择，可以用**长方形**的方式选择数据|
|y|将反白的地方复制|
|d|将反白的地方删除|
`对一整块区域操作，例如可以用来进行多行注释`
##### 插入
  在普通模式下按i进入的模式
##### 命令
   即 :register
#### vim特性
##### 寄存器
|类型|含义|表示方式|举例|特点|
|---|---|---|---|---|
|无名寄存器|默认寄存器|“”|“” p=p|会被最后一条覆盖|
|数字寄存器|"+{0~9}缓存最近10次操作|"0 "{1~9}|"0P "1P|0用于复制专用，1～9用于最近9次行删除或者修改|
|有名寄存器|26英文字母命名有名寄存器|”[a-z]/[A-Z]|"ayw|"A会通过^J追加到"a寄存器中|
|黑洞寄存器|有去无回|"_|"_dw|只想删除而不想覆盖无名寄存器|

+ 如 "1yy(普通模式连续输入),那么就会将内容复制到寄存器1中。再“1p(连续输入)，那么就会将寄存器1中的内容粘贴。
+ 如 "ayw(连续输入)，会将光标所在的单词复制到有名寄存器a中。"ap(连续输入)就会将有名寄存器a中的内容粘贴出来
##### 

## 快捷键
+ shift + i 插入模式，且回到行首
+ A  回到行尾

## vimrc文件设置
+ set showcmd
  - 命令模式下，在底部显示，当前键入的指令。比如，键入的指令是2y3d，那么底部就会显示2y3，当键入d的时候，操作完成，显示消失。