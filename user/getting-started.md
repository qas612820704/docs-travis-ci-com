---
title: 入門指南
layout: en

---

這是一篇相當簡短的指南關於使用 Travis CI 在你 GitHub 托管的代碼庫。如果你是持續整合的新手或是想了解更多有關 Travis CI 的訊息，請從[給初學者的核心概念](/user/for-beginners)開始。

<div id="toc"></div>

## 必備條件

在開始使用 Travis CI 之前，請確保你有下列*所有*的東西：

 * 登入[GitHub](https://github.com/)
 * 在 Github [托管儲存庫](https://help.github.com/categories/importing-your-projects-to-github/) 的專案
 * 在你的專案有可運作的代碼
 * 可運作的建構或測試腳本

## 開始使用 Travis CI

1. 使用你的 Github 帳號，登入至 [GitHub](https://github.com/marketplace/travis-ci)，然後將 Travis CI 應用程式新增到你想啟動的儲存庫。

2. 一旦你登入了 Travis CI，我們就已經同步你 Github 儲存庫。到你的個人資料頁面並啟用想建構的專案： ![enable button](/images/enable.png "enable button")

3. 新增 `.travis.yml` 到你的儲存庫來告訴 Travis CI 該做什麼。

  以下的範例告訴 Travis CI 這是一個 Ruby 的專案，並且應該使用 Ruby 2.2，最新版的 JRuby 和 Rubinius 2.X 構建。

  ```yaml
  language: ruby
  rvm:
  - 2.2
  - jruby
  - rbx-3
  ```
  {: data-file=".travis.yml"}

  Ruby 專案的預設值是用 `bundle install` [安裝相依套件](/user/customizing-the-build/#Customizing-the-Installation-Step)和 `rake` 建構專案。

4. 新增 `.travis.yml` 到 git，提交並推送，觸發 Travis CI 建構：

  > Travis 只會建構在你啟用 Travis CI 儲存庫之後的提交。

5. 檢查建構頁面，看看你的建構[通過或是失敗](/user/customizing-the-build/#Breaking-the-Build)，根據建構指令的回傳狀態去訪問[Travis CI .com 建構狀態](https://travis-ci.com/auth)並選擇你的儲存庫。


## 選擇不同的程式語言

使用其中一個常見的程式語言

```yaml
language: ruby
```
{: data-file=".travis.yml"}

```yaml
language: java
```
{: data-file=".travis.yml"}

```yaml
language: node_js
```
{: data-file=".travis.yml"}

```yaml
language: python
```
{: data-file=".travis.yml"}

```yaml
language: php
```
{: data-file=".travis.yml"}

或者從[完整列表](/user/languages/)選一個.

## 選擇基礎設施 (可選的)

最好判斷你在什麼基礎上建構的方法是設定 `lauguage`。如果你這麼做你的建構會跑在預設的基礎上(除了少數的例外)，Ubuntu 14.04 的容器。你可以更加明確的選擇預設的基礎，藉由新增 `sudo: false` 到你你的 `.travis.yml`。

* 如果你想要在虛擬機中跑更多自定義的環境，使用啟用 Sudo 的基礎架構。

  ```yaml
  sudo: enabled
  ```
  {: data-file=".travis.yml"}

* 如果你的測試是需要跑在 macOS 上，或是專案用到 Swift 或 Objective-C，使用我們的 OS X 環境：

  ```yaml
  os: osx
  ```
  {: data-file=".travis.yml"}

  > 你在 Mac 上開發*不一定*需要用 OS X 環境， 只有當你需要 Swift，Objective-C 或是其他限定 macOS 的軟體時候使用。

## 不只是運行測試

Travis CI 不只是能幫你跑測試而已，它還有其他很多能在你代碼上做的事：

* 部屬到 [GitHub pages](/user/deployment/pages/)
* 運行應用程式在 [Heroku](/user/deployment/heroku/)
* 上傳到 [RubyGems](/user/deployment/rubygems/)
* 發布 [通知](/user/notifications/)

## 延伸閱讀

閱讀更多關於

* [自定義你的建構](/user/customizing-the-build)
* [安全性最佳實踐](/user/best-practices-security/)
* [建立階段](/user/build-stages/)
* [建立矩陣](/user/customizing-the-build/#Build-Matrix)
* [安裝相依套件](/user/installing-dependencies)
* [配置資料庫](/user/database-setup/)
