YAMAHA series documents
==================================

概要
----------------------------------

YAMAHAシリーズ（主にルーター）の備忘録兼のドキュメントです。  
個人的に学習したことを記述していきます。  
主にRTX1200。VoIPルーターとしてNVR500とかも連携してみたい。  
WLX320も使ってみたいけど金欠だし、バグが多いらしいのでどうなんだろ。様子見？

よく使う操作のチートシート
----------------------------------

### 設定をUSBにバックアップ・リストアする

* バックアップ

```
copy config 0 usb1:/rt_config-201312142222.txt
```

* リストア

方向を逆にすればいい。再起動しないと反映されない。

```
copy config usb1:/rt_config-201312142222.txt 0
restart
```

### 出荷時設定に戻す

```
cold start
```

### ファームウェアのアップデート

再起動しないと反映されない。

```
copy exec usb1:/rtx1200.bin 0
restart
```

リンク集
----------------------------------

### 設定例

- [設定例](http://jp.yamaha.com/products/network/solution/?products=rtx1200&solution=&submit=%E7%B5%9E%E3%82%8A%E8%BE%BC%E3%82%80)

### ファームウェア

- [firmware release for Yamaha Network Products](http://www.rtpro.yamaha.co.jp/RT/firmware/)

### ほか

- [外部メモリファイルコピー機能](http://www.rtpro.yamaha.co.jp/RT/docs/external-memory/copy.html)
