# テキスト操作

## 転置

### 改行区切り↔カンマ区切り

```sh
# 縦 to 横
rs -T -C, <FILE

# 横 to 縦
rs -T -c, <FILE
```

## 改行コード

### 確認

```sh
nkf --guess FILE
```

### 変換

```sh
# LF to CRLF
nkf --overwrite -Lw FILE

# CRLF to LF
nkf --overwrite -Lu FILE
```

## 文字エンコーディング

### 確認

```sh
nkf --guess FILE
```

### 変換

```sh
iconv -f CP932 -t UTF-8 FILE
```

指定できるエンコーディング名称は `iconv -l` で確認できる。

## BOM

### 確認

UTF-8文書の先頭3 Byteが `0xEF 0xBB 0xBF` の場合、その文書はBOM付き。

```sh
$ od -t x1 -N 3 FILE
```

### 変換

```sh
# 追加
nkf --overwrite --ic=UTF-8 --oc=UTF-8-BOM FILE

# 除去
nkf --overwrite --ic=UTF-8-BOM --oc=UTF-8 FILE
```
