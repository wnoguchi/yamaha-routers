初期設定
=========

管理者パスワードの設定
----------------------

- 出荷時設定に戻す。

```
cold start
```

- 管理者モード移行。

```
administrator
```

- 文字コードをASCIIに。Macとかだと文字化けしてかなわない。

```
console character ascii
```

- 一般ユーザーパスワード設定。

```
# login password 
Old_Password: ←空パスキーイン
New_Password: ←パスワード設定 
New_Password: ←パスワード設定（確認） 
```

- 管理者ユーザーパスワード設定。

```
# administrator password 
Old_Password: ←空パスキーイン 
New_Password: ←パスワード設定 
New_Password: ←パスワード設定（確認） 
```

- 保存を忘れずに。

```
# save 
Saving ... CONFIG0 Done .
```

その他もろもろ
---------------

- 1時間でログインが切れるようにする。

そのままだと5分ぐらいで切れて設定作業では支障が出るから。

```
login timer 3600
```

LAN1インタフェースにTCP/IP設定
------------------------------

- LAN2/LAN3はWAN側に割り当てる。

### LAN1のIPアドレスを設定する。

以下は `192.168.0.1` をサブネットマスク `255.255.255.0` で割り当てる設定。

```
ip lan1 address 192.168.0.1/24
```

この時点でもう telnet が使える。

```
% telnet 192.168.0.1
Trying 192.168.0.1...
Connected to 192.168.0.1.
Escape character is '^]'.

Password: 

RTX1200 Rev.10.01.53 (Mon Sep  9 15:23:58 2013)
  Copyright (c) 1994-2013 Yamaha Corporation. All Rights Reserved.
  Copyright (c) 1991-1997 Regents of the University of California.
  Copyright (c) 1995-2004 Jean-loup Gailly and Mark Adler.
  Copyright (c) 1998-2000 Tokyo Institute of Technology.
  Copyright (c) 2000 Japan Advanced Institute of Science and Technology, HOKURIKU.
  Copyright (c) 2002 RSA Security Inc. All rights reserved.
  Copyright (c) 1997-2010 University of Cambridge. All rights reserved.
  Copyright (C) 1997 - 2002, Makoto Matsumoto and Takuji Nishimura, All rights reserved.
  Copyright (c) 1995 Tatu Ylonen , Espoo, Finland All rights reserved.
  Copyright (c) 1998-2004 The OpenSSL Project.  All rights reserved.
  Copyright (C) 1995-1998 Eric Young (eay@cryptsoft.com) All rights reserved.
  Copyright (c) 2006 Digital Arts Inc. All Rights Reserved.
  Copyright (C) 1994-2012 Lua.org, PUC-Rio.
  Copyright (c) 1988-1992 Carnegie Mellon University All Rights Reserved.
  Copyright (C) 2004-2007 Diego Nehab. All rights reserved.
  Copyright (c) 2005 JSON.org
00:a0:de:6b:74:13, 00:a0:de:6b:74:14, 00:a0:de:6b:74:15
Memory 128Mbytes, 3LAN, 1BRI
> administrator 
Password: 
# 
```

SSHが使用したいところだが、もう少し我慢。

DHCPサーバーを有効化する
------------------------

```
dhcp service server 
dhcp server rfc2131 compliant except remain-silent 
dhcp scope 1 192.168.0.2-192.168.0.199/24 
```

DNSリレーの設定
----------------

### 個別に指定するとき

```
dns server 8.8.8.8 8.8.4.4 
dns private address spoof on
```

### ISPから自動取得する

インターリンクは自動取得が推奨されている。

```
# PPPoE接続のpp1インタフェースの情報を使用する場合
dns server pp 1
# lan2インタフェースの情報を使用する場合
dns server dhcp lan2
```
