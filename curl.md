# curl

※非POSIX

## Cookie

### レスポンスのSet-Cookieヘッダを取り出す

```sh
curl -c <file> [<options>] <url>
```

下記フィールドをタブ区切りしたフォーマット（Netscape/Mozilla cookie file format）で書き出す。1つの `Set-Cookie` が1つの行に対応する。

|フィールド|型|説明|
|-|-|-|
|1|string|`Domain` に相当|
|2|boolean|サブドメインがcookieを受信するのを許容するか|
|3|string|`Path` に相当|
|4|boolean|`Secure` に相当|
|5|number|`Expires` に相当（UNIX時間で指定）|
|6|string|名前|
|7|string|値|

例:

```
www.example.com	TRUE	/hoge	TRUE	0	foo	bar
```

### リクエストのCookieヘッダに値を設定する

```sh
curl -b "<name>=<value>; ..." [<options>] <url>
curl -b <file> [<options>] <url>
```
