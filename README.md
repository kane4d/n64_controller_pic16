# n64_controller_pic16
Nintendo64のコントローラをPIC16F18326を介してMachiKania Type Mに接続します。
MachiKaniaだけで実装するべきですが、N64コントローラー1us単位の制御をNTSCと共存する自信が無かったため、別マイコン制御にしました。

## MachiKania type Mとの接続
- PIC16(PIN8-13)をPIC32(D0-D5)へそのまま接続
- PIC16(PIN1)をVddへ接続
- PIC16(PIN14)をGndへ接続

## N64コントローラーとの接続
- PIC16(PIN5, C5)をN64コントローラーのデータへ接続。PIC内部でWPUしてるので外部抵抗不要
- Vdd, Gndから電源供給

## キー設定
- 十字キーと黄色方向キーをカーソルキー
- A, B, ZがFireキー
- StartはStartキー

## シリアル接続
実装予定 KM-Basicへコントローラー全情報を転送
- 9600bps
- Serial On  L + C-Left
- Serial Off R + C-Right

## 試行錯誤
非力なPIC16Fで動くようにTIMER, Timer+Gate, CCP(Capture), IO Polling等のいろいろ方法でコーディングしましたが、Falling Edgeでの割り込みを採用しました。

## 移植
32MHz以上で動作するPICへ移植可能です。
MachiKaniaとの接続には必ずOpenDrainでドライブできるポートを割り当ててください。

## 参考サイト
### N64プロトコル
http://www.afermiano.com/index.php/n64-controller-protocol
### ライブラリ
シリアル接続でchanさまの組み込み用printfモジュールを使用する予定です
http://elm-chan.org/fsw/strf/xprintf_j.html
