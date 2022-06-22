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

## BOM（UTF-8）

UTF-8文書の先頭3byteが `0xEF 0xBB 0xBF` の場合、その文書のエンコーディングはBOM付きUTF-8。

### BOMの有無を確認する

```sh
file FILE

od -t x1 -N 3 FILE
```

### BOMを追加する

```sh
nkf --ic=UTF-8 --oc=UTF-8-BOM FILE

nkf --overwrite --ic=UTF-8 --oc=UTF-8-BOM FILE
```

### BOMを削除する

```sh
nkf --ic=UTF-8-BOM --oc=UTF-8 FILE

nkf --overwrite --ic=UTF-8-BOM --oc=UTF-8 FILE
```
