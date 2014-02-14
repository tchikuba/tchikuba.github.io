---
layout: post
title: "ドワンゴ吉村総一郎氏「Play2/Scalaでドメイン駆動設計を利用した大規模Webアプリケーションのスクラム開発の勘所」@デブサミ2014 2日目"
date: 2014-02-14 16:50
comments: true
categories: [devsumi2014, Play2, Scala, DDD, scrum]
description: "2014年2月14日(金)に行われたデブサミ2014 2日目のセッションドワンゴ吉村総一郎氏「Play2/Scalaでドメイン駆動設計を利用した大規模Webアプリケーションのスクラム開発の勘所」を聞いた内容のまとめです。"
keywords: "デブサミ2014, Play2, Scala, ドメイン駆動設計, DDD, スクラム, scrum, PHP"
---

引き続きデブサミ2014。
ドワンゴ吉村総一郎氏によるセッション[「Play2/Scalaでドメイン駆動設計を利用した大規模Webアプリケーションのスクラム開発の勘所」](http://event.shoeisha.jp/devsumi/20140213/session/407/)を聞きました。
いろんなところで良く聞くPHPレガシーコードにどう立ち向かったのか聞いてみたかったです。

- - -

# profile
* [株式会社ドワンゴ](http://info.dwango.co.jp/) [吉村総一郎氏](https://twitter.com/sifue)
* ウォーターフォール開発とアジャイル開発の両方のマネージャー経験

# ニコニコ生放送を書き直す理由: コードの技術的負債
* PHPで書かれている:300万行！
* facebookで1000万行と言われているそう
* 1万行のクラスや4000行のメソッド
* 循環的複雑度600超のメソッドががが
  - あまりに複雑過ぎて龍の巣と言われている（笑）
  - まさに壊れかけのジェンガのよう
* 企画やスケジュールを優先するあまり品質を疎かにする開発体制

# どうやって？
* スモールスタート／スモールリリース
* 2週間に1度、ショーケースを実施
* 年末特番もクリアして今のところ大丈夫

# 裏話
* PHPは素晴らしい: 全てのコレクションをarrayで扱える
* Scalaはたくさんの型があるのでPHPerには辛く初学コストが高い
* 並行プログラミングの知識
  - Actor
* インフラ／アプリの垣根がボトルネックになったので席を近くするなどして改善
* クラウドではなくオンプレミスで
* DBはMySQL
* [gatling](http://gatling-tool.org/)が素晴らしいストレスツール

# DDD (Domain Driven Design: ドメイン駆動設計)
* Play2/Scalaでの開発と相性が良い
* DDD解説のYouTube動画が素晴らしい
  - [DevLove Building Blocks 都元ダイスケ](http://www.youtube.com/watch?v=FNEfk-dlIKU)
  - 社内勉強会で何度も視聴した
* ドメイン層の保守性向上に貢献する

<a href="http://www.amazon.co.jp/gp/product/4798121967/ref=as_li_qf_sp_asin_il?ie=UTF8&camp=247&creative=1211&creativeASIN=4798121967&linkCode=as2&tag=athome0a-22"><img border="0" src="http://ws-fe.amazon-adsystem.com/widgets/q?_encoding=UTF8&ASIN=4798121967&Format=_SL160_&ID=AsinImage&MarketPlace=JP&ServiceVersion=20070822&WS=1&tag=athome0a-22" ></a><img src="http://ir-jp.amazon-adsystem.com/e/ir?t=athome0a-22&l=as2&o=9&a=4798121967" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />

# 環境
* デプロイには[Capistrano](https://github.com/capistrano/capistrano)使用: [Mina](http://nadarei.co/mina/)にしようとしたが断念
* IDEは[IntelliJ IDEA Ultimate](http://www.jetbrains.com/idea/)に統一
* CIは[Jenkins](http://jenkins-ci.org/)
  - 現在scala5万行
  - 重複コード0
  - 行ベースのカバレッジ52%

# アジャイル／スクラム開発
* GreenHopperなどのツール充実
  - これは旧称で現在は[JIRA Agile](https://www.ricksoft.jp/product/atlassian/jira-agile)という名称になっているようですね。
* ドラッガーの書籍はアジャイルと相性が良いのでスクラムマスターの教育に入れている
* ユーザーの要求理解に時間をかける
* スクラムマスターが常にプレイングマネージャーであれるようにする

- - -
話を聞いていてちょっと内容が盛り沢山過ぎてちゃんとメモが取れなかったのが悔やまれます。。
Play2/Scalaについては実際に触ったことがないので非常に勉強になりました。
あと最後に笑い取ってましたがドワンゴではC++に関わらずエンジニア募集してるそうですｗ

