# 詳細ドキュメント



### FAフレーム3x3＠フキダシアリス

最初にこのフレーム用のスクリプトでフキダシの下地を描画します。ここでは角の丸い四角形バルーンを描画しています。

| FAフレーム3x3だけを有効にした図 | せってい |
----|----
| <img src="https://tiribro.github.io/FukidashiALICE.anm/img/one_chance_step001.jpg"> | <img src="https://tiribro.github.io/FukidashiALICE.anm/img/prop_001.png"> |

このスクリプトはほどほどにお利口さんなので、テキスト設定から自分で丁度良いサイズにバルーンを背面描画してくれます。
一つだけ __注意点__ として __「文字毎に個別オブジェクト」非対応！！__ です。一切です。ご了承ください。お願い致します。

このフレームは文字通りフレーム描画スクリプトです。与えられた画像を3x3のタイルとして認識し、任意のパラメータに従って伸縮し、背景にフィットします。次のテーブルをチェックしてください。丸角素材はお持ち帰りいただいて構いません。

| 参照ファイル | 出力イメージ |
----|----
| <img src="https://tiribro.github.io/FukidashiALICE.anm/img/soft_sq3x3_grid.png" width="300"> | <img src="https://tiribro.github.io/FukidashiALICE.anm/img/one_chance_step001_00g.jpg"> |
| <img src="https://tiribro.github.io/FukidashiALICE.anm/img/soft_sq3x3_1080w.png" width="300">（ここに白くて角の丸い四角画像があるようだ・・・） | <img src="https://tiribro.github.io/FukidashiALICE.anm/img/one_chance_step001.jpg"> |
| <img src="https://tiribro.github.io/FukidashiALICE.anm/img/soft_sq3x3_1080b.png" width="300"> | <img src="https://tiribro.github.io/FukidashiALICE.anm/img/one_chance_step001_00b.jpg"> |

#### パラメータ (FAフレーム3x3)

##### 幅px
> バルーンの幅を指定します。PADDING MODEがONの時には、元のイメージサイズを指定pxだけ水平方向に拡大します（PADDING MODEがOFFの時にはそのまま横幅pxとしてクリップします）

##### 高px
> バルーンの高さを指定します。PADDING MODEがONの時には、元のイメージサイズを指定pxだけ垂直方向に拡大します（PADDING MODEがOFFの時にはそのまま高さpxとしてクリップします）

##### 枠px
> 外枠を実際にどれだけの太さで描画するか指定します。大きくすると、参照された3x3素材のうちの、外枠のタイルが太く描画され、ゼロにした場合は中心のタイルだけが描画されます

| 枠px：25 | 枠px：75 |
----|----
| <img src="https://tiribro.github.io/FukidashiALICE.anm/img/one_chance_step001.jpg"> | <img src="https://tiribro.github.io/FukidashiALICE.anm/img/one_chance_step001_round.jpg"> |

##### 下地a
> フレームを描画する前の画像を、フレームの上にどれだけの透明度で描画するか決めます。
>> 0 ～ 100 : 元の画像をフレームの上に指定の透明度で上書きします  
>> -100 ～ 0 : 元の画像をフレームの下に指定の透明度で上書きします（透明度は絶対値）

### FAピン＠フキダシアリス

ピンを与えます。

| FAフレーム3x3＋FAピン | せってい | 参照ファイル |
----|----|----
| <img src="https://tiribro.github.io/FukidashiALICE.anm/img/one_chance_step002.jpg"> | <img src="https://tiribro.github.io/FukidashiALICE.anm/img/prop_002.png"> | <img src="https://tiribro.github.io/FukidashiALICE.anm/img/delta.png">（ここに白い三角の画像があるようだ・・・） |

ピンが付きました。

#### パラメータ (FAピン)

##### 位置
> ピンは下地になる四角形の辺にそって設置されます。
>> 0-100 : 上辺  
>> 100-200 : 右辺  
>> 200-300 : 底辺  
>> 300-400 : 左辺  

##### 幅px, 高px
> ピン画像の描画サイズを指定します。マイナスの値を指定すると元画像サイズで描画されますが、たいして便利な機能ではありません。少し大きめにピン画像を作り、このスライダーをいじってピンのサイズを調整しましょう。

##### 曲げpx
> ピンの先端を下地の四角辺と平行にスライドすることで、ピンの方角をアレンジします。

### FAシャドウ＠フキダシアリス

非常にキメラなシャドウ生成フィルタです。２重縁取り＞単色化＞背面オフセット描画フィルタですが、何が何だかわかりません。ケーススタディでアプローチしましょう。

| FAフレーム3x3＋FAピン＋FAシャドウ（一回目） | せってい１ | せってい２ |
----|----|----
| <img src="https://tiribro.github.io/FukidashiALICE.anm/img/one_chance_step003.jpg"> | <img src="https://tiribro.github.io/FukidashiALICE.anm/img/prop_003.png"> | <img src="https://tiribro.github.io/FukidashiALICE.anm/img/prop_003a.png"> |

外側にボーダーラインが描画されました。詳細設定画面をチェックしてください。縁取り以外なにも指定されていません。
この設定であれば縁取りフィルタを二重でかけることと等価ですが、せっかくなので自スクリプトを使用しています。
縁取りが処理される順番は最初に縁取り1、次に縁取り２が実行されます。

次にFAシャドウをもう一度かけますが、ここで本来の目的を果たします。FAシャドウは「影を背面にずらして描写する」フィルタとして動作します。
差がわかりにくいので、前後のイメージを比較しましょう。

| FAフレーム3x3＋FAピン＋FAシャドウ（一回目） | FAフレーム3x3＋FAピン＋FAシャドウ（一回目）＋FAシャドウ（二回目） |
----|----
| <img src="https://tiribro.github.io/FukidashiALICE.anm/img/one_chance_step003.jpg"> | <img src="https://tiribro.github.io/FukidashiALICE.anm/img/one_chance_step004.jpg"> |

バルーンがやや上にスライドして、その背後にシャドウが描写されています。
左の画像をもとに、さらに二重で縁取りぼかしをかけて単色化し、
生成したシャドウイメージの上に加工前の画像をずらして上書き復元したものが、右の画像です。

| FAフレーム3x3＋FAピン＋FAシャドウ（一回目）＋FAシャドウ（二回目） | せってい１ | せってい２ |
----|----|----
| <img src="https://tiribro.github.io/FukidashiALICE.anm/img/one_chance_step004.jpg"> | <img src="https://tiribro.github.io/FukidashiALICE.anm/img/prop_004.png"> | <img src="https://tiribro.github.io/FukidashiALICE.anm/img/prop_004a.png"> |

#### パラメータ (FAシャドウ)

##### X,Y
> 最後に上書きされるオリジナルイメージを任意の量だけスライドします。「本体をオフセットする」がOFFのときは、シャドウ側をずらして描画します

##### 透明度
> シャドウの透明度です

##### 設定＞最後に単色化する
> 単色化を抑止します。OFFにすると、背後のシャドウを色付きのままにしておけます。（これは何？：このオプションは、縁取りでつけた色が単色化により消えることを抑止しますが、位置をスライドすると色付きのぼやけたイメージが露出してしまうため、スライドしない時にだけ役に立つオプションです）

##### 設定＞単色化の色
> シャドウ単色化するときの色

##### 設定＞縁取り1, 縁取りのサイズ1, 縁取りのぼかし1, 縁取りの色1
> 縁取り１回目のスイッチです。ONで縁取りが実行されます。また、縁取り１回目のサイズ、ぼかし、縁の色を指定します。

##### 設定＞縁取り2, 縁取りのサイズ2, 縁取りのぼかし2, 縁取りの色2
> 縁取り２回目のスイッチです。サイズ、ぼかし、縁の色を指定します。

#### 設定＞アルファFadeIn／Out
> フェード秒数を指定します。0より大きな秒数を指定した場合、開始/終了時に透明度によるフェードを行います

#### 設定＞オフセットFadeIn／Out
> フェード秒数を指定します。0より大きな秒数を指定した場合、開始/終了時にX,Yのオフセットがフェードします










