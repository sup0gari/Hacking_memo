# GoBusterとは
Webサーバー上の隠されたディレクトリやファイル**、またはサブドメインを、ワードリストを使って高速に総当たり（ブルートフォース）検索し、攻撃対象領域を調査するためのツール。

## コマンド
```bash
gobuster dir -u <ターゲット> -w <使用するワードリストのパス> # ワードリストに該当するURLを検索
gobuster vhost -u <ターゲット> -w <使用するワードリストのパス> --append-domain # サブドメインを検索
-k # 証明書チェックをスキップ
-t <スレッド数> # スレッド数を指定
-b <ステータスコード> # 指定したステータスコードを除外
-s <ステータスコード> # 指定したステータスコードのみを表示
--exclude-length <レスポンスの長さ> # 指定したレスポンスの長さを除外
-x <拡張子> # 指定した拡張子を検索
```

## ワードリスト(kali linux)
ディレクトリ検索
`/usr/share/wordlists/dirb/common.txt`
`/usr/share/wordlists/dirbuster/directory-list-lowercase-2.3-medium.txt`
サブドメイン検索
`/usr/share/seclists/Discovery/DNS/subdomains-<ワード数>.txt`
