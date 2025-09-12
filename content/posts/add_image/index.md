+++
title = 'HUGOで画像を張る'
date = 2025-09-12T11:05:40+09:00
draft = true
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
![](Image.jpeg)
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
{{- with .Page.Resources.Get (.Get "path") }}
  {{- with .Process "resize 320x webp" }}
    <img src="{{ .RelPermalink }}" style="width: 20em" alt="{{ $.Get "alt" }}">
  {{- end }}
{{- end -}}
```

```
{{＜ image path="ファイル名" alt="代替テキスト" >}}
{{＜ image path="Image.jpeg" alt="人形の写真" >}}
```
※表現の都合で全角の「＜」を使用しています。

### 結果
{{< image path="Image.jpeg" alt="人形の写真" >}}
これが一番よさそう

## 参考
[https://qiita.com/Qiita/items/c686397e4a0f4f11683d](https://qiita.com/Qiita/items/c686397e4a0f4f11683d)
[https://gohugo.io/content-management/shortcodes/](https://gohugo.io/content-management/shortcodes/)