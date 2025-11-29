# Nmapとは
Nmap（Network Mapper）は、ターゲット端末上で実行されているソフトウェアの名称、バージョン、使用しているポートなどを特定することができるオープンソースのコマンドラインツールです。

## コマンド
```bash
nmap <オプション> <ターゲット>
```

## よく使うオプション
```bash
-p 80 # 80番ポートのスキャン
-p- # すべてのポートのスキャン
-v # スキャン中に詳細な情報を表示
-sS # 完全な接続を確立しないSYNスキャン
-sU # UDPポートのスキャン
-Pn # pingを行わないスキャン
--min-rate=5000 # 1秒間に最低5,000パケットを送信するスキャン
-T4 高速スキャン
```

## 例
```bash
nmap -p- -v -Pn -T4 10.10.10.1

# 下記出力例
Not shown: 65534 closed tcp ports (reset)
PORT   STATE SERVICE
23/tcp open  telnet
```
