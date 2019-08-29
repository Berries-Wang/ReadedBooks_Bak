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


