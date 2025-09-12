+++
title = 'Add_image'
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

## 方法② imgタグ
### 書き方
```html
<img alt="代替テキスト" class="" src="画像のパス"/>
<img alt="人形の写真" class="" src="Image.jpeg"/>
```
<img alt="人形の写真" width="20em" src="Image.jpeg"/>


## 方法③ shortcode




これが一番よさそう