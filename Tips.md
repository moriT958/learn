# 覚えとくと便利なTips的なこと

## Mac(unix)

- `uuidgen`: UUIDを生成できる
- `pbcopy/pbpaste`: クリップボードに保存・貼り付けができる。`echo "Hello,World." | pbcopy`

- `/`はルートディレクトリの事で、システムの最上位のディレクトリ。
- `~`はホームディレクトリのことで、ログインしたユーザのトップディレクトリ。

## Golang

- 書式指定子:
- `%q`を使うと`%s`では表示されない空白やエスケープも詳しく表示できる。
- `%v`: 指定した型のでフォルの表示で出力する。

- `http.NewRequest`では、パス値は`SetPathValue`で明示的にセットしないといけない。

- `[]byte`型と`string`型は相互互換できる。

- 型アサーションについて
  - any、interface{}型のような抽象型を、具体型に変換すること。
  - `v, ok := (interface).(type)`: vは型のゼロ値。okは成功したかどうかのbool。okは無視可能。
  - 型変換との違い：型変換は型そのものを明示的に変するもの。

## Git

- pullし忘れてpushしてしまった時
  - `git pull origin main --rebase`
  - `git rebase --continue`
  - `git push origin main`
