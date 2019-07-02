やりかけ

![post](https://github.com/HiragiEnoki/iroiro/blob/master/interposer/P1000738.JPG)

# ■ELI-Interposerとは

ELI-Interposerは私，ひいらぎえのきのmeishiです．USBハブ，バースイッチ付きの6キーマクロパッドになる予定でした．  

といっていても意味がわからないのでちょっとだけ解説をしたいと思います．  本記事はbuildlogではなく，design-logであり，build-logとなります．

- design-log
	- 発端
	- 要件定義
	- 開発
- build-log
	- BOM
	- 実装対応表
	- 作成


## ■design-log  

### ●発端
funnel-A4を組み上げ，安心しきった私を待っていたのは先達からの熱いはげましのお言葉だった……

![post](https://github.com/HiragiEnoki/iroiro/blob/master/interposer/postA.JPG)
![post](https://github.com/HiragiEnoki/iroiro/blob/master/interposer/repA.JPG)
![post](https://github.com/HiragiEnoki/iroiro/blob/master/interposer/repB.JPG)

※プライバシーに配慮してモザイクを掛けています．

自キ勢怖いわ～，  
やるかあ，となったのがゆるキー2週間前の日曜朝一時のことでした．


### ●要件定義

時間がない．なにをするにもまずは要件定義が大事だと思います．  
- 名刺とは何か？を考えた  
	名刺は自分の名前を紹介し，必要であれば備忘録となることで人と自分をつなげるものだと考えました．で，  
	- でかいシルクロゴ
	- USBハブ機能  
をメインの要件としました．物理的に人（のキーボード）とつながっていくぅ！！！  
こいつキモチワルいな  
サブ要件として下記を定義します．  
	- 6キー+バースイッチ  
キーの数はhifumi（かわいいっすよね）と同数，あとついでに試してみたかったバースイッチを突っ込んでます．  

ここで基板の名前を決めてしまいます．名前決まんないとlogoデザインができないし……  
特にひねりもなく <u>ELI **〈Interposer〉** trial</u> としました．私のすべての生成物がELIのプロダクトとなるのだ．  
インターポーザーってのは，シリコンダイのピッチを変換してPWBに実装しやすくするための基板ですね．  
今回は基板のサイズ的にUSB一口を二口へ変換するのが関の山というところでしょうか．




### ●開発
特になにも考えてない  

- 6キー+バースイッチ  
	- PWBを縦方向に向けるとちょうどよい
		- シルクのための面積も多く取れる
- hub回路
	- 周辺回路込みで2x3のサイズに収める
- でかいシルクロゴ
	- シルクのために背面は可能な限りキレイに仕上げる  
　	（＝ビアの数を最小限にする，背面に部品実装しない．）

USBハブの回路をどうしようか考えましたが，周辺回路込で一番小さくて安い[コレ](http://www.aitendo.com/product/16185)を中央に据えることにしました．一石で四口まとめて一口にできるやり手です．購入経路がaitendoだけってのが気に入らねえけどまあいいでしょう．困るのがどうやって32u4と接続するかなんですが，promicroを載せてusbケーブルってのはダサくてやだったので何も考えずにprimicroを平面展開(違う)してます．  meishiってそういうんじゃないよねというのに配ってから気づいた．

ここまでをキメてからkicadをインストールし，foostanさんの[コレ](https://github.com/foostan/mkbd/blob/master/developers_guide/developrs_guide_jp.md)とかまーくさんの[コレ](https://marksard.github.io/2019/04/25/about-treadstone32/)とかを読みながらai03さんの[コレ](https://wiki.ai03.me/books/pcb-design/page/list-of-kicad-keyboard-parts-libraries)とかdegikeyの[コレ](https://www.digikey.jp/ja/resources/design-tools/kicad)とかをインストールして，  
もげないマイクロの回路図とかaitendoのUSBhubサンプルスケマチックを参考に回路図を作り，digikeyと秋月とにらめっこしながら買える部品の中から部品を選んでアートワークを行いました．こういう無茶をしたりなどした．  
![logo](https://github.com/HiragiEnoki/iroiro/blob/master/interposer/D9Dbc5SU8AIf7vv.png)  
土曜午前三時の作業がこの後悲劇を招くのであった……

シルクはクリスタでさくさくやっていくスタイル．ほめてもらえてうれしいですね．ほかにほめるところがなかっただけ？まあ……  

↓シルク  
![logo](https://github.com/HiragiEnoki/iroiro/blob/master/interposer/Interposerlogolight-1p5%20(1).jpg)

このあと私の名前が変わった．

あとはALLPCBにデータ投げて終わり．土曜日朝7時のことでした．

![mini](https://github.com/HiragiEnoki/iroiro/blob/master/interposer/dakkou.JPG)



このあと，泣きながらBOMをdegikeyに投げたり秋月に投げたりしている最中，usbコネクタのフットプリントに間違えてmini用のプリントを割り付けていることに気づいて大爆笑したりなどした．

## ■buildlog
### ●BOM
（工事中）
### ●対応表
（工事中）


### ●実装
ゆるキー前日，金曜の夜に基板が届くというアレな自体に陥るが動くか動かないかわからないものは配れないということで組んでみることに．  
おれの頭の中にあるbuildguideにしたがって組んでいくといろいろとアレなところが見つかりつつもまあなんとか組み終わって，じゃあファームでも書き込むかと思ってPCにつなげたら  

ブツン

とPCが落ちてですね．それからはまあてんやわんやですよ，aitendoやりやがったなと思いながらfeを取り外してみたり，32u4で雑なことしたのが悪いのかとdatasheet読んでみたり，どこかでGNDに落ちてないかテスターで当たりまくってみたりとしてみたんですが，  
- USBのコネクタだけなら落ちない
- そこにfeiをつなぐと落ちる
- fe1.1を外してUSB–32u4直でも落ちる

……これはおかしい，というところで思い出したのがmini-micro取り違え事件．回路図を見る．フットプリントを見る．また回路図を見る．フットプリントライブラリを……  あれ……microとminiってピン配逆なの……？  
それ！！！！！！！！！それですわ！！！！！！！！！！！！！  

![kuso](https://github.com/HiragiEnoki/iroiro/blob/master/interposer/dainasi.JPG)
<blockquote class="twitter-tweet" data-lang="ja"><p lang="und" dir="ltr"><a href="https://t.co/mbwbVpCJ56">pic.twitter.com/mbwbVpCJ56</a></p>&mdash; Molg H. (@molgh) <a href="https://twitter.com/molgh/status/726854917214879744?ref_src=twsrc%5Etfw">2016年5月1日</a></blockquote>


泣きながらジャンパで逆順になおしたら動いたのでやっぱりこういう感じでしたね．  

![kuso](https://github.com/HiragiEnoki/iroiro/blob/master/interposer/P1000734.JPG)

aitendoは悪くなかった．

あとはクソが誰がこんなもん考えたんじゃいと思いながらストックしてあったミニ四駆のパーツでスイッチバーを組んで終わりです．  
いやコレ……配れんわな，ということでゆるキー会場では何人かに押し付けておわりでした．rev.アップしてもう一回発注したいですね．


おわり