---
title: Excel ファイルに対する暗号/復号処理の遅延について
date: 2020-6-24 03:19:00
tags:
- Rights Management Service
---

本フォーラムは 日本マイクロソフトサポートより Rights Management Services Client 2.1 で確認しております動作仕様について情報を掲載しております。

[事象]
Rights Management Services Client 2.1 を使用して、ネットワーク共有フォルダーに格納されている Excel ファイルを暗号/復号する際に、ファイル形式によって、処理時間に差異があることを確認しております。
同じファイル サイズの XLSX 形式と XLS 形式のファイルの処理を比較した場合に、Office ファイルの構造の違いにより、処理されるデータ量などが異なることから、より多くの通信が発生し、XLSX 形式のファイルの処理に、より多くの時間がかかることを確認しております。

[詳細]
以下の方法にて、XLSX 形式のファイルを暗号/復号した場合に事象が発生することを確認しております。

・Rights Management Service Client 2.1 の IpcfEncryptFile/IpcfDecryptFile を使用

XLSX 形式のファイル構造に起因しておりますため、Rights Management Service Client 2.1 のバージョンに関わらず、すべてのバージョンにて事象が発生することが想定されます。
※ 現在最新のバージョン 1.0.4114.0 でも事象の再現を確認しております。

また、DOCX や PPTX 形式など、その他の Open XML 形式のファイルにおきましても、DOC や PPT 形式などと比較した場合に、同様に処理時間に差異が発生する可能性があります。

[回避策]
暗号/復号対象となるファイルを、暗号/復号処理を行う端末のローカル フォルダー上に、事前に配置することで、遅延を回避することが可能です。

なお、本情報の内容は、作成日時点でのものであり、予告なく変更される場合があります。
何卒ご留意いただけますようお願い申し上げます。

元の記事
https://social.technet.microsoft.com/Forums/ja-JP/ceadc243-ec23-4c42-879f-9f6431fbad42/excel?forum=jpsecurity
