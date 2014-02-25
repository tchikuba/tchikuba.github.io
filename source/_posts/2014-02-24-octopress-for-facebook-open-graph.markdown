---
layout: post
title: "Octopressでfacebook用OGPを設定する方法"
date: 2014-02-24 20:00
comments: true
categories: [Octopress, Facebook, OGP]
description: "Octopressでfacebook用OGPを設定する際に以外と引っ掛かるところがあったので共有します。"
keywords: "Octopress,Facebook,OGP"
published: false
---

Octopressでfacebook用OGPを設定する際、以外と引っ掛かるところがあったので手順をまとめておきます。

# OctopressでOGP設定する際に参考にしたサイト
* [Octopress - Facebook OGP 設定！](http://www.mk-mode.com/octopress/2012/12/31/octopress-facebook-ogp/)
* [Octopressの気になるところを修正してみた](http://www.sankitch.me/blog/2012/05/09/octopress-customize/)
* [OctopressでFacebookシェア用にOGPを設定する](http://morizyun.github.io/blog/octopress-facebook-ogp-upgrade/)

# 手順

## 1. facebookのapp_idを取得する
まずfacebookアプリのapp_idを取得します。
取得方法は[facebookのOGP設定について](http://www.issun.com/blog/ogp/)等を参照すると良いかと。

## 2. OGP用の画像をアップロードする
OGPの`og:image`に指定する画像をアップロードします。

## 3. _config.ymlを編集する
facebook_app_id, facebook_locale, default_ogp_imageをセットします。

``` yaml _config.yml
facebook_app_id: app_id ←手順1で取得したapp_id
facebook_locale: ja_JP
default_ogp_image: /images/xxx.jpg ←手順2でアップロードした画像の相対パス
```

## 4. source/_includes/custom/facebook_ogp.htmlを編集する
以下のような内容をセットしました。

{% raw %}
``` html source/_includes/custom/facebook_ogp.html
<meta property="og:title" content="{% if page.title %}{{ page.title }} - {% endif %}{{ site.title }}" />
<meta property="og:description" content="{{ description | strip_html | condense_spaces | truncate:150 }}" />
<meta property="og:url" content="{{ canonical }}/" />
<meta property="og:image" content="{{ site.url }}{% if page.ogp_image %}{{ page.ogp_image }}{% else %}{{ site.default_ogp_image }}{% endif %}" />
<meta property="og:author" content="{{ site.author }}" />
<meta property="og:site_name" content="{{ site.title }}" />
<meta property="og:locale" content="{{ site.facebook_locale }}" />
<meta property="og:type" content="{% if page.index %}blog{% else %}article{% endif %}" />
<meta property="fb:app_id" content="{{ site.facebook_app_id }}" />
```
{% endraw %}

* `og:url`についてはなぜかcanonicalのままだとURL末尾の`/`が抜けてOGPエラーが発生したので`/`を追加
* `og:image`はフルパスで指定

## 5. source/_includes/head.htmlを編集する
上記`facebook_ogp.html`をインクルードする記述を`</head>`の直前に追加します。

{% raw %}
``` html source/_includes/head.html
  (略)
  {% include custom/facebook_ogp.html %}
</head>
```
{% endraw %}

# facebookアプリの設定でApp Domainsを指定しないとJSエラー発生
https://developers.facebook.com/x/apps/659253570789231/settings/
* Add Platformからウェブサイトを登録してApp Domainsを指定しないとFB側でエラー発生

# OGPの画像が十分に大きくないよ警告が出る
http://ore.hatenablog.jp/entry/2013/02/24/185923

# FBのデバッガーは便利
https://developers.facebook.com/tools/debug

