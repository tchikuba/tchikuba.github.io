---
layout: post
title: "Rails勉強会@東京#90に参加してきました"
date: 2013-12-21 20:00
comments: true
categories: [study, ruby, rails]
description: "rails勉強会@東京#90に参加してきたのでまとめを書きました"
keywords: "ruby, rails, 勉強会, TDD, テスト, OOP, オブジェクト指向プログラミング, DDD, ドメイン駆動設計"
---

[Rails勉強会@東京 第90回](http://railsmeetingtokyo.doorkeeper.jp/events/7642)に参加してきました。

非常に勉強になったのと嬉しかったのはいつもrails関連情報でお世話になってる[酒と泪とRubyとRailsと](http://morizyun.github.io/)のブログ書かれてる[@zyunnosukeさん](https://twitter.com/zyunnosuke)に初めて会えたこと。あと実は一度行ってみたかった[永和システムマネジメント](http://www.esm.co.jp/)さんのオフィス。アジャイル関連で有名な会社で在籍されている方の訳書などに色々お世話になっているので心の中で頭下げて来ました。最近のだとリーン開発の現場って本が熱い。(後述)

- - -

いつも参加している勉強会とは趣向が違い、予め決まったお題に沿って勉強会が進行するのではなく、今日参加したメンバーがやりたいことを持ち寄ってテーマを決めて進めるという、結構新しいスタイルでした。個人的には最初「結構行き当たりばったりなのね」って思ったんですが、実際に進行してみてこういう形式も悪くないなぁと感じた。そしてある意味その方が高度な勉強会だなと。

最初自己紹介した後、やりたいことを列挙して共通のもの＋挙手でテーマを決めるという感じ。
結局テーマは*「railsでのテストの基礎＋rails4.1.0beta1リリースノート読む or railsでOOPするには」*になり、後半はOOPに参加した。

以下にざっと話題になったコンテンツのURLを中心にまとめておきます。

### テスト関連

* [poltergeist](http://blog.livedoor.jp/sasata299/archives/51924944.html)
  - js含めたacceptanceテストやるならコレだねという話。
  - デフォルトのdriverだとseleniumだけどそれだとブラウザで重いからヘッドレスでブラウザエミュレータ上でテスト進めてくれる。
  - ポルターガイスト現象って勝手に物が動くことを指すけど、命名の由来もそこから来たんじゃないか。
* [herokuでrails](http://morizyun.github.io/blog/heroku-rails4-postgresql-introduction/)
  - 勉強会の中1hで何故か自分の時間が取られたんですがその間にpoltergeistを軽く触ってみようと思ってrails環境作ろうと思ってどうせならherokuでやってみようと思って参考にした記事。
  - また例によって@zyunnosukeさん。ありがとうございます！
* [.rvmrcから.ruby-gemsetと.ruby-versionに移行](http://qiita.com/prinum/items/ac9feadbbe497649ab3f)
  - rvm入れたりとこの辺の環境構築に思ったより時間がかかって結局勉強会の中1hではruby2/rails4な環境構築だけで終わってしまったというオチ。

- - -

### rails OOP
* [肥大化したActiveRecordモデルをリファクタリングする7つの方法(翻訳)](http://techracho.bpsinc.jp/hachi8833/2013_11_19/14738)
  - 最近仕事でコントローラーに寄った処理をリファクタリングしてて自分の中で課題感じている箇所。
  - この辺の課題感を最初の何やりたいで提示したら採用してもらえたので勉強会後半はこれについて半分のグループで議論することに。
* [DCI](http://dodemoyoiblog.blogspot.jp/2012/09/dci-data-context-interaction.html)
  - rails界隈で所謂普通の(DDDの流れから来る)OOP派とDCI派で一時期議論があったという話を聞いた。
  - 自分DCIという概念を初めて聞いたのでちょっと理解がまだ不十分なところもあるけど、modelとroleを分けて必要なコンテキストでroleをincludeしましょう、という設計思想の模様。
  - 個人的にはDDDとも親和性の高い考え方ではあるなぁと思った。特に上記ブログで紹介されている以下の部分、非常に共感出来ます。
  > *まずはビジネスロジックやユーザエクスペリエンスに基づいて大枠の設計がなされ、局所的な最適化に各種ツールが活用される。その優先度が逆転してはいけない。*
* [Ruby on Rails Advent Calendar 2013](http://qiita.com/advent-calendar/2013/ruby-on-rails)
  - rails OOP的な話は結構今年のadvent calendarでも色々ブログ書かれてたよね、という話があった。
  - 実際見返してみると確かに。以下のエントリが今の自分の課題感とマッチしてた感じ。
    * [てめえらのRailsはオブジェクト指向じゃねえ！まずはCallbackクラス、Validatorクラスを活用しろ！](http://qiita.com/joker1007/items/2a03500017766bdb0234)
    * [Railsでサービスとフォームを導入してみる話](http://a-suenami.hatenablog.com/entry/2013/12/06/092146)

- - -

### その他
* [MOGOK](http://mogok.jp/index.html)
  - 参加者の方が関わっているサービス。
  - 他にもミニ四駆のサイト趣味で作られている方がいたのですがどうも見つからない。。
    * 追記：@zyunnosukeさんが教えてくれました。[このサイト](http://mini4wg.com/)。
    * 全然どうでも良い話だけど、私もダッシュ四駆郎とかコロコロコミックで読んでた世代なのでミニ四駆やってみようかな〜
* [Joruri](http://joruri.org/)
  - wordpressみたいなrubyのプロダクトってあるの？って話から出てきた話題。
  - 実際に徳島では本当にたくさんのサイトがこれで作られてるんですねぇ。知らなかった。
  - [githubにソースあった](https://github.com/joruri/joruricms)んでチラ見してたんですがテストがなくコントローラーがちょっとレガシー入ってる感じではありましたけど何か面白そうだった。
* [Middleman](http://middlemanjp.github.io/)
  - CMSの流れで最近流行りの静的サイトジェネレータ。
  - 最近だとrubyでCMSやるならこれで良いんじゃないかという話が出てました。

- - -

### 関連書籍
個人的には前述のリーン開発の現場って本がずっと私が勉強会とかで主張してたことがまとまってる感じがして嬉しいです。
あとテスト関連だとthe rspec book、OOP関連だとエリック・エヴァンスのDDDがオススメ。

<iframe src="http://rcm-fe.amazon-adsystem.com/e/cm?t=athome0a-22&o=9&p=8&l=as1&asins=427406932X&ref=tf_til&fc1=000000&IS2=1&lt1=_blank&m=amazon&lc1=0000FF&bc1=000000&bg1=FFFFFF&f=ifr" style="width:120px;height:240px;" scrolling="no" marginwidth="0" marginheight="0" frameborder="0"></iframe>

<iframe src="http://rcm-fe.amazon-adsystem.com/e/cm?t=athome0a-22&o=9&p=8&l=as1&asins=4798121932&ref=tf_til&fc1=000000&IS2=1&lt1=_blank&m=amazon&lc1=0000FF&bc1=000000&bg1=FFFFFF&f=ifr" style="width:120px;height:240px;" scrolling="no" marginwidth="0" marginheight="0" frameborder="0"></iframe>

<iframe src="http://rcm-fe.amazon-adsystem.com/e/cm?t=athome0a-22&o=9&p=8&l=as1&asins=4798121967&ref=tf_til&fc1=000000&IS2=1&lt1=_blank&m=amazon&lc1=0000FF&bc1=000000&bg1=FFFFFF&f=ifr" style="width:120px;height:240px;" scrolling="no" marginwidth="0" marginheight="0" frameborder="0"></iframe>

- - -

ざっとまとめるとこんな感じかな。
個人的にはちょっと新鮮な空気の勉強会でしたがリアルな課題感をその場で確認することが出来るのでこういう形式はより実践向けで良いんじゃないかと思いました。
またスケジュールが合えば積極的に参加して行こうと思います。

### 追記
私が参加しなかったRails4.1betaリリースノートの話題は[@zyunnosukeさんのまとめ](http://morizyun.github.io/blog/rspec-changelog-rails-tokyo-90/)が詳しいです。さすがです！
