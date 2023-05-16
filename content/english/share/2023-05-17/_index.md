---
title: "2023-05-17 隱藏在 AI 背後的技術"
description: "談論有AI技術閒聊"
categories: ["Tech"]
tags: ["Tech"]
---

# 2023-05-17 隱藏在 AI 背後的技術

## 講者： 增宇

## 什麼是 AI ?

根據 Wikipedia 所定義的**人工智慧**（Artificial Intelligence，縮寫為 AI）：
指由人製造出來的機器所表現出來的智慧。通常人工智慧是指透過普通電腦程式來呈現人類智慧的技術。

因此不論其背後所使用的技術是 [Rule-based](https://zh.wikipedia.org/wiki/%E5%9F%BA%E6%96%BC%E8%A6%8F%E5%89%87%E7%9A%84%E7%B3%BB%E7%B5%B1) 或是 [機器學習（Machine learning，縮寫為 ML）](https://zh.wikipedia.org/wiki/%E6%9C%BA%E5%99%A8%E5%AD%A6%E4%B9%A0) 都可以稱為 AI。而現在主流的 AI 技術則是使用一種屬於 ML 技術的 [深度學習（Deep learning，縮寫為 DL）](https://zh.wikipedia.org/zh-tw/%E6%B7%B1%E5%BA%A6%E5%AD%A6%E4%B9%A0)。

![](https://hackmd.io/_uploads/SkwF88o4n.png)

## AI 發展史

AI 最早從 1950 年代就開始發展了，有許多現在訓練 AI 所使用的演算法和技術都是從當時就被提出了，只是礙於當時電腦的計算能力及資料數量太少的問題使得發展受到限制。

伴隨著電腦的普及而興起了第二次的發展熱潮，這次人們主要專注於專家系統的研究，但後來因為其侷限性且沒辦法自主學習而逐漸退潮。而此時期也因為金主們覺得投資人工智慧的性價比不高而停止投資，成為此時期最大的研究瓶頸。

隨著現今電腦、網路資訊的蓬勃發展，深度學習的效果得以展現，也因為人工智慧成功在特定領域已經勝過人類（如 Deep Blue、AlphaGO 等），而迎來了第三次的人工智慧發展潮流。

![](https://hackmd.io/_uploads/By2T9GyS3.jpg)

## Machine learning 及 Deep learning 簡介

一般撰寫程式時，我們會將 Input 丟到人工撰寫的 Function 後得到一個 Output。而 ML 的目標就是將 **人工撰寫 Function** 的這個工作交給程式自己學習。

ML 主要可以分為三個步驟，第一個步驟為定義 Function Set(Model)，第二個步驟是要讓 Machine 可以定義出好的 Function (替它評分)，最後一個步驟就是用演算法找出最好的 Function。

![](https://hackmd.io/_uploads/H1uRdvs42.jpg)

下面是一個 **類神經網路的 Model**(Function Set) 示意圖，左邊是輸入端、右邊是輸出端，中間 Hidden Layer 的每一個節點都表示一個參數，當任意一個參數改變時就代表一個全新的 Function ，如此一來我們就有無限個 Function 可以來挑選了。

![](https://hackmd.io/_uploads/B1sXXDiNh.png)

要 Training Model 主要有三大類的方法，分別是 **監督式學習(Supervised learning)** 、 **非監督學習(Unsupervised learning)** 及 **強化學習(Reinforcement Learning)**，其中也包含了相當多的技術，這邊就先不贅述了，有興趣深入的話可以參考 References 中的線上課程。

而 DL 就是指 Model 的 Layer 較多，而單一 Layer 中的參數較少。在許多應用中（相同參數數量的條件下），較深的 Model 通常表現較佳。

![](https://hackmd.io/_uploads/rkJV5voVh.png)

## AI 的技術應用

根據 Wikipedia 所介紹的 AI 應用主要可以分為下列四種：

### 感知能力（Perception）

1. 看: 電腦視覺（Computer Vision）、圖像辨識（Image Recognition）、臉部辨識（Face Recognition）、物件偵測（Object Detection）
2. 聽: 語音辨識（Sound Recognition）
3. 說: 語音生成（Sound Generation）、文字轉換語音（Text-to-Speech）
4. 讀: 自然語言處理（Natural Language Processing，NLP）、語音轉換文字（Speech-to-Text）
5. 寫: 機器翻譯（Machine Translation）

綜合應用範例(聊天 AI)：[ChatGPT](https://chat.openai.com/), [Google Bard](https://bard.google.com/), [Bing Chat](https://www.bing.com/new)

### 認知能力（Cognition）

指的是人類透過學習、判斷、分析等等心理活動來瞭解訊息、獲取知識的過程與能力，對人類認知的模仿與學習也是目前 AI 第二個焦點領域，主要包括：

分析辨識能力：例如醫學圖像分析、產品推薦、垃圾郵件辨識、法律案件分析、犯罪偵測、信用風險分析、消費行為分析等。
預測能力：例如 AI 執行的預防性維修（Predictive Maintenance）、智慧天然災害預測與防治。
判斷能力：例如 AI 下圍棋、自動駕駛車、健保詐欺判斷、癌症判斷等。
學習能力：例如機器學習、深度學習、增強式學習等等各種學習方法。

### 創造力（Creativity）

指的是人類產生新思想，新發現，新方法，新理論，新設計，創造新事物的能力，它是結合知識、智力、能力、個性及潛意識等各種因素優化而成，這個領域目前人類仍遙遙領先 AI，但 AI 也試著急起直追，主要領域包括：AI 作曲、AI 作詩、AI 小說、AI 繪畫、AI 設計等。

實際應用案例：[Midjourney](https://docs.midjourney.com/), [DALL·E 2](https://labs.openai.com/), [Stableboost](https://stableboost.ai/create), [NovelAI (小說及插圖)](https://novelai.net/stories), [Stable Diffusion(免費)](https://stablediffusionweb.com/#demo), [Deepfake (影片換臉)](https://deepfakesweb.com/), [Leonardo](https://leonardo.ai/)

軟體開發相關應用案例：[Copilot](https://github.com/features/copilot), [CodeWhisperer](https://aws.amazon.com/tw/codewhisperer/)

### 智慧（Wisdom）

指的是人類深刻瞭解人、事、物的真相，能探求真實真理、明辨是非，指導人類可以過著有意義生活的一種能力，這個領域牽涉人類自我意識、自我認知與價值觀，是目前 AI 尚未觸及的一部分，也是人類最難以模仿的一個領域。

## References

1. [人工智慧 - Wikipedia](https://zh.wikipedia.org/zh-tw/%E4%BA%BA%E5%B7%A5%E6%99%BA%E8%83%BD)
2. [什麼是人工智慧、機器學習和深度學習? - Tommy Huang](https://chih-sheng-huang821.medium.com/%E4%BB%80%E9%BA%BC%E6%98%AF%E4%BA%BA%E5%B7%A5%E6%99%BA%E6%85%A7-%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E5%92%8C%E6%B7%B1%E5%BA%A6%E5%AD%B8%E7%BF%92-587e6a0dc72a)
3. [【AI60 問】Q10 人工智慧(AI)發展史？ - 提拔我園丁](https://blog.tibame.com/?p=17567)
4. [[Day 04] 人工智慧歷史回顧 History of Artificial Intelligence](https://ithelp.ithome.com.tw/articles/10239971)
5. [Machine Learning 線上課程 - NTU 李宏毅](https://www.youtube.com/watch?v=CXgbekl66jc&list=PLJV_el3uVTsPy9oCRY30oBPNLCo89yu49)
6. [AI 繪圖網站綜合比較 - Bowtie 團隊](https://www.bowtie.com.hk/blog/zh/ai-%E7%B9%AA%E5%9C%96/)
