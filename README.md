# n64_controller_pic16
Nintendo64のコントローラをPIC16F18326を介してMachiKania Type Mに接続します。

## MachiKania type Mとの接続
- PIC16(PIN8-13)をPIC32(D0-D5)へそのまま接続
- PIC16(PIN1)をVddへ接続
- PIC16(PIN14)をGndへ接続

## N64コントローラーとの接続
- PIC16(PIN5, C5)をN64コントローラーのデータへ接続。PIC内部でWPUしてるので外部抵抗不要
- Vdd, Gndから電源供給


