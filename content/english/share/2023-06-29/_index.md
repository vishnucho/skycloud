---
title: '2023-06-29 你不需要密碼 - Fast IDentity Online'
description: 'fxck up your password'
categories: ['Tech']
tags: ['Tech']
---

# 你不需要密碼 - Fast IDentity Online

## 講者： Jeff

現在，你需要申請會員，請輸入你的帳號密碼

注意: 密碼必須包含大小寫字母、數字、特殊符號，且長度必須大於 8 個字元。每三個月變更一次密碼，且不可與前三次的密碼相同。

MDFK.

## 密碼機制的困境

1. 密碼的安全性與使用者的行為有關，但使用者的行為是無法控制的。
2. 密碼驗證的是 ID 而不是使用者的身份。
3. 密碼考驗的是使用者的記憶力，而不是使用者的身份。

> 聽過釣魚網站吧，魚兒們。

## 日趨複雜的密碼機制，還是密碼

1. 增加複雜度與長度
2. 增加變更頻率
3. 增加變異性
4. 安全提示問題
5. SSO / OAuth

## 密碼的安全性

2 Factor Authentication (2FA) / one-time password (OTP)

> 一個密碼驗證最主要弱點就是密碼是一個共享的秘密。
>
> 除非你是有使用 2FA 的 28% 使用者之一
>
> 在現代的密碼機制下，2FA 幾乎是必要的

## 資安是光譜

```mermaid
graph LR
    A[安全性] --- B[便利性]
```

## Fast Identity Online (FIDO)

FIDO 的目標是提供更安全、更便利的身份驗證機制，取代傳統的使用密碼進行身份驗證的方式。

- 2012: FIDO Alliance
- 2013: iPhone 5s
- 2014: UAF/U2F
  - UAF: 生物特徵
  - U2F: 硬體金鑰
- 2018: FIDO2 WebAuthn/CTAP
  - WebAuthn: 網頁 API
  - CTAP: 裝置 API
- 2019: W3C WebAuthn
- 2020: Platform and browser support (WebAuthn)

## Web Authentication API

Web Authentication API (WebAuthn) 是由 W3C 與 FIDO 撰寫的規格，並由 Google、Mozilla、Microsoft、Yubico 等公司參與。

該 API 允許伺服器使用公開金鑰密碼學而不是密碼來註冊和驗證使用者。

> SSH key: credential

## Client to Authenticator Protocol (CTAP)

WebAuthn API 透過 CTAP 與驗證器溝通

## Registering

```mermaid
sequenceDiagram
    participant User as User
    participant UserDevice as User Device (Authenticator)
    participant Server as Server

    User->>UserDevice: 建立帳號
    UserDevice->>UserDevice: 生成公私鑰對
    UserDevice->>UserDevice: 儲存公私鑰對
    UserDevice->>Server: 註冊請求（包含公鑰）
    Server->>Server: 生成挑戰（隨機字符串）
    Server->>UserDevice: 提供挑戰
    UserDevice->>UserDevice: 簽署挑戰（使用私鑰）
    UserDevice->>Server: 提交挑戰回應（簽名和公鑰）
    Server->>Server: 驗證挑戰回應（簽名和公鑰）
    Server->>Server: 儲存註冊資料（包含公鑰和用戶標識）
    Server->>User: 註冊成功通知
```

## Authenticating

```mermaid
sequenceDiagram
    participant User as User
    participant UserDevice as User Device (Authenticator)
    participant Server as Server

    User->>UserDevice: 登入
    UserDevice->>Server: 請求登入
    Server->>Server: 生成挑戰（隨機字符串）
    Server->>UserDevice: 提供登入挑戰
    UserDevice->>UserDevice: 簽署登入挑戰（使用私鑰）
    UserDevice->>Server: 提交登入挑戰回應（簽名）
    Server->>Server: 驗證登入挑戰回應（使用公鑰）
    Server->>User: 回傳登入結果
```

## Passkeys

**你不需要密碼，而是密碼需要你**

1. 不再有字面上意義的密碼，使用者只需要證明自己
2. 不可視的密碼儲存在那些能認證使用者的裝置中
3. 密碼是唯一的，但證明自己的方式卻是多樣的
4. 在便利性與安全性中取得平衡

[Passkey DEMO](https://www.passkeys.io/)


> One more thing...
> WEB 3.0: Decentralized Identity (DID)