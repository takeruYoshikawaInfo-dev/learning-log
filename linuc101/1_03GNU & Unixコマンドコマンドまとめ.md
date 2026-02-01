# LinuC 101 1.03：GNU & Unixコマンド

■1. ファイル・ディレクトリ操作（基本）

### mkdir
```bash
# ディレクトリを作成する
# mkdir [オプション] {ディレクトリ名}
mkdir -p project/docs
# (備考) -p は親ディレクトリも含めて作成する
```

### rm
```bash
# ファイルやディレクトリを削除する
# rm [オプション] {対象}
rm -rf /tmp/old_data
# (備考) -r は再帰的削除、-f は確認なし強制削除（注意！）
```

### touch
```bash
# 空ファイルの作成、またはタイムスタンプの更新
# touch {ファイル名}
touch original.txt
```


■2. テキスト処理（フィルタ・検索）

### cat
```bash
# ファイル内容を連結して表示する
# cat [オプション] {ファイル名}
cat -n /etc/hosts
# (備考) -n は行番号を付与して表示
```

### grep
```bash
# テキスト内から文字列パターンを検索する
# grep [オプション] {検索文字列} {ファイル名}
grep -i "error" /var/log/syslog
# (備考) -i は大文字小文字を区別しない、-v は不一致行を表示
```

### sed
```bash
# 文字列の置換や抽出を行う（ストリームエディタ）
# sed 's/{置換前}/{置換後}/g' {ファイル名}
sed 's/apple/orange/g' list.txt
# (備考) 試験では 's' (置換) や 'd' (削除) の使い方が頻出
```

### awk
```bash
# テキストのパターン処理と抽出を行う
# awk '{print ${列番号}}' {ファイル名}
awk -F: '{print $1}' /etc/passwd
# (備考) -F は区切り文字の指定。例はユーザー名の一覧表示
```


■3. ファイル比較・並び替え

### sort
```bash
# 行単位で並び替える
# sort [オプション] {ファイル名}
sort -r data.txt
# (備考) -r は降順、-n は数値として並び替え
```

### uniq
```bash
# 重複した行を1行にまとめる
# uniq [オプション] {ファイル名}
uniq -c log.txt
# (備考) 事前に sort しておく必要がある。-c は出現回数を表示
```


■4. 検索とアーカイブ

### find
```bash
# ファイルを条件検索する
# find {検索パス} -name "{条件}"
find /home/user -name "*.log" -mtime -7
# (備考) -mtime は更新日、-size はファイルサイズで検索
```

### tar
```bash
# ファイルをアーカイブ化（＋圧縮）する
# tar [オプション] {作成ファイル名} {対象}
tar -cvzf backup.tar.gz /etc/
# (備考) -c:作成, -x:展開, -v:詳細, -z:gzip, -j:bzip2
```
