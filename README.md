# あにめインフォ

[うずらインフォ](https://uzurainfo.han-be.com/) が終了するようなので、過去のアニメ情報をまとめなおしました。

## ローカル環境

index.html をダブルクリックしてブラウザで開くと Fetch API が URL scheme `file` に対応していないため下記のエラーが出ます。

```
Fetch API cannot load file:///C:/path/to/anime-info/docs/data/2020-Q3.json. URL scheme "file" is not supported.
```

何らかのサーバーを立ち上げてください。

```powershell
cd docs
php -S localhost:8000
```

http://localhost:8000/
