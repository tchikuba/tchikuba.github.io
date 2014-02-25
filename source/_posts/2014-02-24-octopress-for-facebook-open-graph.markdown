---
layout: post
title: "Octopressでfacebook用OGPを設定する方法"
date: 2014-02-24 20:00
comments: true
categories: [Octopress, Facebook, OGP]
description: "Octopressでfacebook用OGPを設定する際に以外と引っ掛かるところがあったので共有します。"
keywords: "Octopress,Facebook,OGP"
published: true
---

Octopressでfacebook用OGPを設定する際、意外と引っ掛かるところがあったので手順をまとめておきます。

# OctopressでOGP設定する際に参考にしたサイト
* [Octopress - Facebook OGP 設定！](http://www.mk-mode.com/octopress/2012/12/31/octopress-facebook-ogp/)
* [Octopressの気になるところを修正してみた](http://www.sankitch.me/blog/2012/05/09/octopress-customize/)
* [OctopressでFacebookシェア用にOGPを設定する](http://morizyun.github.io/blog/octopress-facebook-ogp-upgrade/)

# 手順

## 1. facebookのapp_idを取得する
まずfacebookアプリのapp_idを取得します。
取得方法は[facebookのOGP設定について](http://www.issun.com/blog/ogp/)等を参照すると良いかと。

* facebookアプリの設定で`App Domains`を指定しないとJSエラー発生が発生するのでご注意を。
* `+Add Platform`をクリックして`ウェブサイト`を選択して`サイトURL``Mobile Site URL`を設定してから`App Domains`を入力しないと順序が逆だとfacebook側で警告が出ますのでご注意を。

## 2. OGP用の画像をアップロードする
OGPの`og:image`プロパティに指定する画像をアップロードします。

## 3. _config.ymlを編集する
`facebook_app_id`, `facebook_locale`, `default_ogp_image`をセットします。

``` yaml _config.yml
facebook_app_id: app_id ←手順1で取得したapp_id
facebook_locale: ja_JP
default_ogp_image: /images/xxx.jpg ←手順2でアップロードした画像の相対パス
```

## 4. source/_includes/facebook_like.htmlを編集する
以下のように手順3でセットした`facebook_locale`と`facebook_app_id`を動的になるよう修正します。

{% raw %}
``` html source/_includes/facebook_like.html
{% if site.facebook_like %}
<div id="fb-root"></div>
<script>(function(d, s, id) {
  var js, fjs = d.getElementsByTagName(s)[0];
  if (d.getElementById(id)) {return;}
  js = d.createElement(s); js.id = id;
  js.src = "//connect.facebook.net/{{ site.facebook_locale }}/all.js#appId={{ site.facebook_app_id }}&xfbml=1";
  fjs.parentNode.insertBefore(js, fjs);
}(document, 'script', 'facebook-jssdk'));</script>
{% endif %}
```
{% endraw %}

## 5. source/_includes/custom/facebook_ogp.htmlを編集する
以下のようなOGPをセットします。

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

* `og:image`はフルパスで指定

## 6. source/_includes/head.htmlを編集する
上記`facebook_ogp.html`をインクルードする記述を`</head>`の直前に追加します。

{% raw %}
``` html source/_includes/head.html
  (略)
  {% include custom/facebook_ogp.html %}
</head>
```

また、"authorに関するOGPが設定不十分だよ"という以下の警告が出ます。

> "The meta tag on the page was specified with name ‘author’, which matches a configured property of this object type. It will be ignored unless specified with the meta property attribute instead of the meta name attribute."

これを解消する為には以下のmetaタグを削除します。

``` html source/_includes/head.html
  <meta name="author" content="{{ site.author }}">
```
{% endraw %}

以下参考記事です。

* [ブログの記事をFacebookでシェアした時に、作成者名を表示させる方法 #wpacja2013](http://mekemoke.jp/2013/12/1319.html)

## 7. 記事をアップしてOGPデバッガーで確認する
facebookが提供している[OGPデバッガー](https://developers.facebook.com/tools/debug)で
OGPが意図するように設定されているか確認します。

以下はデバッガーで確認するとよく出る警告です。

> "og:image should be larger. Provided og:image is not big enough. Please use an image that's at least 200x200 and preferably 1500x1500."

* "OGPの画像が十分に大きくないよ"という警告。十分に大きいサイズでないと出るようです。以下参考記事。
  - [Facebookのog:imageが無視されて異なる画像が勝手に指定される件（推奨サイズの追記あり）](http://ore.hatenablog.jp/entry/2013/02/24/185923)
  - 推奨は1500x1500らしいのですがそこまで大きくなくても私の場合800pxくらいで大丈夫でした。


以上
