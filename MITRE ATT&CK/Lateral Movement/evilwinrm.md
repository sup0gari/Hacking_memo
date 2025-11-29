# Evil-WinRMとは
リモートのWindowsマシンに対しWindows Remote Managementプロトコル経由でアクセスし、対話的なシェルセッションを確立するために設計されたオープンソースのツール。

## 接続方法
```bash
evil-winrm -i <ターゲット> -u <ユーザー名> -p '<パスワード>' # パスワードで接続
evil-winrm -i <ターゲット> -u <ユーザー名> -H '<NTハッシュ>' # NTハッシュで接続
```
