# シェル

## キー操作（bash emacsモード）

### カーソル移動

|キー|説明|
|-|-|
|Ctrl B|1文字前へ移動|
|Ctrl F|1文字後へ移動|
|Esc B|1単語前へ移動|
|Esc F|1単語後へ移動|
|Ctrl A|先頭へ移動|
|Ctrl E|末尾へ移動|

### 編集

|キー|説明|
|-|-|
|Del|前の1文字を削除|
|Ctrl D|後の1文字を削除|
|Esc Del|前の1単語を削除|
|Esc D|後の1単語を削除|
|Ctrl U|先頭までを削除|
|Ctrl K|末尾までを削除|
|Esc U|後の1単語を大文字にする|
|Esc L|後の1単語を小文字にする|
|Esc T|2単語を交換|
|Ctrl Y|最近削除した語句を貼り付け|
|Esc .|前回のコマンドの末尾の単語を貼り付け|
|Esc R|加えられた編集をすべて戻す|

### 履歴

|キー|説明|
|-|-|
|Ctrl R|履歴検索|
|Ctrl R R|前回の入力を選択|
|Ctrl P|履歴を前へ移動|
|Ctrl N|履歴を次へ移動|

## スクリプト

### パラメータ展開

|式|説明|拡張|
|-|-|-|
|`${parameter:-word}`|`parameter` がnullなら `word` を返す||
|`${parameter:=word}`|`parameter` がnullなら `word` を返し `parameter` に代入する||
|`${parameter:?word}`|`parameter` がnullなら `word` をstderrに出力してシェルを終了する||
|`${parameter:+word}`|`parameter` がnullでなければ `word` を返す||
|`${parameter:offset:length}`|部分文字列を返す。 `offset` は0始まり。末尾までを取得する場合 `:length` は省略可|bash|
|`${#parameter}`|長さを返す||
|`${parameter#pattern}`|`pattern` と前方最短一致した部分を除去して返す||
|`${parameter##pattern}`|`pattern` と前方最長一致した部分を除去して返す||
|`${parameter%pattern}`|`pattern` と後方最短一致した部分を除去して返す||
|`${parameter%%pattern}`|`pattern` と後方最長一致した部分を除去して返す||
|`${parameter/pattern/replacement}`|最初に一致した箇所を置換|bash|
|`${parameter//pattern/replacement}`|一致した箇所すべてを置換|bash|

### 評価演算子

|式|説明|拡張|
|-|-|-|
|<i>a</i> = <i>b</i>|||
|<i>a</i> != <i>b</i>|||
|<i>a</i> =~ <i>regex</i>|`[[ ]]` の中で利用可|bash|
|<i>a</i> < <i>b</i>||bash|
|<i>a</i> > <i>b</i>||bash|
|<i>a</i> -eq <i>b</i>|整数として評価||
|<i>a</i> -ne <i>b</i>|整数として評価||
|<i>a</i> -gt <i>b</i>|整数として評価||
|<i>a</i> -ge <i>b</i>|整数として評価||
|<i>a</i> -lt <i>b</i>|整数として評価||
|<i>a</i> -le <i>b</i>|整数として評価||
|-z <i>string</i>|<i>string</i>がnull||
|-n <i>string</i>|<i>string</i>がnullでない||
|-e <i>path</i>|<i>path</i>が存在する||
|-f <i>path</i>|<i>path</i>が存在しファイルである||
|-s <i>path</i>|<i>path</i>が存在し空でないファイルである||
|-d <i>path</i>|<i>path</i>が存在しディレクトリである||
|-h <i>path</i>|<i>path</i>が存在しシンボリック・リンクである||
|-r <i>path</i>|<i>path</i>が存在しパーミッション `r` が付いている||
|-w <i>path</i>|<i>path</i>が存在しパーミッション `w` が付いている||
|-x <i>path</i>|<i>path</i>が存在しパーミッション `x` が付いている||
|<i>path1</i> -nt <i>path2</i>|<i>path1</i>が<i>path2</i>より新しい|bash|
|<i>path1</i> -ot <i>path2</i>|<i>path1</i>が<i>path2</i>より古い|bash|
