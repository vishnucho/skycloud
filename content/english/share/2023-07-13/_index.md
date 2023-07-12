---
title: '2023-07-12 Debug的好朋友 - Chrome Devtools'
description: 'Chrome Devtools'
categories: ['Tech']
tags: ['Tech']
---

# Debug的好朋友 - Chrome Devtools

## 講者： Ariel

## Element面板
![element-panel](https://vishnucho.github.io/skycloud/share/2023-07-13/imgs/element.webp)

* #1: 查看該元素
* #2: 設置不同斷點模擬設備
* #3: HTML元素結構顯示即時編輯，在console面板可以用$0獲取當前選取的元素並操作
* #4: 當前選中元素的所在位置
* #5: 顯示當前選中元素的樣式，盒模型
* #6: 顯示當前選中元素的盒模型，樣式屬性計算
* #7: 顯示當前選中元素上所綁定的事件
* #8: 顯示DOM斷點列表
* #9  顯示當前選中元素的屬性

## Network面板

### 檢視請求記錄
- Status：HTTP狀態碼
- Type：請求資源的MIME型別
- Initiator：標記請求是由某一對象發起
- Size：請求的資源大小
- Time：總持續時間，從發起請求到資源下載完成
- Waterfall：每一個請求活動不同階段的可視化瀑布流

> 可使用filter過濾請求，filter支援正則表達式、參數(cookie-domain、cookie-name、cookie-path、cookie-value、domain、has-response-header、is、larger-than、method、mime-type、mixed-content、priority、resource-type、response-header-set-cookie、scheme、set-cookie-domain、set-cookie-name、set-cookie-value、status-code、url)

### 檢視載入事件
DOMContentLoaded事件在Overview和Requests Table對應藍線，並且在Summary以藍色文字顯示確切時間，而Load事件對應紅色。

![network-panel](https://vishnucho.github.io/skycloud/share/2023-07-13/imgs/chrome-devtools-network.webp)

> DOMContentLoaded: 在 DOM 結構被完整的讀取跟解析後就會被觸發，不須等待外部資源讀取完成
> load: 在網頁所有資源都已經載入完成後才會觸發

### 其他
* 模擬不同的網路條件
* 檢查檔案有沒有壓縮成功
* 攔截請求

## Reference
1. [devtool dom](https://developer.chrome.com/docs/devtools/dom/)
2. [devtool network](https://developer.chrome.com/docs/devtools/network/reference/)