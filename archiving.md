# アーカイヴ

## zip

※非POSIX

```sh
zip [options] [-e [-P passwd]] archive path ... [-i path ...] [-x path ...]
```

|オプション|説明|
|-|-|
|-r|ディレクトリ構造を保ったままエントリをアーカイヴに追加する|
|-e|暗号化する|
|-P <i>passwd</i>|パスワードを指定する|
|-i <i>path ...</i>|処理対象のパターンを指定する|
|-x <i>path ...</i>|処理対象外のパターンを指定する|

アーカイヴが既にある場合は追加・上書きとなる。

```sh
unzip [-P passwd] archive [path ...] [-x path ...] [-d outdir]
```

|オプション|説明|
|-|-|
|-d <i>outdir</i>|展開先を指定する|

拡張子 `.zip` は省略可能。

例: カレント・ディレクトリを起点に `*.md` ファイルのみをディレクトリ構造を保ったままアーカイヴする。

```sh
zip -r hoge . -i "*.md"
```

例: アーカイヴをカレント・ディレクトリに展開する。

```sh
unzip hoge.zip
```

例: 特定のファイルのみ取り出す。

```sh
unzip hoge.zip foo/bar
```

## gzip

※非POSIX

```sh
gzip [-ckr] path ...
gunzip [-kr] path ...
```

|オプション|説明|
|-|-|
|-c|出力を標準出力にする|
|-k|元ファイルを残す|
|-r|ディレクトリ配下のファイルそれぞれを処理対象とする|

拡張子 `.gz` は省略可能。

## bzip2

※非POSIX

```sh
bzip2 [-ck] path ...
bunzip2 [-k] path ...
```

|オプション|説明|
|-|-|
|-c|出力を標準出力にする|
|-k|元ファイルを残す|

## xz

※非POSIX

```sh
xz [-ck] path ...
unxz [-k] file ...
```

|オプション|説明|
|-|-|
|-c|出力を標準出力にする|
|-k|元ファイルを残す|

## tar

※非POSIX

```sh
tar [options] [-f archive] [path path ...]
```

|オプション|説明|
|-|-|
|-c|アーカイヴを作成する|
|-r|エントリを既存アーカイヴに追加する（圧縮アーカイヴでは利用不可）|
|-u|更新日時が新しい場合のみエントリを既存アーカイヴに追加する（圧縮アーカイヴでは利用不可）|
|-t|アーカイヴの内容を一覧表示する|
|-x|アーカイヴを展開する|
|-z|gzip圧縮／展開|
|-j|bzip2圧縮／展開|
|-J|xz圧縮／展開|
|-v|verbose|
|-f <i>archive</i>|アーカイヴ名を指定する|

オプションの `-` は省略することが多い。

例: アーカイヴを作る。アーカイヴ内には `foo/bar` ディレクトリが出来る。

```sh
tar cvzf hoge.tar.gz /foo/bar
```

例: カレント・ディレクトリに展開する。

```sh
tar xvzf hoge.tar.gz
```

例: 特定のファイルのみ取り出す。

```sh
tar xvzf hoge.tar.gz foo/bar/baz
```

## 7z

※非POSIX

```sh
7z a [-ppasswd] archive path ...
7z x [-ppasswd] [-ooutdir] archive
7z l archive
```

|オプション|説明|
|-|-|
|a|アーカイヴに追加する|
|x|アーカイヴを展開する|
|l|アーカイヴの内容を一覧表示する|
|-p<i>passwd</i>|パスワードを指定する|
|-o<i>outdir</i>|展開先を指定する|
