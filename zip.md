# zip

## ターミナルから操作する

### 内容物を列挙する

```sh
unzip -l ZIPFILE
```

```sh
7zz l ZIPFILE
```

### 圧縮する

```sh
zip -r [-e -P PASSWORD] ZIPFILE FILES...
```

```sh
7zz a [-pPASSWORD] ZIPFILE FILES...
```

### 伸長する

```sh
unzip [-P PASSWORD] ZIPFILE [-d OUTDIR] [FILES...]
```

```sh
7zz x [-oOUTDIR] -pPASSWORD ZIPFILE
```
