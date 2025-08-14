+++
title = 'Hugoの環境構築'
date = 2025-08-14T15:40:50+09:00
draft = true
tags=["hugo"]
summary= "環境構築の巻"
+++

## HUGOとは
+ GO言語で書かれた静的サイトジェネレーター
+ 早い
+ markdownで書ける
+ GOの知識は要らん

## 私の環境
+ Windows 11 24H2(ちなみにInsider Priveewのベータチャンネルに入ってます)
+ VSCode 1.103.0
+ WSL上でやってます
```bash
$ hugo version
hugo v0.123.7+extended linux/amd64 BuildDate=2025-07-18T03:41:49Z VendorInfo=ubuntu:0.123.7-1ubuntu0.3
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=24.04
DISTRIB_CODENAME=noble
DISTRIB_DESCRIPTION="Ubuntu 24.04.3 LTS"
```
Powershell(≠Windows PowerShell)からでもいけるらしい(.NET Frameworkと.NETの違いらしい)

## 手順
### HUGOのインストール
```bash
$ sudo apt install hugo
```
Ubuntuを再起動。

### サイトを作る
```bash
$ hugo new site site_name
```
<details><summary>俺用</summary>
カレントディレクトリを親に移して
```bash
$ hugo new site site_name --force
```
した場合、後々ファイルの位置で整合が取れなくなる。
</details>

### tailwindテーマの導入
```bash
$ git submodule add https://github.com/tomowang/hugo-theme-tailwind.git themes/tailwind
```
```hugo.toml```をいかに書き換え
```toml
baseURL = "https://example.com/"
title = "Hugo Theme Tailwind Example Site"
author = "Your Name"
copyright = "Your Name"
pagination.pagerSize = 10
languageCode = "jp"
defaultContentLanguage = 'jp'
theme = "tailwind"

[markup]
  _merge = "deep"

[params]
  contentTypeName = "posts"

  [params.header]
    logo = "logo.webp"
    title = ""

  [params.footer]
    since = 2023
    poweredby = true

[menu]

  [[menu.main]]
    identifier = "投稿"
    name = "Post"
    pageRef = "/posts"
    weight = 10

  [[menu.main]]
    identifier = "about"
    name = "About"
    pageRef = "/about"
    weight = 20

[taxonomies]
category = "categories"
tag = "tags"
series = "series"
```

### ページを作る
```bash
$ hugo new content posts/page_name/index.md
```
か`content`ディレクトリに直接mdファイルを作る。

### ビルドとサーバー起動
```bash
$ hugo --buildDrafts
```
でmarkdownをhtmlに変換してくれる。
次にローカルサーバーを起動。
```bash
$ hugo server & #bash でローカルにサーバーが起動。
$ hugo server -D & #下書きも含める。
```

<details><summary>謎</summary>
Windows上のPowerSHellで ```hugo server -D & ```bash とした場合、リアルタイムで保存した内容をビルドしてくれるが、WSLではなぜかできない？なんでだ？ちゃんと調べなくては。
</details>

## 最後に
markdown慣れたい。go言語も使ってみたい。
次回は画像とかGitHub Pagesをちゃんと理解したい。

## 参考
+ https://gohugo.io/getting-started/quick-start/
+ https://github.com/tomowang/hugo-theme-tailwind/tree/4d127288a8cc77a41bf97d895855c48c9e1152d5