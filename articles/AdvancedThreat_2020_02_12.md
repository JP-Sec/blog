---
title: FAQ Microsoft Advanced Threat Analytics(ATA)/ AzureAdvanced Threat Protection(AATP)
date: 2020-2-12 11:56:00
tags:
- Azure AdvancedThreat Protection
- Microsoft AdvancedThreat Analytics(ATA)
---

マイクロソフトサポート部門より Microsoft Advanced Threat Analytics(ATA)/ AzureAdvanced Threat Protection(AATP)について良くあるお問い合わせをまとめております。

以下のとおり製品毎の公開情報もございますが、サポートへのお問い合わせ数が多い項目についてまとめておりますので、是非併せてご参照くださいますと幸いです。

『ATAに関してよく寄せられる質問』
https://docs.microsoft.com/ja-jp/advanced-threat-analytics/ata-technical-faq

『AzureATPに関してよく寄せられる質問』
https://docs.microsoft.com/ja-jp/azure-advanced-threat-protection/atp-technical-faq

Q1どんな製品か
ActiveDirectoryの通信を監視し、不正な認証が行われていないか認証観点でアラートを通知します。
攻撃のための認証情報の搾取などの兆候を捉える製品となります。
他製品との連携で可能となる場合もございますが、動作制御、及び、マルウェア検出などは対象外となりますので予めご留意ください。

[ATA]
専用のツールで各ADの通信を監視し、オンプレミスに監視サーバーを構築して認証アラートを監視します。

[AATP]
専用のツールで各ADの通信を監視し、AzureATPに通信を送ることでAzureATP上で認証アラートを監視します。

Q2ライセンスについて

[ATA]
サーバーのアクティブ化のためのライセンス、及び、EMSE3などのクライアント用のライセンスが必要となります。

[AATP]
こちらはEMSE5などのクライアント用のライセンスのみが必要となります。
ATACenterサーバーのアクティブ化のライセンスについては以下をご参照ください。

『AdvancedThreatAnalytics(ATA)のライセンスはどこで取得できますか。』
https://docs.microsoft.com/ja-jp/advanced-threat-analytics/ata-technical-faq#where-can-i-get-a-license-for-advanced-threat-analytics-ata

Q3お問合せ方法について

[ATA]
オンプレミスで完結する製品となりますので、オンプレミスの契約での問合せが必要となります。

[AATP]
Azureのご契約でお問い合わせいただけます。

Q4モジュールのインストールができない/サービスが起動しない
通信を監視するため、モジュールをインストールする必要がございます。
このモジュールはATACenterサーバー、または、AzureATPと接続ができる必要があり、この接続ができない場合にはモジュールのインストールに失敗します。

このような場合には以下の前提条件をご確認ください。

『ATAの前提条件』
https://docs.microsoft.com/ja-jp/advanced-threat-analytics/ata-prerequisites

『AzureATPの前提条件』
https://docs.microsoft.com/ja-jp/azure-advanced-threat-protection/atp-prerequisites

Q5サービスが頻繁に再起動する/リソース不足が発生する
これらの製品は通信を全て監視するため、CPU,メモリリソースを消費します。
また、メモリの使用量、CPUの使用率が高くなりますと自動的にサービスを再起動し、リソースを開放する処理が行われます。
その為、事前のサイジングを実施いただくことを推奨いたします。

『ATA容量計画』
https://docs.microsoft.com/ja-jp/advanced-threat-analytics/ata-capacity-planning

『クイックスタート:AzureATP用の容量を計画する』
https://docs.microsoft.com/ja-jp/azure-advanced-threat-protection/atp-capacity-planning

また、アンチマルウェアソフトやネットワークアナライザーのようなツールが干渉し、環境によっては正常に動作がしない可能性がございます。
上記の影響が懸念される場合、対象のアプリケーションを停止して事象が改善するか、また、マルウェア対策ソフトの除外設定を推奨いたします。

ATACenterサーバーについては以下に記載がございます。

『ウイルス対策の除外リストの設定』
https://docs.microsoft.com/ja-jp/advanced-threat-analytics/install-ata-step1#set-anti-virus-exclusions

------------------------------------------------
フォルダー
C:\ProgramFiles\MicrosoftAdvancedThreatAnalytics\Center\MongoDB\bin\data
C:\ProgramFiles\MicrosoftAdvancedThreatAnalytics\Center\ParentKerberosAsBloomFilters
C:\ProgramFiles\MicrosoftAdvancedThreatAnalytics\Center\ParentKerberosTgsBloomFilters
C:\ProgramFiles\MicrosoftAdvancedThreatAnalytics\Center\Backup
C:\ProgramFiles\MicrosoftAdvancedThreatAnalytics\Center\Logs

プロセス
mongod.exe
Microsoft.Tri.Center.exe
------------------------------------------------

ATAGatewayの対象フォルダ、及び、プロセスは以下になります。
------------------------------------------------
フォルダー
C:\ProgramFiles\MicrosoftAdvancedThreatAnalytics\

プロセス
Microsoft.Tri.Gateway.exe
Microsoft.Tri.Gateway.updater.exe
------------------------------------------------

AzureATPの対象フォルダ、及び、プロセスは以下になります。
------------------------------------------------
フォルダー
C:\ProgramFiles\AzureAdvancedThreatProtectionSensor\

プロセス
Microsoft.Tri.Sensor.exe
Microsoft.Tri.Sensor.updater.exe
------------------------------------------------

Q6.AzureATP構築時に一度MicrosoftCloudAppSecurity(MCAS)のページに遷移する
こちらは仕様となります。
現在AzureATPはMCASと連携ができるようになっており、MCASポータルからもアラートが確認できるようになっております。
今後、ポータルを統合する計画もあり、このような動作となりますこと、ご了承ください。

Q7.製品のログの出力先
ATA,AATP共に動作時にログを出力いたします。
こちらを確認し、トラブルシュートを行うこととなります。
ATAの動作ログについては以下をご参照ください。

『ATAログを使用したATAのトラブルシューティング』
https://docs.microsoft.com/ja-jp/advanced-threat-analytics/troubleshooting-ata-using-logs

AATPの動作ログについては以下をご参照ください。

『ATPログを使用したAATPセンサーのトラブルシューティング』
https://docs.microsoft.com/ja-jp/azure-advanced-threat-protection/troubleshooting-atp-using-logs

Q8.アラートが出力されたら何を確認すればよいか
基本的にはユーザー（端末）側の処理と照らし併せ、意図的な処理かどうかを確認します。
ATA/AATPは不正と"思われる"認証動作を検出するため、必ずしも危険が存在するわけではございませんが、ユーザーが意図していないアラートが出力された場合には以下の公開情報にある対処策を実施することを推奨いたします。

[ATA]
以下のサイトより、対処方法をご参照ください。

『AdvancedThreatAnalytics疑わしいアクティビティガイド』
https://docs.microsoft.com/ja-jp/advanced-threat-analytics/suspicious-activity-guide

[AATP]
以下のサイトから"チュートリアル"に記載されているアラートの対処方法をご参照ください。

『チュートリアル:偵察のアラート』
https://docs.microsoft.com/ja-jp/azure-advanced-threat-protection/atp-reconnaissance-alerts


上記情報が少しでもお客様のお役に立てば幸いです。

この情報は2020/02/12時点のものとなります。
今後予期せず変更される可能性がございますので、ご留意くださいますようお願い申し上げます。

元の記事
https://social.technet.microsoft.com/Forums/ja-JP/880d1907-e5e3-46ef-9475-6861d80eab39/faq-microsoft-advanced-threat-analyticsataazure-advanced-threat-protectionaatp?forum=jpsecurity
