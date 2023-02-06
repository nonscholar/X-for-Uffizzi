# Xray for Uffizzi

* * *

# 目录

- [项目特点](README.md#项目特点)
- [部署](README.md#部署)
- [鸣谢下列作者的文章和项目](README.md#鸣谢下列作者的文章和项目)
- [免责声明](README.md#免责声明)

* * *

## 项目特点:
* 本项目用于在 [Uffizzi](https://app.uffizzi.com) 部署 Xray，采用的方案为 Argo + Xray + WebSocket + TLS
* 在浏览器查看系统各项信息，方便直观
* 使用 CloudFlare 的 Argo 隧道，直接优选 + 隧道，CDN 不用再做 workers
* 回流分流，同时支持 Xray 4 种主流协议: vless /  vmess / trojan / shadowsocks
* vmess 和 vless 的 uuid，trojan 和 shadowsocks 的 password，各协议的 ws 路径既可以自定义，又或者使用默认值
* 集成哪吒探针，可以自由选择是否安装
* 前端 js 定时保活，会玩的用户可以根据具体情况修改间隔时间
* 节点信息以 V2rayN / Clash / 小火箭 链接方式输出
* Xray 文件重新编译官方文件增加隐秘性，修改了运行时的显示信息，文件为: https://github.com/XTLS/Xray-core/blob/main/core/core.go

## 部署:
* 注册 [Uffizzi](https://app.uffizzi.com)
* 点击项目右上方 "Use this template" 按钮，创建一个新库，如果需要哪吒，务必设置为不可见的私库，因为哪吒三个环境变量将暴露在文件处
* 绑定 Github 项目，授权使用上一步建立的库
* compose.yml 第 13-17 行设置各变量，如果不需要哪吒，删除或注释 15-17 行

* 用到的变量
  | 变量名        | 是否必须 | 默认值 | 备注 |
  | ------------ | ------ | ------ | ------ |
  | UUID         | 否 | de04add9-5c68-8bab-950c-08cd5320df18 | 可在线生成 https://www.zxgj.cn/g/uuid |
  | WSPATH       | 否 | argo | 勿以 / 开头，各协议路径为 `/WSPATH-协议`，如 `/argo-vless`,`/argo-vmess`,`/argo-trojan`,`/argo-shadowsocks` |
  | NEZHA_SERVER | 否 |        | 哪吒探针服务端的 IP 或域名 |
  | NEZHA_PORT   | 否 |        | 哪吒探针服务端的端口 |
  | NEZHA_KEY    | 否 |        | 哪吒探针客户端专用 Key |

* 需要应用的 js
  | 命令 | 说明 |
  | ---- |------ |
  | <URL>/list | 查看节点数据 |
  | <URL>/status | 查看后台进程 |
  | <URL>/listen | 查看后台监听端口 |
  


<img width="1631" alt="image" src="https://user-images.githubusercontent.com/92626977/216976623-a67d2a98-4940-4ea2-a704-fb2053a213dc.png">

<img width="1631" alt="image" src="https://user-images.githubusercontent.com/92626977/216977836-06c5ed85-545e-43b0-97c0-74bec269957c.png">

<img width="1069" alt="image" src="https://user-images.githubusercontent.com/92626977/216978370-1df57c3c-7f40-42a4-85b2-f2d22a69bf83.png">

<img width="1648" alt="image" src="https://user-images.githubusercontent.com/92626977/216978920-e8498768-9c1a-4f9b-ae23-2e5db135b9f6.png">

<img width="1629" alt="image" src="https://user-images.githubusercontent.com/92626977/216979507-d4d84552-ca37-4078-b3f5-6c530826b9bf.png">

<img width="885" alt="image" src="https://user-images.githubusercontent.com/92626977/216980080-773707bb-5607-4980-8de2-6e2f4e07dcaa.png">

<img width="511" alt="image" src="https://user-images.githubusercontent.com/92626977/216980271-55431c26-4d05-4501-a119-55d5d7cba5ee.png">
 
## 鸣谢下列作者的文章和项目:
大佬 Nike Jeff 的 trojan 项目，https://github.com/hrzyang/glitch-trojan ，在此基础上作修改。

## 免责声明:
* 本程序仅供学习了解, 非盈利目的，请于下载后 24 小时内删除, 不得用作任何商业用途, 文字、数据及图片均有所属版权, 如转载须注明来源。
* 使用本程序必循遵守部署免责声明。使用本程序必循遵守部署服务器所在地、所在国家和用户所在国家的法律法规, 程序作者不对使用者任何不当行为负责。
