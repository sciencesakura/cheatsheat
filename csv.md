# CSV操作

- [csvkit](https://csvkit.readthedocs.io/en/latest/index.html)
- [csvtool](https://colin.maudry.com/csvtool-manual-page/)

## 確認

```sh
# カラム一覧
csvstat -n FILE

# カラム数表示
csvtool width FILE

# レコード数表示
csvtool height FILE
```

## 検索

```sh
# STRINGを含む
csvgrep -c COLUMNS -m STRING FILE

# STRINGを含まない
csvgrep -c COLUMNS -i -m STRING FILE

# REGEXに合致する
csvgrep -c COLUMNS -r REGEX FILE

# REGEXに合致しない
csvgrep -c COLUMNS -i -r REGEX FILE

# SQL
csvsql -I --query QUERY FILE
```

## ソート

```sh
# 昇順
csvsort -I -c COLUMNS FILE

# 降順
csvsort -I -c COLUMNS -r FILE
```

## 転置

```sh
csvtool transpose FILE
```

## 変換

```sh
# to JSON
csvjson FILE

# to JSONL
csvjson --stream FILE
```
