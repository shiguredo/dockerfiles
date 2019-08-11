Dockerfile 置き場
=================

内容と管理ポリシー

- `erlang/` 以下

  - Erlang/OTP 入りイメージ
  - CentOS, Ubuntu の幾つかのバージョン向け
  - Erlang/OTP のリリースに追従していく

- `erlang-one-shot/` 以下

  - Erlang/OTP 入りイメージ
  - 特にディストリビューションに縛りをつけない
  - Erlang/OTP のリリースには追従しない

- `circleci`

  - CircleCI 2.0 用イメージ
  - デプロイ、テストなど用途に応じて追加する
