# Shell

## リファレンス

### パラメータ展開

|式|説明|Bash拡張|
|---|---|:---:|
|`${parameter:-word}`|nullなら `word` を返す||
|`${parameter:=word}`|nullなら `word` を `parameter` に代入して返す||
|`${parameter:?word}`|nullなら `word` をstderrに出力して終了する||
|`${parameter:+word}`|nullでなければ `word` を返す||
|`${parameter:offset:length}`|部分文字列を返す（ `:length` 省略可）|✔|
|`${#parameter}`|文字列の長さを返す||
|`${parameter#pattern}`|前方最短一致した部分を除去して返す||
|`${parameter##pattern}`|前方最長一致した部分を除去して返す||
|`${parameter%pattern}`|後方最短一致した部分を除去して返す||
|`${parameter%%pattern}`|後方最長一致した部分を除去して返す||
|`${parameter/pattern/replacement}`|最初に一致した部分を置換して返す|✔|
|`${parameter//pattern/replacement}`|一致した部分すべてを置換して返す|✔|
|`${parameter/#pattern/replacement}`|先頭で一致した部分を置換して返す|✔|
|`${parameter/%pattern/replacement}`|末尾で一致した部分を置換して返す|✔|
|`${parameter^pattern}`|一致した先頭一文字を大文字にして返す|✔|
|`${parameter^^pattern}`|一致した部分を大文字にして返す|✔|
|`${parameter,pattern}`|一致した先頭一文字を子文字にして返す|✔|
|`${parameter,,pattern}`|一致した部分を子文字にして返す|✔|
|`${parameter[*]}`|（配列・連想配列）全要素をIFSの先頭一文字で結合して返す|✔|
|`${parameter[@]}`|（配列・連想配列）全要素を返す|✔|
|`${!parameter[*]}`|（配列・連想配列）全添字をIFSの先頭一文字で結合して返す|✔|
|`${!parameter[@]}`|（配列・連想配列）全添字を返す|✔|
|`${#parameter[*]}`|（配列・連想配列）要素数を返す|✔|

### 評価演算子

|式|説明|Bash拡張|
|---|---|:---:|
|`-d file`|ファイルが存在しディレクトリである||
|`-e file`|ファイルが存在する||
|`-f file`|ファイルが存在しレギュラーファイルである||
|`-r file`|ファイルが存在し読取可能である||
|`-s file`|ファイルが存在し空でない||
|`-w file`|ファイルが存在し書込可能である||
|`-x file`|ファイルが存在し実行可能である||
|`file1 -nt file2`|`file1` が `file2` より新しい|✔|
|`file1 -ot file2`|`file1` が `file2` より古い|✔|
|`-z string`|文字列が空||
|`-n string`|文字列が空でない||
|`string1 = string2`|||
|`string1 != string2`|||
|`string1 < string2`||✔|
|`string1 > string2`||✔|
|`int1 -eq int2`|||
|`int1 -ne int2`|||
|`int1 -lt int2`|||
|`int1 -le int2`|||
|`int1 -gt int2`|||
|`int1 -ge int2`|||

`[[` でのみ使えるもの:

|式|説明|Bash拡張|
|---|---|:---:|
|`string =~ regex`|正規表現にマッチする|✔|

## イディオム

### 条件判定

```sh
# NOT
[ ! EXPR ]

# AND
[ EXPR1 ] && [ EXPR2 ]

# AND（古）
[ EXPR1 -a EXPR2 ]

# OR
[ EXPR1 ] || [ EXPR2 ]

# OR（古）
[ EXPR1 -o EXPR2 ]
```

### 配列［Bash拡張］

```sh
declare -a names

names=(Alice Bob Carol)
names[3]=Dave

for nm in "${names[@]}"; do
  echo "$nm"
done
```

### 連想配列［Bash拡張］

```sh
declare -A score

score=([Alice]=100 [Bob]=80 [Carol]=60)
score[Dave]=90

for sc in "${!score[@]}"; do
  echo "$sc=${score[$sc]}"
done
```

### 各ファイルに対してなにかする

```sh
# ファイル1つずつにコマンド実行
find . -type f -exec CMD {} \;

# ファイルを複数まとめてコマンド実行
find . -type f -exec CMD {} +

# 一コマンドで済まない場合はfor文で
for i in $(find . -type f); do
  ...
done
```

### テキストファイルの各行に対してなにかする

```sh
while IFS= read -r line; do
  ...
done < FILE
```
