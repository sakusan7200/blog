+++
title = 'HUGOで画像を張る'
date = 2025-09-12T11:05:40+09:00
draft = false
+++

# HUGOで画像をはろうの巻
HUGOで画像をはる方法について調べました。

## 方法① Markdownでよくある(?)書き方
### 書き方
```
![人形の写真](Image.jpeg)
![代替テキスト](画像のURL)
```
### 結果
![a]("Image.jpeg")
でかい。

## 方法② imgタグ
### 書き方
```html
<img alt="代替テキスト" class="" src="画像のパス"/>
<img alt="人形の写真" class="" src="Image.jpeg"/>
```
<img alt="人形の写真" style="width:20em" src="Image.jpeg"/>



## 方法③ shortcode
### 書き方

```html
<img src="{{ .Get "src" }}" alt="{{ .Get "alt" }}" style="width: 20em;">
```

```
{{＜ image src="Image.jpeg" alt="サンプル画像" >}}
{{＜ image src="Image.jpeg" alt="サンプル画像" >}}
```
※表現の都合で全角の「＜」を使用しています。

### 結果
{{< image src="Image.jpeg" alt="サンプル画像" >}}
これが一番よさそう

## 参考
[https://qiita.com/Qiita/items/c686397e4a0f4f11683d](https://qiita.com/Qiita/items/c686397e4a0f4f11683d)\
[https://gohugo.io/content-management/shortcodes/](https://gohugo.io/content-management/shortcodes/)