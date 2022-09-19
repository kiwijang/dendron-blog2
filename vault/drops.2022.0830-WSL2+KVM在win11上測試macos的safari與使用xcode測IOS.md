---
id: o7mp336qqwyjf1d0jefmg53
title: 0830 WSL2 + KVM 在 win11 上測試 macos 的 safari 與使用 xcode 測 IOS
desc: ""
updated: 1663219119443
created: 1662562033027
tags:
  - PROG.OS
status: w
---

## 測試環境搭建

這個筆記記錄了使用 IIS、VirtualBox、和 android 的 remote debbuging 來測網站。

> https://hackmd.io/vy1TyPnNRESPMTwMqNuPlA

但我最想用用看最潮的 Linux GUI。

> https://docs.microsoft.com/zh-cn/windows/wsl/tutorials/gui-apps

所以要用 Win11 的電腦才可以使用，我的電腦是 win11 pro。

以下是參考: [在 Windows 上流畅使用 MacOS 虚拟机](https://blog.hal.wang/7afa8fc1/) 的實作過程。

## 簡述過程

使用 WSL2 -> 灌 Ubuntu -> 在裡面灌 qemu -> 透過 OSX-KVM 灌好 macos -> 用 qemu 開啟 macos 的虛擬機

最後設定一些東西，讓此 WSL2 內的虛擬機可以連上我 win11 的 localhost。(還有設定螢幕大小和硬體配置)

## 下載 Ubuntu

## 安裝要用到的套件

## 相關設定
