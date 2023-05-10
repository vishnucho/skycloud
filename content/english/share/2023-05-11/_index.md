---
title: "2023-05-11 隨機這件小事 - 魔鬼藏在細節裡"
description: "談論有關隨機的數學與程式碼閒聊"
categories: ["Tech"]
tags: ["Tech"]
---

# 隨機這件小事 - 魔鬼藏在細節裡

## 講者： Vishnu

## Ipod Shuffle 小故事

`有三組曲風ABC  shuffled:ABBBBACBACBBB`  
最初版本的 Shuffle 是數學上真正意義的隨機，但是使用者體感上感受到的是不隨機，因為人類的大腦是很容易找出規律的，常常會發現會有重複的歌曲順序或是接連許多首歌曲都是同一曲風的歌曲，這樣的使用者體驗是不好的。

`有三組曲風ABC  shuffled:ABACBACBCBABAB`  
Ipod 開發團隊並沒有向使用者教育，而是吸取使用者的感受量身設計關於曲目的隨機演算法，讓使用者體感上感受到的是隨機，例如：使用者會覺得每首歌曲都是不同曲風的歌曲，這樣的使用者體驗是好的。

> 開發團隊沒有義務與權利教育使用者，而必須良好的設計使用者體驗。

## Bias & Deviation 隨機偏誤與偏差

### Bias 偏誤

- 硬幣若正反出現機率不一致,意味著有**Bias 偏誤**
- 一個骰子若 1~6 點出現機率不一致,意味著有**Bias 偏誤**
- 可以用隨機性測試方法評斷一個亂數產生器是否有**Bias 偏誤**
  - 頻數測試
  - 遊程測試
  - 塊內最長連續「1」測試
  - 矩陣秩的測試
  - 非重疊模板匹配測試
  - 重疊模板匹配測試
  - 通用統計測試
  - 近似熵測試
  - 部分和測試
  - 隨機漫步變量測試

### Deviation 偏差

- 一個骰子骰 60 次,出現的次數與理想值 10 次之間的差距,每輪之間的會有**Deviation 偏差**
- 常以標準差作為參考指標
- 可以用統計方法計算出結果的統計量值

## Chaos - 混沌蝴蝶效應

> 一個細微的初始值差異可以造成巨大的結果差異

### 三體問題

![three-body](./shares/2023-05-11/imgs/three-body.gif)

### 混沌擺

![three-body](./shares/2023-05-11/imgs/swinging-sticks.webp)

### 雜湊函式

| 輸入       | MD5 Hash                         | SHA-1 Hash                               |
| ---------- | -------------------------------- | ---------------------------------------- |
| vishnu_cho | a2b34e90492ce05ab5d6a0b8bebe3e1e | 0e2c42bbc36389a9de7e6b696c6f2b68ff55d416 |
| vishnucho  | 0d79ed5a70748e4f1994a56339bb17ff | 90caae37cdaa5a72b4d65b7007105269467b4303 |
| 123456789  | 25f9e794323b453885f5181f1b624d0b | f7c3bc1d808e04732adf679965ccc34ca7ae3441 |
| 123456788  | f5f091a697cd91c4170cda38e81f4b1a | 6b63d2a490228d003c055c36430ba00666db7ff7 |

### 應用

使用雜湊函式來做到隨機的效果，例如： `hash("vishnu_cho") % 3`

根據雜湊函式的相同輸入會有相同輸出的特性, 可以用檔案正確性驗證，例如： `下載檔案後檢查 MD5 Hash 值是否相同`

根據雜湊函式的不對稱性，可用於公正性事前檢驗，例如：未來有機會再分享 [零知識證明](https://zh.wikipedia.org/wiki/%E9%9B%B6%E7%9F%A5%E8%AF%86%E8%AF%81%E6%98%8E)

## Pseudorandomness 偽隨機性

### 必較表

| 特點     | 偽隨機         | 真隨機   |
| -------- | -------------- | -------- |
| 產生方式 | 種子+演算法    | 自然現象 |
| 產生速度 | 快             | 慢       |
| 產生成本 | 低             | 高       |
| 產生結果 | 具有週期可重複 | 不可重複 |

一般來說我們使用的隨機數都是偽隨機，因為真隨機的產生方式是依靠自然現象，例如：熱噪訊號、量子力學的效應、放射性元素的衰退輻射...等，這些產生方式都是需要耗費大量的成本，所以我們一般使用的隨機數都是偽隨機。

### 但我們要如何增加偽隨機的隨機性呢?

選擇較優的種子來源，例如：精度是奈秒的時間單位，或是使用者的滑鼠移動軌跡...等。

選擇較優的演算法，其循環週期必須大於使用區間，例如：`rand() % 3`，若使用的是線性同餘法，其循環週期只有 2，所以不適合使用，但若使用的是 Mersenne Twister，其循環週期為 2^19937 - 1，所以適合使用。

參照文章：[隨機的浪漫 - 機率真的測不準還是命中注定?](https://www.forevergame.org/math/2023-01-13/)

## Golang Rand Package 原生套件討論

討論
| 套件 |函式| 生成邏輯 | 說明 |
| ----------- |---| ------------------------------ | -------------------- |
| math/rand |`Intn(n int) int`| 產生一個[0,$2^{31}-1$]後取餘數 | 隨機性生成器 |
| crypto/rand |`Int(rand io.Reader, max *big.Int) (n *big.Int, err error)`| 使用系統層隨機數產生 | 加密安全隨機數生成器 |