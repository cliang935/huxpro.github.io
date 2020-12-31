---
layout: post
title: Vim命令记录
subtitle:
author: Liang Chen
date: 2020-08-21 18:00:00 +0800
tags: [Notes, Vim]
catalog: true
mathjax: true
---

<head>
    <script src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML" type="text/javascript"></script>
    <script type="text/x-mathjax-config">
        MathJax.Hub.Config({
            tex2jax: {
            skipTags: ['script', 'noscript', 'style', 'textarea', 'pre'],
            inlineMath: [['$','$']]
            }
        });
    </script>
</head>

# vi 常用命令  

## 01. 一般模式  

### 1.1 移动光标  

- `h`，`j`，`k`，`l`：上下左右移动一个字符  
- `Ctrl`+`f` ，`Ctrl`+`b` ，`Ctrl`+`d` ，`Ctrl`+`u`： 上下移动一页/半页  
- `n<space>`：例如 `20<space>` 则光标会向后面移动 20 个字符  
- `0`：移动到一行的最前面字符  
- `$`：移动到一行的最后面字符  
- `G`：移动到文件的最后一行  
- `nG`：例如`20G`则会移动到文件的第 20 行  
- `gg`：移动到文件的第一行  
- `n<Enter>`：向下移动 n 行  

### 1.2 复制粘贴删除  

- `X,x`：向前/后删除一个字符  
- `nx`：连续向后删除 n 个字符  
- `dd`：删除一行  
- `ndd`：例如`20dd`是删除 20 行  
- `d1G`：删除到第一行的所有数据  
- `dG`：删除到最后一行的所有数据  
- `d$`，`d0`：~  
- `yy`：复制该行  
- `nyy`：复制 n 行  
- `y1G`，`yG`：~  
- `y0`，`y$`：~  
- `p,P`：粘贴在下/上方  
- `u`：复原前一个动作【撤销】  
- `Ctrl`+`r`：重做前一个动作  
- `.`：重复前一个动作  

### 1.3 搜索替换  

- `Shift`+`*`: ...
- `/word`，`?word`：向光标之下/上寻找一个名称为 word 的字符串  
- `n,N`：如果刚刚执行 /vbird 去向下搜寻 vbird ，则按下 n 后，会向下继续搜寻下一个 vbird ；N 反向  
- `:n1,n2s/word1/word2/g`：在 100 到 200 行之间搜寻 vbird 并取代为 VBIRD 则`:100,200s/vbird/VBIRD/g`  
- `:%s/word1/word2/g`：从第一行到最后一行寻找 word1 字符串，并将该字符串取代为 word2   
- `:%s/word1/word2/gc`：在取代前显示提示字符给用户确认 (confirm) 是否需要取代！  

## 02. 编辑模式  

### 2.1 插入模式  

- `i`：在目前光标所在处输入  
- `I`：在目前所在行的第一个非空格符处开始输入  
- `a`：从目前光标所在的下一个字符处开始输入  
- `A`：从光标所在行的最后一个字符处开始输入  
- `o,O`：在目前光标所在的下/上一行处输入新的一行  

### 2.2  取代模式  

- `r`：取代光标所在的那一个字符一次  
- `R`：一直取代光标所在的文字，直到按下`ESC`为止  

## 03. 指令行模式  

### 3.1 储存离开等指令  

- `:w`：保存  
- `:wa`: ~
- `:w!`：强制写入  
- `:q`：离开
- `:qa`: ~
- `:q!`：强制离开不保存  
- `:wq`：~  
- `:w [filename]`：另存为  
- `:r [filename]`：将 [filename] 这个文件内容加到游标所在行后面  
- `:n1,n2 w [filename]`：将 n1 到 n2 行的内容保存为 [filename] 文件  
- `:! command`：暂时离开 vi 到指令行模式下执行 command 的显示结果！例如 [:! ls /home] 即可在 vi 当中察看 /home 底下以 ls 输出的档案信息！  

### 3.2 显示行号  

- `:set nu`：显示行号  
- `:set nonu`：取消行号  

- `:set hls`: 高亮显示
- `:set nohls`: 取消高亮

## 04 可视块模式  

- `Ctrl`+`v`：进入块选择模式  
- 批量注释：进入块选择模式，移动光标选中要注释的行，按`I`进入行首插入模式输入注释符号，按两下 `ESC`即可  

## 05 目录操作  

### 5.1 vim自带目录操作  

- `:E`：打开目录  
- `:Se`：水平窗口打开目录  
- `:Ve`：垂直窗口打开目录  

## 06 缓冲区操作  

>  感觉不常用，我自己不常用

- `:ls, :buffers`：列出所有缓冲区  
- `:bn[ext]`：下一个缓冲区  
- `:bp[revious]`：上一个缓冲区  
- `:b {number, expression}`：跳转到指定缓冲区，例如`b2`  
- `:b exa`：跳转到`example.txt`文件缓冲区  
- `:sb 3`：分屏并打开编号为3的Buffer  
- `:vertical sb 3`：同上，垂直分屏  

## 07 打开窗口  

- `:new`：~  
- `:vertical new`：垂直~  

## 08 标签操作  

>  感觉不常用，我自己不常用

- `:tabnew`：打开新的标签  
- `:tabnew file`：在新标签中打开文件  
- `:tabc`：关闭当前标签  
- `:tabo`：关闭除当前的其他标签  
- `:tabs`：列出所有标签  
- `:tabn`：切换下一个标签  
- `:tabp`：切换上一个标签  
- 标准模式下按下`g`+`t`：在标签间切换  

## 09 跨文件复制粘贴内容  

- 将被操作文件用标签打开，或者存入缓冲区，接下来的操作同文件内复制粘贴操作  

## 10 屏幕操作  

### 10.1 改变尺寸  

- `ctrl`+`w`+`=`：平均  
- `ctrl`+`w`+`+`：增大  
- `ctrl`+`w`+`-`：减小  

### 10.2 屏幕移动  

- `Ctrl`+`f`：往前滚动一整屏  
- `Ctrl`+`b`：往后滚动一整屏  
- `Ctrl`+`d`：往前滚动半屏  
- `Ctrl`+`u`：往后滚动半屏  
- `Ctrl`+`e`：往后滚动一行  
- `Ctrl`+`y`：往前滚动一行  
- `z`+`Enter`：将光标所在行移动到屏幕顶端  
- `z`+`.`：将光标所在行移动到屏幕中间  
- `z`+`-`：将光标所在行移动到屏幕低端  
 
## 录制操作

- `qa`：开始录制，操作保存到a buffer, `q`：退出录制, `n@a`：重复n次操作

## 不换行下一行多行显示

- `:set wrap`; `:set nowrap`

## 单词跳转

- `w e b`

## 光标跳转

- `H M L`

## 一行内查找字符

- `f F`
- `;`: 重复查找

## 修改单词

- `cw`
- `caw`: change a word then enter [insert] mode
- `c$ c^`
- `ci" ci( ci[`: change cotent in "" () or [] then enter [insert] mode
- `yi"`: copy cotent in "" 
- `ya"`: copy cotent in "" including ""
- `yw yaw dw daw`
