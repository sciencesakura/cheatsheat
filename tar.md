# tar

サポートする主な圧縮方式:

| 圧縮方式 | オプション | 主な拡張子 |
|---|---|---|
| [gzip](./gzip.md) | `z` | `.tar.gz` |
| bzip2 | `j` | `.tar.bz2` |
| xz | `J` | `.tar.xz` |

以降は特記なければgzipでの例となる。

## ターミナルから操作する

### 内容物を列挙する

```sh
tar lzf TARFILE
```

### 圧縮する

```sh
tar cvzf TARFILE FILES...
```

### 伸長する

```sh
tar xvzf TARFILE [FILES...]
```
