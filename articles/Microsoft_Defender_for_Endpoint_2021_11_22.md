---
title: Red Hat Enterprise Linux へ Microsoft Defender for Endpoint をインストールする際の依存関係について
date: 2021-11-22 17:30:00
tags:
- Microsoft Defender for Endpoint
---
いつも弊社製品をご利用いただきまして誠にありがとうございます。
日本マイクロソフト Azure Security サポートチームです。
本記事では、Red Hat Enterprise Linux へ Microsoft Defender for Endpoint(以降 MDE) をインストール、及びアップデートいただく際の依存関係について紹介します。

[発生する事象]
MDE のインストール、及びアップデートでは、yum コマンドによる依存関係の確認や解決が行われます。
依存関係が自動解決されない場合、インストールやアップデートに失敗します。

[発生する事象例]
MDE のコンポーネントである mdatp モジュールのバージョン 101.45.13 以降では、mde-netfilter モジュールが依存関係モジュールとして追加されています。
※ mde-netfilterモジュールを依存関係とするmdatpモジュールのバージョン 101.45.13は、2021/10/15時点で prod チャネルから配信しています
mde-netfilter モジュールは、libnetfilter_queue と依存関係があります。
libnetfilter_queue が未インストールの場合、自動解決が試行されます。
自動解決によるインストールに失敗した場合、mde-netfilter モジュール、及び mdatp モジュールのインストールに失敗します。

エラーの例:
問題: package mdatp-101.45.13-1.x86_64 requires mde-netfilter, but none of the providers can be installed
- cannot install the best candidate for the job
- nothing provides libnetfilter_queue needed by mde-netfilter-100.69.32-1.x86_64

[発生する事象例の想定原因]
デフォルトでは、libnetfilter_queueはrhui-rhel-8-for-x86_64-baseos-rhui-rpms リポジトリから libnetfilter_queue のダウンロードを試行します。
libnetfilter_queueはrhui-rhel-8-for-x86_64-baseos-rhui-rpms リポジトリへのアクセス制限やリポジトリの未構成、モジュールのインストール制限が行われている可能性があります。

[発生する事象例の対処策]
rhui-rhel-8-for-x86_64-baseos-rhui-rpms リポジトリへのアクセスやリポジトリの構成、及びモジュールのインストール許可を Red Hat Enterprise Linux やネットワーク観点でご確認ください。

この情報は2021/11/22 時点のものとなります。
今後予期せず変更される可能性がございますので、ご留意くださいますようお願い申し上げます。
