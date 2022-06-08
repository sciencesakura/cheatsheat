# テキスト操作

## 改行コードの変換

### LF to CRLF

```sh
nkf -Lw FILE

nkf --overwrite -Lw FILE
```

`nkf` がない場合:

```sh
sed 's/$/\r/' FILE
```

### CRLF to LF

```sh
nkf -Lu FILE

nkf --overwrite -Lu FILE
```

`nkf` がない場合:

```sh
tr -d \\r <FILE
```

## 文字エンコーディングの変換

```sh
iconv -f CP932 -t UTF-8 FILE  # CP932 to UTF-8
```

指定できるエンコーディングは `iconv -l` で確認できる。

## BOMの付け外し（UTF-8）

BOM: `EF BB BF`

### BOMを付ける

```sh
nkf --oc=UTF-8-BOM FILE

nkf --overwrite --oc=UTF-8-BOM FILE
```

### BOMを外す

```sh
nkf --oc=UTF-8 FILE

nkf --overwrite --oc=UTF-8 FILE
```
