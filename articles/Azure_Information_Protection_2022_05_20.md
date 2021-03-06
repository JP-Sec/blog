---
title: AIP クライアントで共有フォルダ内にある複数ファイルを一括保護する場合の注意事項について
date: 2022-05-20
tags:
- Azure Information Protection
---

こんにちは。Azure Security サポートチームです。

今回は AIP クライアント (右クリックオプションの「分類して保護する」) コンソールのご利用にあたって注意する必要のシナリオがございますのでお知らせいたします。
AIP クライアントでは、個別のファイル上で右クリックを押下し、オプション内の [分類して保護する] をクリックすることで、ラベル付けを行うためのコンソールを起動できます。

この右クリックの [分類して保護する] をフォルダ上で起動させると、そのフォルダに格納されているすべてのファイルを再帰的にラベル付け処理できます。特定のフォルダ下部に含まれるコンテンツを一括処理でき、処理の終了時には処理の成功可否も確認できる便利な機能です。

**参考 URL**

エクスプローラーを使用してファイルを分類および保護する<br>
[分類&保護 - Azure Information Protection統合ラベル付けクライアント | Microsoft Docs](https://docs.microsoft.com/ja-jp/azure/information-protection/rms-client/clientv2-classify-protect#use-the-file-explorer-to-classify-and-protect-files)


**注意が必要なシナリオ**

複数ユーザーが使用するファイル共有内のフォルダについて、一括でラベル付け処理を行う際には注意が必要です。

ファイル共有に対して一括でラベル付け処理を行うユーザーとは別のユーザーが、同一フォルダ内のラベル付け対象のファイルを開いている場合、クライアントによるラベル付け処理はスキップされます。
そのため、対象フォルダに格納されているファイルが他のユーザーに利用されていても、クライアントによるラベル付けの一括操作を実施することは問題ございません。

しかしながら、複数のユーザーで同時に AIP クライアントを使用してラベル付け処理を実施した場合に、稀にファイルが破損してしまう動作を確認いたしました。

AIP クライアントでは、次のような流れでファイルに対するラベル付けが処理されます。
1. クライアントにて対象ファイルのラベルのステータスを確認する。
2. ラベル付けが必要な場合には端末の一時領域にファイルをコピーする。
3. ラベル付け処理の後に元のフォルダ パスにファイルを差し替える。

このラベル付け処理について、複数のクライアントが同一ファイルに対して全く同じタイミングで処理を行おうとすると、対象ファイルに二重に暗号化メタデータの付与を行ってしまったり、片側のクライアントによる処理で差し替え途中の不完全なデータの状態で対象ファイルがもう片方のクライアントによってキャプチャとラベル付け処理が行われてしまうことによってファイルが破損してしまう場合があります。

AIP クライアントによる一括処理を行う際に、複数のユーザーが "まったく同じタイミング" で操作を実施する状況は一般的なシナリオとしては想定されておりません。特定フォルダに対して一括でラベル付け/暗号化処理を行う場合、複数のユーザー/端末で同時に実施いただくことは避けていただけますようお願い申し上げます。

今回のお知らせは以上になります。

- ※本ブログ記事化にあたり、弊社サポートによる調査にご協力いただきましたお客様に深く感謝いたします。
- ※本情報の内容（添付文書、リンク先などを含む）は、作成日時点でのものであり、予告なく変更される場合があります。
