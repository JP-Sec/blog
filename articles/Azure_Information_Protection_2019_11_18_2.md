---
title: Azure Information Protection の通信要件に関する補足情報
date:2019-11-18 09:50:00
tags:
-Azure Information Protection
---

◆ この情報はマイクロソフトサポートからのご案内となります(更新: 2019/11/18) ◆

Azure Information Protection にてコンテンツの保護や復号機能をご利用いただく場合の通信要件につきましては、以下のように弊社公開情報にてお纏めしております。

<ファイアウォールとネットワーク インフラストラクチャ>
https://docs.microsoft.com/ja-jp/azure/information-protection/requirements#firewalls-and-network-infrastructure

上記公開情報内に記載のリンクより、許可が必要な URL などの詳細を確認することが可能です。

なお、上記は、Azure information Protection 固有の通信要件となります。
そのため、その他にも Windows OS 観点などにて許可が必要な URL があることを確認しておりますので、以下にご案内いたします。

Azure information Protection では、SSL 通信を利用いたしますので、SSL 証明書を取得する際に以下のエンドポイントへの通信が発生する場合がございます。

ctldl.windowsupdate.com

こちらは、ルート証明書更新プログラムが、Windows Update 上の信頼機関の一覧を自動的に確認し、更新プログラムがあるかどうかを確認するために使用されます。
この URL への通信が許可されていない場合に、Azure information Protection ビューアーによるファイル閲覧時にエラーが発生する事象の報告を確認しております。
そのため、Azure information Protection 利用時には、必要に応じて、こちらの URL を許可することをご検討ください。

※ 現時点では、上記以外の URL は確認できておりませんが、今後他にも通信許可が必要な URL が報告されました際には、情報を更新して参ります。

[その他の参考 URL]
ルート証明書更新プログラムについては、以下の弊社公開情報およびブログをご参照ください。

<Windows Vista、Windows Server 2008、Windows 7、および Windows Server 2008 R2 の信頼されていない証明書の自動更新ツールについて>
https://support.microsoft.com/ja-jp/help/2677070/an-automatic-updater-of-untrusted-certificates-is-available-for-window

<マイクロソフトが提供する信頼できる証明書利用基盤 ～ルート証明書更新プログラムと更新ツール ～>
https://blogs.technet.microsoft.com/jpsecurity/2013/01/16/65374/

Windows 10 端末が接続するエンドポイントについては、以下の弊社公開情報をご参考ください。

<Windows 10 Enterprise Version 1903 の接続エンドポイントの管理>
https://docs.microsoft.com/ja-jp/windows/privacy/manage-windows-1903-endpoints

上記情報が少しでもお客様のお役に立てば幸いです。

この情報は 2019/11/18 時点のものとなります。
今後予期せず変更される可能性がございますので、ご留意くださいますようお願い申し上げます。

元の記事
https://social.technet.microsoft.com/Forums/ja-JP/6c111ee2-675f-4c27-915b-2e055bc176fd/azure-information-protection?forum=jpsecurity
