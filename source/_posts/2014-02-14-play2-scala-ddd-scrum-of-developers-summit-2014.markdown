---
layout: post
title: "ドワンゴ吉村総一郎氏「Play2/Scalaでドメイン駆動設計を利用した大規模Webアプリケーションのスクラム開発の勘所」@デブサミ2014 2日目"
date: 2014-02-14 16:50
comments: true
categories: [devsumi2014, Play2, Scala, DDD, scrum]
description: "2014年2月14日(金)に行われたデブサミ2014 2日目のセッションドワンゴ吉村総一郎氏「Play2/Scalaでドメイン駆動設計を利用した大規模Webアプリケーションのスクラム開発の勘所」を聞いた内容のまとめです。"
keywords: "デブサミ2014, Play2, Scala, ドメイン駆動設計, DDD, スクラム, scrum, PHP"
---

引き続き[デブサミ2014](http://event.shoeisha.jp/devsumi/20140213/)。
ドワンゴ吉村総一郎氏によるセッション[「Play2/Scalaでドメイン駆動設計を利用した大規模Webアプリケーションのスクラム開発の勘所」](http://event.shoeisha.jp/devsumi/20140213/session/407/)を聞きました。
![top slide](/images/play2-scala-ddd-scrum/1.jpg)
いろんなところで良く聞くPHPレガシーコードにどう立ち向かったのか聞いてみたかったです。
案の定というか、想像以上のPHPレガシーコードっぷりにちょっと感動すらしましたがｗ

- - -

# profile
* [株式会社ドワンゴ](http://info.dwango.co.jp/) [吉村総一郎氏](https://twitter.com/sifue)
* ウォーターフォール開発とアジャイル開発の両方のマネージャー経験
* [スライド](http://sifue.hatenablog.com/entry/2014/02/14/195018)
<iframe src="http://www.slideshare.net/slideshow/embed_code/31204064" width="427" height="356" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px 1px 0; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="https://www.slideshare.net/sifue/developers-summit-2014-play2scalaweb" title="Developers Summit 2014 「Play2/Scalaでドメイン駆動設計を利用した大規模Webアプリケーションのスクラム開発の勘所」" target="_blank">Developers Summit 2014 「Play2/Scalaでドメイン駆動設計を利用した大規模Webアプリケーションのスクラム開発の勘所」</a> </strong> from <strong><a href="http://www.slideshare.net/sifue" target="_blank">Yoshimura Soichiro</a></strong> </div>

# ニコニコ生放送を書き直す理由
* コードの技術的負債がやばい
* PHPで書かれている: 300万行！
  - facebookで1000万行と言われているそう
* 1万行のクラスや4000行のメソッド
* 循環的複雑度600超のメソッドががが
  - あまりに複雑過ぎて龍の巣と言われている（笑）
  - まさに壊れかけのジェンガのよう
* 企画やスケジュールを優先するあまり品質を疎かにする開発体制

# どうやって？
* スモールスタート／スモールリリース
* 2週間に1度、[ショーケース](http://books.google.co.jp/books?id=qqkQ-HhjZf0C&pg=PA208&lpg=PA208&dq=%E3%82%B7%E3%83%A7%E3%83%BC%E3%82%B1%E3%83%BC%E3%82%B9%E3%80%80%E3%82%A2%E3%82%B8%E3%83%A3%E3%82%A4%E3%83%AB&source=bl&ots=eHDng0u5MV&sig=l4tCZtgK-4xsdDZFHSXr9MgTrCQ&hl=ja&sa=X&ei=gEQAU8qmEIe6lAXtooHADw&ved=0CEAQ6AEwAw#v=onepage&q=%E3%82%B7%E3%83%A7%E3%83%BC%E3%82%B1%E3%83%BC%E3%82%B9%E3%80%80%E3%82%A2%E3%82%B8%E3%83%A3%E3%82%A4%E3%83%AB&f=false)を実施
* 年末特番もクリアして今のところ大丈夫

# 裏話
* PHPは素晴らしい: 全てのコレクションをarrayで扱える
* Scalaはたくさんの型があるのでPHPerには辛く初学コストが高い
* 並行プログラミングの知識も必要
  - [Actor](http://www.atmarkit.co.jp/ait/articles/1209/06/news134.html)とか
* インフラ／アプリの組織的な垣根がボトルネックになったので席を近くするなどして改善
* インフラはクラウドではなくオンプレミスで
* DBはMySQL／Redis
* [gatling](http://gatling-tool.org/)が素晴らしいストレスツール

# DDD (Domain Driven Design: [ドメイン駆動設計](http://ja.wikipedia.org/wiki/%E3%83%89%E3%83%A1%E3%82%A4%E3%83%B3%E9%A7%86%E5%8B%95%E8%A8%AD%E8%A8%88))
* Play2/Scalaでの開発と相性が良い(スライドP.42)
![slide 42](/images/play2-scala-ddd-scrum/2.jpg)
* DDD解説のYouTube動画(42分)が素晴らしい
  - [DevLove Building Blocks 都元ダイスケ](http://www.youtube.com/watch?v=FNEfk-dlIKU)
  - 社内勉強会で何度も視聴した
* ドメイン層の保守性向上に貢献する

# 環境
* デプロイには[Capistrano](https://github.com/capistrano/capistrano)使用: [Mina](http://nadarei.co/mina/)にしようとしたが断念
* IDEは[IntelliJ IDEA Ultimate](http://www.jetbrains.com/idea/)に統一
* CIは[Jenkins](http://jenkins-ci.org/)
  - 現在scalaのコードは5万行
  - 重複コード0
  - 行ベースのカバレッジ52%
* Play2/Scalaによる開発には難点もある(スライドP.61)
![slide 61](/images/play2-scala-ddd-scrum/3.jpg)

# アジャイル／スクラム開発
* GreenHopperなどのツール充実
  - これは旧称で現在は[JIRA Agile](https://www.ricksoft.jp/product/atlassian/jira-agile)という名称になっているようですね。
* [ドラッガー](http://ja.wikipedia.org/wiki/%E3%83%94%E3%83%BC%E3%82%BF%E3%83%BC%E3%83%BB%E3%83%89%E3%83%A9%E3%83%83%E3%82%AB%E3%83%BC)の書籍はアジャイルと相性が良いので[スクラムマスター](http://www.atmarkit.co.jp/ait/articles/1205/30/news130.html)の教育に入れている
* ユーザーの要求理解に時間をかける
* スクラムマスターが常にプレイングマネージャーであれるようにする
  - スクラムマスターが技術的な観点で理解していないと課題やtodoをブレイクダウンできない

# 関連書籍

<div>
<a href="http://www.amazon.co.jp/gp/product/4798121967/ref=as_li_qf_sp_asin_il?ie=UTF8&camp=247&creative=1211&creativeASIN=4798121967&linkCode=as2&tag=athome0a-22"><img border="0" src="http://ws-fe.amazon-adsystem.com/widgets/q?_encoding=UTF8&ASIN=4798121967&Format=_SL160_&ID=AsinImage&MarketPlace=JP&ServiceVersion=20070822&WS=1&tag=athome0a-22" ></a><img src="http://ir-jp.amazon-adsystem.com/e/ir?t=athome0a-22&l=as2&o=9&a=4798121967" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

<a href="http://www.amazon.co.jp/gp/product/4274068560/ref=as_li_qf_sp_asin_il?ie=UTF8&camp=247&creative=1211&creativeASIN=4274068560&linkCode=as2&tag=athome0a-22"><img border="0" src="http://ws-fe.amazon-adsystem.com/widgets/q?_encoding=UTF8&ASIN=4274068560&Format=_SL160_&ID=AsinImage&MarketPlace=JP&ServiceVersion=20070822&WS=1&tag=athome0a-22" ></a><img src="http://ir-jp.amazon-adsystem.com/e/ir?t=athome0a-22&l=as2&o=9&a=4274068560" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

<a href="http://www.amazon.co.jp/gp/product/4478410232/ref=as_li_qf_sp_asin_il?ie=UTF8&camp=247&creative=1211&creativeASIN=4478410232&linkCode=as2&tag=athome0a-22"><img border="0" src="http://ws-fe.amazon-adsystem.com/widgets/q?_encoding=UTF8&ASIN=4478410232&Format=_SL160_&ID=AsinImage&MarketPlace=JP&ServiceVersion=20070822&WS=1&tag=athome0a-22" ></a><img src="http://ir-jp.amazon-adsystem.com/e/ir?t=athome0a-22&l=as2&o=9&a=4478410232" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

<a href="http://www.amazon.co.jp/gp/product/4478012032/ref=as_li_qf_sp_asin_il?ie=UTF8&camp=247&creative=1211&creativeASIN=4478012032&linkCode=as2&tag=athome0a-22"><img border="0" src="http://ws-fe.amazon-adsystem.com/widgets/q?_encoding=UTF8&ASIN=4478012032&Format=_SL160_&ID=AsinImage&MarketPlace=JP&ServiceVersion=20070822&WS=1&tag=athome0a-22" ></a><img src="http://ir-jp.amazon-adsystem.com/e/ir?t=athome0a-22&l=as2&o=9&a=4478012032" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />
</div>

- - -
話を聞いていてちょっと感じたのは、内容が盛り沢山過ぎたかなと思いました。
それなりに早口で発表されていたのでちゃんとメモが取れなかったのが悔やまれます。。
Play2/Scalaについては実際に触ったことがないので聞いていて非常に勉強になりました。
またDDDやスクラムに関連付けて発表をされており、説得力が増していたような気がします。
この辺りは発表者の方のプレゼン技術と技術的な習熟度の高さを感じさせる上手さがあったかと。

あと最後に笑い取ってましたが[ドワンゴではC++に関わらず](http://developers.slashdot.jp/story/14/02/14/0421236/)エンジニア募集してるそうですｗ

