# Dockerfile 置き場

内容と管理ポリシー

- `erlang/` 以下
  - Erlang/OTP 入りイメージ
  - CentOS, RHEL, Ubuntu の幾つかのバージョン向け
  - Erlang/OTP のリリースに追従していく

## Erlang/OTP JIT

- CentOS / RHEL は OTP 24 JIT には非対応
    - GCC が古すぎる
- Ubuntu arm 版は OTP 24 JIT には非対応
    - AsmJit が arm 非対応
