---
id: w5ej8rx5rn7c37yul52sm87
title: 1129 Nand2tetris
desc: ""
updated: 1670250677174
created: 1669691084582
---

## 前言

真的很想知道記憶體超頻那些數字到底是在調什麼... 第三章 Memory 有提到記憶體的運作方式，來看看能不能開竅...

絕對要配這個看:

[Nand2Tetris 慕課記 -- 從邏輯閘到方塊遊戲 by 陳鍾誠老師](https://programmermagazine.github.io/mag/ymag201506/book.html)

課程章節:

```
0. From Nand to Tetris
1. Boolean Functions
2. Boolean Arithmetic
3. Memory
4. Machine Language
5. Computer Architecture
6. Assembler
7. VM I: Stack Arithmetic
8. VM II: Program Control
9. High-Level Language Project
10. Compiler I: Syntax Analysis Project
11. Compiler II: Code Generation Project
12. Operating System
```

### 網路公開課 Build a Modern Computer from First Principles

就是這兩堂課:

![](/assets/images/2022-11-29-11-32-17.png)

- [Build a Modern Computer from First Principles: From Nand to Tetris (Project-Centered Course) by Shimon Schocken, Noam Nisan](https://www.coursera
- .org/learn/build-a-computer)

- [Build a Modern Computer from First Principles: Nand to Tetris Part II (project-centered course) by Shimon Schocken](https://www.coursera.org/learn/nand2tetris2)

### [Nand2tetris 網站](http://nand2tetris.org/)

![](/assets/images/2022-11-29-11-37-00.png)

> 可以前往下載講義/簡報/習題

## 我的筆記

### (x AND y)

x∧y

### (x OR y)

x∨y

### NOT(x)

¬x

### Commutative Laws

(x AND y) = (y AND x)  
(x OR y) = (y OR x)

### Associative Laws

(x AND (y AND z)) = ((x AND y) AND z))
(x OR (y OR z)) = ((x OR y) OR z))

### Distributive Laws

(x AND (y OR z)) = (x AND y) OR (x AND z)
(x OR (y AND z)) = (x OR y) AND (x OR z)

### De Morgan Laws

NOT(x AND y) = NOT(x) OR NOT(y)
NOT(x OR y) = NOT(x) AND NOT(y)

### 用來簡化看來很複雜的邏輯

![](/assets/images/2022-12-05-22-19-29.png)

### 邏輯表

總共有這幾種可能

![](/assets/images/2022-12-05-22-21-29.png)

其實遇到邏輯複雜的我都只是表列後一一寫下 QQ

簡化真的要另外花時間，感覺以後可以請 ChatGPT 幫我看一下能不能簡化。

![](/assets/images/2022-12-05-22-30-24.png)

> [NAND 元件具有全能性，也就是其它邏輯閘都可以由一群 NAND 所組合而成](https://programmermagazine.github.io/mag/ymag201506/book.html#nand2tetris-%E7%AC%AC-1-%E9%80%B1----%E5%B8%83%E6%9E%97%E5%87%BD%E6%95%B8)

## 小結
