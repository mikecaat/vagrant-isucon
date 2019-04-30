# vagrant-isucon/isucon8-qualifier

## Overview

isucon8予選とほぼ同じ環境を構築するためのVagrantfileです。

- CPU 2コア、メモリ1GBの4台構成(VirtualBoxを想定)
  - bench: ベンチマーク用サーバ
  - webapp1: 参加者用サーバ(web, ap, dbの自動起動設定済)
  - webapp2: 参加者用サーバ(web, ap, dbの自動起動設定済)
  - webapp3: 参加者用サーバ(web, ap, dbの自動起動設定済)

## Usage

- vagrant実行環境を用意する
- このリポジトリ内のVagrantfileを手元に用意する
  - 必要に応じてVagrantfileを編集する
- Vagrantfileがあるディレクトリで`vagrant up`を実行する
  - ベンチマーク用サーバ(bench)と参加者用サーバ(webapp1, webapp2, webapp3)が起動
- Ansibleによるプロビジョニングが完了したら`vagrant ssh`を実行する
  - vagrant ssh bench
  - vagrant ssh webapp
- ベンチマークを実行する
  - sudo -i -u isucon
  - cd torb/bench
  - bin/bench -remotes=(webapp1サーバのIPアドレス) -output result.json
