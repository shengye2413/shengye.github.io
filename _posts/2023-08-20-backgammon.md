---
layout: post
title: 五子棋字符版
categories: Essays
tags:
- 项目
date: 2023-08-20 14:00 +0000
---
# 五子棋字符版

## 概述

​	本项目实现了一个简单的命令行版两人五子棋游戏。玩家在16x16的棋盘上轮流下棋,先连成五子的一方获胜。

## 开发环境

​	**vscode，ubuntu**

## 游戏流程

1. 初始化棋盘

   定义一个字符型的16x16的字符数组，数组全赋值为-方便观看，这个数组用来建立一个16x16的表格当作棋盘，棋子只能下在棋盘里，下棋下在对应的坐标里。

2. 接收玩家输入位置

   读取输入，把输入当作坐标，坐标位置的字符变为下子者所使用的字符。定义一个整数，保存下子个数，个数为偶数的为A，为奇数的为B。

3. 检查胜负

   遍历整个棋盘，当寻找到对应的棋子时开始判断。

   1.分别定义两个整数计数A和B的相连棋子个数，为了方便之后的调用，定义在主函数中。

   2.判读棋子之后的横向棋子是否相等，相等计数等于相连棋子数，不相等计数清零。

   3.当计数达到5时，判定为胜利，计数不为零则返回计数位。不为5时计数位为0

4. 打印棋盘

   1.当程序开始时，清空屏幕，打印空棋盘。

   2.输出横纵坐标方便描述。

   3.判断游戏是否结束，未结束接受输入，然后清空屏幕，再次打印新的棋盘排列。

5. 重复2-5直至游戏结束

## 功能模块

主要分为以下几个模块:

- 主程序:main.c
  - 初始化棋盘
  - 获取玩家输入
  - 调用判断胜负的函数
  - 打印棋盘
- 棋盘操作:sheet.c
  - 创建棋盘
  - 打印棋盘
  - 判断玩家是否获胜
- 描述棋盘操作的头文件:sheet.h

## 数据结构

使用二维字符数组sheet[16][16]表示棋盘,空格用'-'表示,玩家A用'O'表示,玩家B用'X'表示。

## 主要函数

- create_sheet:初始化棋盘为16*16的空格

- put_sheet:输入棋子，奇偶分别代表不同棋子

- check_win:打印当前棋盘,判断胜负

- AWin:判断A方是否获胜

- BWin:判断B方是否获胜

  1. create_sheet函数:

  初始化棋盘,用 '-' 填充16x16的二维字符数组,表示为空棋格。

![start](https://github.com/shengye2413/shengyeproject/blob/main/backgammon/start.png?raw=true)
  调用示例:

  ```c
  char sheet[16][16];
  create_sheet(sheet); // 初始化棋盘
  ```

  2. put_sheet函数:

     输入棋子，奇偶分别代表不同棋子

![game](https://github.com/shengye2413/shengyeproject/blob/main/backgammon/game.png?raw=true)

     调用示例:

     ```c
     put_sheet(sheet,a,b,number); // 输入棋子
     ```

  3. check_win函数:

  打印当前棋盘状态,判断游戏是否结束,有胜负结果或者是平局。  

  调用示例:

  ```c
  check_win(A_count, B_count, number, sheet); 
  ```

  3. AWin函数:

  检查A方是否已经获胜,即是否已经连成5子。返回连子数。

![end](https://github.com/shengye2413/shengyeproject/blob/main/backgammon/end.png?raw=true)
  调用示例:

  ```c
  int A_count = AWin(sheet, A_count);
  ```

  4. BWin函数:

  检查B方是否已经获胜,类似于AWin。

  

  5. main函数:

  主程序,实现游戏主循环逻辑。

  

  6. print_sheet函数:

  用于打印当前的棋盘状态。

