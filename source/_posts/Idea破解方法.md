---
title: Idea破解方法
date: 2022-09-09 11:04:16
categories:
- 杂七杂八
- 软件安利
tags:
- 软件分享
- Idea
- 破解
---

<font color=red>通过补丁可以永久激活 IDEA，前面 IDEA 安装方式都是一样的，主要是后面的步骤，注意看后面就行~</font>

申明：本教程 IntelliJ IDEA 破解补丁、激活码均收集于网络，请勿商用，仅供个人学习使用，如有侵权，请联系作者删除。若条件允许，希望大家购买正版 ！

PS: 本教程最新更新时间: 2022年09月09日~

idea安装教程和冲突笔者不在这里赘述，百度都有解决方案，咱们直接开始后面的步骤~~~~

# 一、 永久激活版
- ### 下载激活脚本
   ![Reference](破解文件列表.png)
  打开文件夹后，目录如下，ja-netfilter.jar 为激活补丁：
  ![Reference](ja-netifilter.png)
- ### 复制补丁所在的整个文件夹到硬盘某个位置
  <font color=red>必须是整个ja-netifilter文件夹，之后就不要移动和删除这个文件夹了,这里笔者是直接放在了D盘</font>
- ### 引用激活补丁
  进入 IDEA 的安装目录，笔者安装时，使用了默认安装路径，然后，进入 /bin 目录下，修改
    `idea64.exe.vmoptions`配置文件:
  ![Reference](idea64.exe.vmoptions.png)
  在 `idea64.exe.vmoptions` 配置文件结尾添加如下配置：
    ``` vmoptions
    # 引用补丁，开头必须以 -javaagent: 开头，后面跟着补丁的绝对路径（可根据你实际的位置进行修改）,注意路径一定要填写正确，且不能包含中文，否则会导致 IDEA 无法启动
    -javaagent:D:/ja-netfilter/ja-netfilter.jar
    # 最新 IDEA 版本需要添加下面两行，以支持 Java 17, 否则会报 Key is invalid
    --add-opens=java.base/jdk.internal.org.objectweb.asm=ALL-UNNAMED
    --add-opens=java.base/jdk.internal.org.objectweb.asm.tree=ALL-UNNAMED
    ```
  ![Reference](vmoptions配置文件编辑.png)
- 重启 IDEA

  <font color=red>配置完成后保存，一定要重启 IDEA !!!</font>

  <font color=red>配置完成后保存，一定要重启 IDEA !!!</font>
- 重新打开 IDEA, 填入指定激活码点击激活完成激活
  ```
  ZCB571FZHV-eyJsaWNlbnNlSWQiOiJaQ0I1NzFGWkhWIiwibGljZW5zZWVOYW1lIjoiZnV6emVzIGFsbHkiLCJhc3NpZ25lZU5hbWUiOiIiLCJhc3NpZ25lZUVtYWlsIjoiIiwibGljZW5zZVJlc3RyaWN0aW9uIjoiIiwiY2hlY2tDb25jdXJyZW50VXNlIjpmYWxzZSwicHJvZHVjdHMiOlt7ImNvZGUiOiJQREIiLCJmYWxsYmFja0RhdGUiOiIyMDIzLTA3LTAxIiwicGFpZFVwVG8iOiIyMDIzLTA3LTAxIiwiZXh0ZW5kZWQiOnRydWV9LHsiY29kZSI6IlBTSSIsImZhbGxiYWNrRGF0ZSI6IjIwMjMtMDctMDEiLCJwYWlkVXBUbyI6IjIwMjMtMDctMDEiLCJleHRlbmRlZCI6dHJ1ZX0seyJjb2RlIjoiUFBDIiwiZmFsbGJhY2tEYXRlIjoiMjAyMy0wNy0wMSIsInBhaWRVcFRvIjoiMjAyMy0wNy0wMSIsImV4dGVuZGVkIjp0cnVlfSx7ImNvZGUiOiJQQ1dNUCIsImZhbGxiYWNrRGF0ZSI6IjIwMjMtMDctMDEiLCJwYWlkVXBUbyI6IjIwMjMtMDctMDEiLCJleHRlbmRlZCI6dHJ1ZX0seyJjb2RlIjoiUFBTIiwiZmFsbGJhY2tEYXRlIjoiMjAyMy0wNy0wMSIsInBhaWRVcFRvIjoiMjAyMy0wNy0wMSIsImV4dGVuZGVkIjp0cnVlfSx7ImNvZGUiOiJQUkIiLCJmYWxsYmFja0RhdGUiOiIyMDIzLTA3LTAxIiwicGFpZFVwVG8iOiIyMDIzLTA3LTAxIiwiZXh0ZW5kZWQiOnRydWV9LHsiY29kZSI6IklJIiwiZmFsbGJhY2tEYXRlIjoiMjAyMy0wNy0wMSIsInBhaWRVcFRvIjoiMjAyMy0wNy0wMSIsImV4dGVuZGVkIjpmYWxzZX0seyJjb2RlIjoiUEdPIiwiZmFsbGJhY2tEYXRlIjoiMjAyMy0wNy0wMSIsInBhaWRVcFRvIjoiMjAyMy0wNy0wMSIsImV4dGVuZGVkIjp0cnVlfSx7ImNvZGUiOiJQU1ciLCJmYWxsYmFja0RhdGUiOiIyMDIzLTA3LTAxIiwicGFpZFVwVG8iOiIyMDIzLTA3LTAxIiwiZXh0ZW5kZWQiOnRy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
  ```
- 成功页面

![Reference](激活成功页面.png)

# 二、 30天无限试用插件版
- 将ide-eval-resetter-2.1.6插件包直接拖进idea中安装然后重启idea

  ![Reference](ide-eval-resetter-2.1.6.png)

  ![Reference](ide-eval启用.png)
- 接着点击该插件的reset重置即可试用30天
## 附破解包from百度网盘:
## [破解包](https://pan.baidu.com/s/1YTc2CFHbSXz8Jbvo_S9_Jw  "JetBrains2022最新全家桶激活(7.30).zip") 密码:18cm
