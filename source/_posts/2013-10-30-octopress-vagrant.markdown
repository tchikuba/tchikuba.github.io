---
layout: post
title: "Octopressブログ環境をVagrantのboxで複数マシンで使う"
date: 2013-10-30 20:00
comments: true
categories: [octopress, vagrant]
---
Linuxで整えたOctopressでブログ書く環境をWindowsとMacでもそれぞれ作りたかったのとrubyのバージョンとか揃えるの億劫だしそれぞれ作るの面倒だなと思ったけど、既にvagrantな環境誰か作ってんじゃね？と思ってググったらありました。

> [octopress-vagrant](https://github.com/aequasi/octopress-vagrant)

世の中考えることは一緒ですね！

というわけで早速vagrant upしたらすぐにvirtualboxにてブログ書ける環境を整えることが出来ました。
手順は以下に。

* リモートリポジトリ(私の場合Bitbucket)とGitHubにゲストOS側のssh公開鍵を追加登録
* Vagrantfileのポート4000番のフォワード設定を追加
* ubuntuのデフォルトロケールを日本語に変更
* リモートリポジトリからOctopressソースをgit clone
* rake generateを叩いて[octopress root]/publicにhtmlの実態を生成

これでホストOSから`http://localhost:4000`にアクセスするとvirtualbox上で動いているゲストOSに構築されたブログが見えるようになります。
後は[Packer](http://www.packer.io/)でboxイメージも共有すると良いかもしれません。

余談ですが、DevOps面白いですね！
PHP開発環境をxampp/mamppとかで作ったり手動でVMWare上でVM開発環境作ったりして格闘してた経験のある私としてはホント良い時代になったなぁと痛感する次第。
