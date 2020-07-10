# VIM


## 第一章 vi文本编辑器

### 常用命令
```vim
i
cw
:e!
:q!
ZZ
:!
C-Z -> fg

```

## 第二章 简单文本编辑
```vim
i
hjkl
+ 下一行第一个字符
- 上一行第一个字符
e/E 单词结尾
0$ HL
bwe
2h 3j 4k 5l
:set wm=10
:set nu
```

### 移动光标
```vim
w # 移动一个单词计算标点符号
W # 移动一个单词不计算标点符号

b
B

[n]b
[n]w

G
gg

C-o #TODO
C-i #TODO

,, + w 跳转
,, + fe 查找'e',快速跳转定位到某个字符位置
```
### 更改文本
```vim
cw # 从光标到这个单词的结尾
cc # 整行
c2b # 从光标往前两个单词
c$ （同 C)
ciw # 修改-删除整个单词-插入模式
c0

C # 修改(删除到行尾)


a
A

i
I

o
O

s
S # 修改(前删除整行)

r
R

,a=  # 按逗号对齐
cs"' # 双引号替换我单引号
```

### 多行操作修改单双引号
v 可视模式 :'<,'>norm $cs"'

### J合并多行

### 大小写

~          将光标下的字母改变大小写
3~         将光标位置开始的3个字母改变其大小写
g~~        改变当前行字母的大小写
U          将可视模式下选择的字母全改成大写字母
u          将可视模式下选择的字母全改成小写
gUU        将当前行的字母改成大写
guu        将当前行的字母全改成小写
3gUU      将从光标开始到下面3行字母改成大写
gUw       将光标下的单词改成大写。
guw       将光标下的单词改成小写。

vim中大小写转化的命令是
gu或者gU
形象一点的解释就是小u意味着转为小写；大U意味着转为大写.
剩下的就是对这两个命令的限定（限定操作的行，字母，单词）等等

1. 整篇文章大写转化为小写
打开文件后，无须进入命令行模式。键入:ggguG
解释一下：ggguG分作三段gg gu G
gg=光标到文件第一个字符
gu=把选定范围全部小写
G=到文件结束

2. 整篇文章小写转化ä¸º大写
打开文件后，无须进入命令行模式。键入:gggUG
解释一下：gggUG分作三段gg gU G
gg=光标到文件第一个字符
gU=把选定范围全部大写
G=到文件结束

3. 只转化某个单词
guw 、gue
gUw、gUe
这样，光标后面的单词便会进行大小写转换
想转换5个单词的命令如下：
gu5w、gu5e
gU5w、gU5e

4. 转换几行的大小写
将光标定位到想转换的行上，键入：1gU 从光标所在行 往下一行都进行小写到大写的转换
10gU，则进行11行小写到大写的转换
以此类推，就出现其他的大小写转换命令
gU0        ：从光标所在位置到行首，都变为大写
gU$        ：从光标所在位置到行尾，都变为大写
gUG        ：从光标所在位置到文章最后一个字符，都变为大写
gU1G    ：从光标所在位置到文章第一个字符，都变为大写

### 删除文本
dw
diw
db
d$
d0
dd
D = d$

### 粘贴
p
xp 对调字母

### 重复
.

### wm
:set wm=0

### 撤销
u

### 分屏
1. 分屏启动
vim -On file1 file2
vim -on file1 file2

2. 关闭分屏
Ctrl+w c 关闭当前
Ctrl+w q 关闭其他

3. 分屏
横分
Ctrl+w s
:sp filename

竖分
Ctrl+w v
:vsp filename

4. 移动光标
Ctrl+w [HJKL]

5. 屏幕尺寸
Ctrl+w [=+-]

### 宏
qa

开始录制

@a 执行

### 函数列表
F9

### 书签 vim-signature
m/ 打开列表 Open location list and display marks from current buffer.
m? Open location list and display markers from current buffer. Markers in the text tell where folds start and end.
mx add x
dmx delete x.
m. If no mark on line, place the next available mark. Otherwise, remove (first) existing mark. 这个可以避免手动安排大量 mark，但是有些常用 mark 还是形成习惯比较好。
m- Delete all marks from the current line
m<Space> Delete all marks from the current buffer.
m<BS> Remove all markers.
:SignatureToggle can be used to show/hide the signs.
:SignatureRefresh to refresh

### 最近打开
,f

### 查看历史
,h


## 第三章 快速移动

### 滚屏
Ctrl+F
Ctrl+B
Ctrl+D
Ctrl+U
Ctrl+E
Ctrl+Y

### z调整光标
z Enter
z.
z-
200z Enter

### 重画屏幕
Ctrl+L

### 屏幕中移动
H 到顶端
M 到中央
L 到底端
nH 到顶端往下n行
nL 到底端往上n行

### 根据文本块移动
e
E
(
)
{
}
[[
]]

### 根据搜索移动
,,w (k-vim)
,,fe (k-vim)
/
?向上搜索
n
N
/Enter
?Enter
:set nowrpascan # 只搜索光标位置之前的单词

### 通过搜索删除文本
d?move

### 自动索引目录
.~/Downloads/

### 当前行搜索
fx
Fx
tx
Tx
;分号继续
,
,,w
,,f

### 根据行号移动
```vim
^G
`` 回到原来的位置
'' 回到原来位置开头
```
#TODO 相对移动多少行

## 第四章 越过基础的藩篱

1. 命令行选项
```vim
+n file
+  file         # 最后一样打开file
+/pattern file  #
-c command file # NOTICE
-R
vi -r # 恢复缓冲区
ex -r
```
2. 缓冲区名称
```vim
"    # 缓冲区调用 "1p
1~9  # 最后9次删除操作的内容
a~z  # "a5dd 删除5行保存到缓冲去a，"ap 调取缓冲区a后粘贴
```
3. 缓冲区与标记命名
```vim
"b command      # 用缓冲区b执行命令
mx              # 将当前位置标记为x
'x              # 将光标移到标记x所在的行的第一个字符
`x              # 将光标移到用x标记的字符
``
''
```
4. 数字递增
Ctrl+a
Ctrl+x
:r !seq 1 100

## 第五章 ex编辑器概述
```vim
:.,$d
:20,.m$
:%t$
:-,+t0   # 当前行上一行、下一行复制到开头
:/pattern/d  # 删除包含pattern的行
```
## 第六章 全局替换
```vim
:%s/old/new/g
:g/pattern/s/old/new/g
```

## 第七章 高级编辑方法
```vim
:set all
:r !date
:sh  ->  Ctrl+D
```
### 用vi过滤文本
!命令

### 单词缩写
:ab 10c  cccccccccc   #定义10c 输入后显示cccccccccc
:unab 10c
:ab    # 显示所有缩写

### map
:map命令 定义编辑命令

:map x 更改按键操作

### @功能

### ctags

:!ctags file.c
:tags fun

## 第八章 vi同类品的功能总览

...
