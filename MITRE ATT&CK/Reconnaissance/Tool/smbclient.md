# smbclientとは
LinuxからSMB共有にアクセスするためのコマンドラインツール

## ダウンロード方法
```bash
# Debian/Ubuntu系
sudo apt update
sudo apt install smbclient

# RHEL/CentOS系
sudo yum install samba-client
```

## 接続方法
```bash
smbclient //<ターゲット>/<共有フォルダ> -N # 匿名接続
smbclient -L //<ターゲット> -N # 匿名接続で共有フォルダを表示
smbclient //<ターゲット>/<共有フォルダ -c <コマンド> # 匿名接続と同時にコマンドを実行
smbclient //<ターゲット>/<共有フォルダ> -U <ユーザー名> # ユーザーを指定して接続
smbclient -k //<ターゲット>/<共有フォルダ> # Kerberos認証を使用して接続
```

## コマンド
```bash
get <ファイル名> # ファイルをダウンロード
prompt OFF # 警告などの確認メッセージをオフにする
recurse ON # ダウンロードする時などで再帰をオンにする
mget * # すべてのファイルをダウンロード
```
