# さくらVPS メモ

さくらVPSのセットアップ時のメモ

## パッケージマネージャのアップデート

OS: ubuntu24.04

- `sudo apt update`
- `sudo apt upgrade`

## SSHサーバのセットアップ

- 公開鍵の設定

  - ローカルでキーペアを作成: `ssh-keygen -t [alg] -N [keyname]`
  - 公開鍵をホストへコピー: `scp ~/.ssh/id_rsa.pub [username]@[hostname]:~/.ssh/authorized_keys`
  - 接続確認: `ssh -l username hostname(ip)`

  - SSHサーバ(ssh.service)の起動確認

    - `sudo systemctl status ssh`: sshサーバが起動しているか確認
    - 起動していない場合
      - `sudo systemctl enable ssh`
      - `sudo systemctl start ssh`

  - SSHソケット(ssh.socket)の起動確認
    - `sudo systemctl status ssh.socket`

- ホスト: `/etc/ssh/sshd_config`を編集

  - ポートの変更: `Port 22`
  - ルート権限でのログインを禁止: `PermitRootLogin no`
  - パスワードでログインを禁止: `PasswordAuthentication no`
  - `sudo systemctl restart ssh`
  - `sudo systemctl reload ssh`
  - `sudo systemctl enable ssh`

- ホスト: `/lib/systemd/system/ssh.socket`を編集

  - `ListenStream=[Port]`を変更
  - `systemctl daemon-reload`
  - `systemctl restart ssh`

- sshクライアントの設定
  - ローカル: `~/.ssh/config`を編集
  - 以下のようにすると、`ssh sakura`のみでログインできるので便利

```: config
  Host sakura
    HostName (hostname)
    IdentityFile ~/.ssh/(keyname)
    User (username)
    Port (port)
```

## ファイヤーウォール(ufw)の設定

- 全ポートでの接続拒否: `sudo ufw default deny`
- `sudo ufw allow [Port]`
- `sudo ufw enable`
