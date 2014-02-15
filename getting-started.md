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