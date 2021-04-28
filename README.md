# Dockerfile 置き場

内容と管理ポリシー

- `erlang/` 以下
  - Erlang/OTP 入りイメージ
  - CentOS 7.9 / 8.3
  - RHEL 7.9 / 8.3
  - Ubuntu 18.04 / 20.04
  - Ubuntu 20.04 のみ arm64v8 版あり
  - Erlang/OTP のリリースに追従していく

## Erlang/OTP JIT

- CentOS / RHEL は OTP 24 JIT には非対応
    - GCC が古すぎる
- Ubuntu arm 版は OTP 24 JIT には非対応
