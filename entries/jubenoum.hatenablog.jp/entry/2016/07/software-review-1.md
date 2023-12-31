---
Title: ソフトウェア設計レビューの効果を高めるには（技法編）
Category:
- Experience
- システム
- 開発
- Column
Date: 2016-07-18T10:00:00+09:00
URL: https://yourpalm.jubenoum.com/entry/2016/07/software-review-1
EditURL: https://blog.hatena.ne.jp/atauky/jubenoum.hatenablog.jp/atom/entry/6653812171406069789
---

[f:id:atauky:20160717234232p:plain]

最近、品質に問題あり、障害多発とされたチームにヘルプで入ることになり、
レビューのやりかたや、進めかたを観点にいろいろ分析をしています。

そこで、ソフトウェアの品質管理やレビュー技法に関する本や
IT系サイトでネタを集めていたのですが、まとめると、技法と
マインドなのだなと考えた次第です。

まず、***技法***に着目してまとめてみたいと思います。



<!-- more -->



## レビューの技法

同じ名前がつけられていても、本やホームページごとに同じ言葉でも
内容にばらつきがあって、実際のところどうやねん、というのが正直な感想でした。

だいたい上から開催するのが面倒とされる順にならんでいます。

* インスペクション
   * 事前に定められた手順とチェックリストに従って第三者がレビューを行う、最も形式的（フォーマル）なレビュー手法
* テクニカルレビュー
   * インスペクションとウォークスルーの間くらい
* ウォークスルー
   * レビューを希望する作成者が数人のレビューアを招集、成果物の内容を順に説明する形式をとる。それに対してレビューアは、説明を通じて対象を追跡・検証し、その誤りや矛盾、抜け漏れなどを指摘する
* パスアラウンド
   * レビュー対象となる成果物を電子メールなどで複数のレビューアに配布・回覧し、フィードバックを求める方法
* アドホックレビュー
   * 必要に応じて身近な同僚や手すきの仲間に成果物を見てもらう非公式レビュー

## レビュー技法を要素に分割

よくわからないなら要素に分割してしまえ！

1. 会議を開くか、開かないか
1. プロジェクト外の第三者を参加者とするか
1. レビュー記録を残すかどうか
1. (会議をする場合)資料の事前配布はするか、しないか
1. (会議をする場合)資料の事前欠陥摘出はするか、しないか
1. (会議をする場合)専任の司会者をたてるか、たてないか
1. (会議をする場合)専任の書記をたてるか、たてないか

3.-7.については、会議をする場合の効果を上げるためのやりくちです。

<dl>
 <dt>会議</dt>
 <dd>事前に場所と時間を定め、3人以上で時間と空間を共有する場とします</dd>
 <dt>プロジェクト外</dt>
 <dd>当該プロジェクト内の隠語が通じない程度の部外者とします</dd>
</dl>

上記、5つのレビュー技法を下記のとおりの要素にわけて表にします。
情報源によって、定義がばらばらなので、参考程度に。


| 技法            | 会議 | 第三者 | 記録 | 配布 | 摘出 | 司会 | 書記 |
| :------------- | :-- | :--- | :-- | :-- | :-- | :-- | :-- |
| インスペクション   | 開く  | 必須 | 残す | する | する | 専任 | 専任 |
| テクニカルレビュー | 開く  | 任意 | 残す | する | 任意 | 専任 | 専任 |
| ウォークスルー    | 開く  | 任意 | 任意 | 任意 | 任意 | 作成者 | 任意 |
| パスアラウンド    | 開かない | 任意 | 残す | N/A | N/A | N/A | N/A |
| アドホックレビュー | 開かない | 任意 | しない | N/A | N/A | N/A | N/A |


## 前提

以降、上記7つの要素ごとにメリット・デメリットを確認したいと思いますが、
まずレビューにおける前提を確認します。

### 設計レビューの目的

設計工程の成果物における欠陥の摘出です。
後続のテスト工程で欠陥が検出されると、対応のコストは高くなります。

### レビューア

レビューアとして、指摘する人には指摘するだけの知識と技量があるものとします。
どの程度の技量が必要かなどは、現場で決めてくれ！

## 要素別

狙いと懸念、懸念への対策の流れで記述します。

* 会議
* 第三者の参加
* レビュー記録
* 事前の資料配布
* 事前の欠陥摘出
* 専任の司会者
* 専任の書記


### 会議
#### 開く

[f:id:atauky:20160718020027j:plain]

会議を開いて、複数人で顔を合わせてレビューすることで、お互いの意見に触発されて
新しい指摘がされる効果を期待します。
また、レビュー本来の目的とは異なりますが、新規メンバーを参加させることで
教育効果をあげることも期待できます。

参加者に招集をかける調整コストがかかりますが、事前に固定の時間帯をレビューの
ために確保するように決めておけば、調整の労力を軽減できるでしょう。



#### 開かない

[f:id:atauky:20160718015939j:plain]

会議を開くことが時間的（忙しい）、空間的（国を跨いでレビュー開催）
な理由で難しいこともあります。
そこで技法として「パスアラウンド」を選択し、資料をメールや
ファイルサーバのポインタを示すことで配布して
各自の指摘結果を集めることもありますが…

* やっぱり忙しいのでそんなに内容確認できない
* 複数から同じ指摘が発生した場合、とりまとめ後排除が必要
* 複数から矛盾する指摘が発生した場合、意見調整が必要
* 顔合わせをしないので、参加者相互のかかわりから
 触発されて新しい指摘がされる効果は期待できない

といったあたりが懸念されます。

* 時間的問題については、誤字脱字以外の指摘のひとりあたりノルマを与える
* 空間的問題については、Skypeのツールを用いて解決をはかる

などで対策が取れそうです。

### 第三者
#### 参加する

プロジェクト外の第三者が参加することで、プロジェクト内で
暗黙の前提となっている事項の指摘がされることが期待されます。

調整の面倒さが増すことが懸念されます。
特定の設計成果物については第三者のレビューを必須とするというコンセンサスの醸成、
ルールを組織内に根付かせるなどしておくのが対策になるでしょう。

#### 参加しない

参加する場合とは逆に「ひとりよがり」の記述ばかりになることが懸念されます。
暗黙の前提が記載されないままの設計書は新規参画者の参画の際の教育コストを
高める結果につながったりします。

とはいえ、全部が全部第三者参加のレビューにかけられるかというと
それもまた現実的ではないかもしれませんので、
ある程度経験をつんだ他プロジェクト担当者が、アサインされた際に
疑問に思う点を指摘してもらうという手が考えられると思います。

### レビュー記録
#### 残す

記録を残すことで

* 漏れのない指摘修正
* 残された記録をもとにした、組織的品質改善

が期待されます。

レビュー記録を残す場合の懸念は、

* 指摘件数や、被指摘件数が人事評価につながらないようにすること
* 誤字脱字など軽微な問題の指摘や対応で時間が取られること

が考えられます。

* レビュー指摘件数を人事評価につなげないようにする、
* 誤字脱字は事前または事後にまとめて解消するステップをもうける

という対応で、余計な不安や指摘で時間をとられないようにしましょう。

#### 残さない

レビュー記録を残すこと自体に手間がかかるので、残さずにすむと楽です。
ただ、残す場合のメリットはなくなり、指摘修正漏れ、ノウハウが組織として残らない
といった問題が生じることが懸念されます。

立ち話のように気楽に行なわれる「アドホックレビュー」を実施した場合でも
別途ウォークスルー開催時のレビュー記録に記載できるよう、指摘内容を
メールで残しておく…などの工夫が必要と考えます。


### 資料の事前配布
#### する

資料の事前配布をすることで、参加者に事前に内容を確認してもらい、
本番の会議の際に指摘する事項の方針を考えてもらい、実際に
顔を合わせての会議の時間の有効活用を目指します。

目を通してくれないことが懸念点となります。

もし読んでくれなかった参加者がいる場合は、
会議開始10分は資料に目を通す時間として、
他の参加者は休憩時間にするなどの会議運営とするのが
対策になると思います。

### しない

（割愛）



### 資料の事前欠陥摘出
#### する

資料の事前配布に加え、事前に欠陥を摘出してもらうことで、
本番の会議では、会議開催の効果で最も期待される
お互いの意見に触発されて新しい指摘がされる効果を期待します。

事前配布と同様、目を通してくれないことが懸念されますが、
どうしても読んでほしいような重要なレビューの場合は、

* 指摘事項リストを事前提出できなかったレビューアは不参加とする
* 提出しなかったレビューアの評価が下がることを周知する

などして読ませるように仕向けるのがよさそうです。

会議のめんどくささが上がるにつれて、組織的ルールでしばらないと
まともに開催できなくなるように思いますので、ここは管理側の腕の
見せどころですね。

### しない

（割愛）

### 専任の司会者
#### たてる

専任の司会者をたてることで、レビュー時間を有効に活用することができます。
効果について具体的な内容は下記URL参照。


[http://www.itmedia.co.jp/im/articles/1004/14/news100.html:embed:cite]




懸念としては、レビューに関するコストということになりますが、
インスペクションのようにルールとして、専任の司会をたてることを必須とする
ような場合以外は、費用対効果を見て判断することになるでしょう。

#### たてない

たてない場合は、作成者が設計書の気になるところを中心に
話題にあげていくことになると思います。
その場合には、作成者の考え方、理解度をはかることはしやすくなると
思いますが、作成者の気にしている点に確認ポイントが集中しすぎ、
その他のポイントの指摘が漏れる点が懸念されます。

レビュー参加者全員が司会者…というかファシリテーションの
意識を持っているようなチームであれば、うまくいくかも…ということで
ファシリテーションの研修を受けるというのが対策になりうると考えます。


### 専任の書記
#### たてる

司会者と同様、レビューアに役割に専念してもらうことで、
レビュー時間を有効に活用することができます。

懸念も司会者同様コストとなりますが、

* レビューが集中する期間に時間単価の比較的安い専任の書記を雇う
* プロジェクト新規参画者に担当してもらう（教育も兼ねる）

などして、設計者、指摘者が本来の役割に集中できるようにしたいです。

#### たてない

専任の書記をたてない場合、作成者が記録を残すのがまだよいかなと思います。
ただし、その場で修正せず、指摘を記録することに集中することです。
そうしないと、「記録」がきちんと残せない危険が出てきますので。


-------

以上、まとめると、

* 気軽にやるものは、組織としてノウハウが蓄積できないデメリットが発生しやすい
* 会議をする調整が面倒なレビューは、メリットを享受する「組織」がメンバーに対して「しばり」をかけないと効果が出ない

ということになります。

次は「マインド」についてまとめたいと思います。

## 参考資料


[asin:B01683BFJM:detail]


[asin:4817192631:detail]


[http://itpro.nikkeibp.co.jp/article/COLUMN/20100714/350299/:embed:cite]

[http://itpro.nikkeibp.co.jp/article/COLUMN/20100714/350301/:embed:cite]

[http://qiita.com/mima_ita/items/c3490ad1ccc12ad853f1:embed:cite]




