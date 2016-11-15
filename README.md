I love 半加算器
--------------

資料: slide/

## Introduction

今日はコンピュータを木で作る話をします。

## コンピュータを作りたい

なぜコンピュータを木で作りたいかというと、コンピュータの事をよく知りたいからです。
私は小学三年生からプログラムを書いてますが、コンピュータが大好きです。
そして、プログラマにとって理解するという事は、実装出来るという事です。
なので、コンピュータを作る事によってコンピュータを理解したいというのは当然の欲望という事になります。

## 色々な自作コンピュータ

とはいえ、コンピュータを作ると言っても色々なアプローチがあります。

* 一番良くあるパターンは、自作 PC を作るという物。私もいっときやってましたが、CPU と筐体とメモリとハードディスクをくっつけて PC を組み立てます。これも立派にコンピュータの理解に役立ちます。Arduino 等の電子工作もこれに当たると思います。

* 次によくあるパターンは、チップを買ってきてくっつけるという物。最近のマイクロコントローラは必要な回路がチップの中に入っているので、意外と簡単にコンピュータを組み立てる事が出来ます。

* 次に人気のあるのは、FPGA でコンピュータを作るという物。論理回路のレベルからコンピュータの動作を知る事が出来ます。

* 根強い人気の物は論理ゲート自体を自分で作る物です。半導体の自作は難しいので、上の方法と違って実用的な物を作るのは難しいのですが、レゴ、プラレール、マーブルマシン、スーパーマリオ、マインクラフト等での実装例があります。

今日の話はこの最後の論理回路を自作するという話です。

## ヒモと滑車を使ったコンピュータ

私自身がこういう世界と初めて出会ったのは高校生の頃です。この『別冊日経サイエンス 遊びの展開』という本を読んで衝撃を受けました。これに、なんとニューギニアの古代文明の遺跡からヒモと滑車で実装されたデジタルコンピュータが発見されたという話題が載っていたのです！

## ヒモと滑車を使ったコンピュータ

この本は絶版なのですが、大人になってから元ネタになった A.K.Dewdney the
Tinkertoy Computer を入手しました。

ここに遺跡から発掘された AND、OR、NOT といった基本的な論理回路の説明が
書かれてあるのですが、どうやらヒモの位置で 1 と 0 を表現していたようで
す。たるんだ状態が 0 で、引っ張った状態が 1 になっています。

例えばこの OR の例では、INPUT に出たどちらか一方のヒモを引っ張ると、
OUTPUT のヒモも引っ張られる事で OR を実装します。

AND の例はもうちょっとややこしくて、一方のヒモを引っ張ったらたるみの部
分が伸びるだけで、両方を引っ張って初めて OUTPUT も引っ張られるという理
屈で AND を実装します。

## コンピュータを木で作りたい

実はオチとしてはこの話はフィクションで、ニューギニアの話は作者の捏造な
のですが。コンピュータが大好きだった私はこの本を読んで自分でもコンピュー
タを作りたくなりました。

市販のコンピュータで使われる部品をバラした物をくっつけるとコンピュータ
が出来るというのは当たり前の話です。市販のコンピュータで使われる物と全
く同じ原理を使い、全く別の素材を使って実装する事で、初めてコンピュータ
を理解したと言えるのでは無いでしょうか?

つまり、コンピュータを細かく分解して原理を学習する帰納のプロセスだけだ
と、なるほどと納得して終わりですが、その原理を利用して全然違う素材でコ
ンピュータを作る事で、深く理解し新たな発見を見つけたいのです。

## Fibonnaci Engine

まず最初に作ったのがこれです。この頃はあまり論理素子の事が良く分かって
無くて、とりあえず足し算が出来る機械を作ろうとしました。矢印が二本突き
出ていますが、これは足のペダルで動かす事が出来ます。左の矢印は足の動き
に連動して上下に動きますが、右はラチェットの仕組みでリセットするまで上
にしか上がりません。これで例えば 3 + 4 を計算しようとすると、足をまず3
回回して 3 回戻す。そして 4 回回すと答えの矢印が 7 の位置を指すという理
屈です。

## 計算ガイコツ

この作品はどっちかというと厳密さよりも受けを狙った物だったのですが、あ
とでちゃんとした計算機も作りました。動作原理はこうです。

右側の輪っかを使ってまず数字を例えば 3 に合わせます。そのまま手を離すと
重りの力で右側の輪っかはゼロに戻るのですが、左はラチェットの仕組みでそ
のまま止まります。再び右側の輪っかを今度は 4 に合わせると、左の輪っかは
止まった所から回り始めるので結果 7 が骸骨の目玉の部分に表示されるという
仕組みです。

## 学んだこと

この二つの作品で学んだことは、どうも計算を実現するにはラチェット的な物
が要るという事です。ラチェットというのは、自転車なんかについてる部品で、
回転の力を一方向にだけ伝えて、逆は空回りする仕組みです。ラチェットが無
ければ、自転車で坂道を下る時に足をくるくる回さなくてはいけません。

歯車だけの組み合わせで足し算を実現する事は出来ません。この「空回り」が
計算の本質である事が分かりました。

歯車だけで実装出来る機械は、入力と出力が一対一で対応しています。例えば
入力を二倍する計算は歯車だけで実装出来ます。しかし、二つの数字の足し算
は複数の入力が一つの出力に対応するため、どこかで情報を捨てる仕組みが必
要になります。

## A.K.Dewdney のコンピュータを再現する

さて、次に挑戦したのは先ほどの糸と滑車のコンピュータの実現です。私の計
算機と違って、これは論理素子の実装です。実用的にはより役に立たない方向
性ですが、実はこっちの方がより現実のコンピュータに近いのです。

## 2008年: 段ボールによるブール代数モデル

まずはダンボールで試作しました。プルタブがゴムで常に引っ張られる状態に
なっていて、二つの腕のうち一つでも引っ張られるとプルタブが引き上げられ
る仕組みです。これで OR を実装したと言えます。

## 学んだこと

Dewdney の一見簡単そうな仕組みも作ってみると意外と難しい事が分かりまし
た。さらに複数の部品を組み合わせるとなると相当簡単なしくみを使わなくて
はならないです。なので、AND の実装は諦めて、OR と NOT だけで作る事にし
ました。AND は OR と同じ機構を使って、入出力の意味を逆転するだけで代用
する事が出来ます。

## 表記法の開発

また、実体を描いて設計すると大変なので、ヒモを使った論理回路を表現する
のに適切な新たな表記法を開発しました。

この表記法では、四角い箱が状態を表していて、上が黒い時が ON で下が黒い
時が OFF です。三角形がゲートを表していて、片方でも引っ張られると答えの
状態が引っ張られるという事を示しています。

これと引っ張りの方向を明記すると、論理回路が実現出来ているのがわかります。

## 半加算器を木で作りたい

また、実装対象としては半加算器を選びました。課題としてそれなりに複雑で、
色々な人が既に作っているため、ベンチマークとして最適であると判断しまし
た。

あとは論理回路をそのまま新表記法に翻訳し、物に置き換えてゆくだけです。

## 2008年: 糸と重りの半加算器

そして完成したのがこの糸と重りの初代半加算器です。

## 2009年 木製半加算器

これは作りがちゃちいため長時間の展示や、知らない人に触ってもらうという
用途には無理だったので、強度と安定度をアップさせた木製半加算器を作りま
した。

## 2016年 木製半加算器 2016

さらに、スライド機構から回転機構への変更によって抵抗を削減し、全加算器
実装への布石となる新型を今年発表しました。

## 次の目標

----

* 1800 文字で 5 分
* 7200 文字で 20 分

## References

* A.K.Dewdney the Tinkertoy Computer https://archive.org/details/tinkertoycomputer00dewd
* 関数と写像: https://en.wikipedia.org/wiki/Function_(mathematics)
* 別冊日経サイエンス コンピューターレクリエーション 4 遊びの展開 http://www.nikkei-science.com/page/sci_book/bessatsu/51113.html
* 糸と重りの半加算器: http://d.hatena.ne.jp/propella/20081124/p1
* Wooden Half Adder: http://propella.blogspot.jp/2009/11/wooden-half-adder.html


http://metatoys.org/alligator/ 見せる?
