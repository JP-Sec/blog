---
title: Azure Information Protection サービスプリンシパルを用いた認証が失敗する事象について 更新:2019/12/3
date: 2019-8-30
tags:
- Azure Information Protection
---

◆ この情報はマイクロソフトサポートからのご案内となります(更新: 2019/12/3) ◆

Azure Information Protection サービスをご利用される場合にサービスプリンシパル（Set-RMSServerAuthentication）を用いる場合に認証ができず、処理に失敗する事象が確認できております。
この事象について以下のとおりご連絡いたします。

[事象]
2019 年 8 月初旬より、サービスプリンシパルを用いて、Azure Information Protection の機能を利用する場合に 0x80040211 や 0x800704dc など、認証に関するエラーが発生いたします。
なお、ユーザーアカウントで AIP をご利用されている場合については影響を受けません。

[対象製品]
・Azure Information Protection Client
・RMS Client 2.1

[対象バージョン]
・1.53.10.0 未満のバージョンの Azure Information Protection Client
・1.0.4114.0 未満のバージョンの RMS Client 2.1

[回避策]
各アプリケーションのバージョンアップが回避策となります。
- Azure Information Protection Client
- RMS Client 2.1 

[原因]
2018 年に Symmetric Key の実装が更新され、RMS サービス側で下位互換性のサポートを行わなくなったため、サポート対象外のバージョンのアプリケーションをご利用されていた場合に当該事象が発生したことを確認いたしました。
ご迷惑をおかけいたしまして誠に申し訳ございませんが、当該事象が確認された場合には AIP Client、及び、RMS Client のバージョンアップを実施いただけますようお願いいたします。

この情報は 2019/12/3 時点のものとなります。
今後予期せず変更される可能性がございますので、ご留意くださいますようお願い申し上げます。

元の記事
https://social.technet.microsoft.com/Forums/ja-JP/c3ec69b1-6133-45ff-9470-11c7e022437a/azure-information-protection-2019123?forum=jpsecurity
