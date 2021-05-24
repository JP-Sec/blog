---
title: Identity Manager サービス再起動時の PCNS への影響について
date: 2019-3-30
tags:
- Identity Manager
---

こんにちは、Identity Manager サポート です。
今回は Password Change Notification Service (PCNS) を利用している環境で、連携先の Identity Manager のサービスを再起動した場合の影響について紹介します。

Identity Manager を再起動後、当該 Identity Manager と連携している PCNS を利用して、パスワード同期を行いますと以下のエラー (イベント ID: 6025) が発生します。
エラーのとおりパスワード同期は失敗しますが、1 分後にリトライされることで正常にパスワード同期が完了しますので、ご安心ください。
運用においてログを監視されている場合は、下図のとおりアプリケーション ログにエラーが出力されますので、サービス再起動時の想定された動作としてご認識いただけると幸いです。

<PCNS 稼働サーバーのアプリケーション ログ>
![](https://github.com/JP-Sec/blog/blob/main/articles/MIM/1421919.png?raw=true)

また、複数の Identity Manager と連携してパスワード同期を行っている PCNS 環境もあると思います。そのような環境においても、いずれかの Identity Manager のサービスが停止 (再起動) した場合は上記と同様の動作 (エラー & リトライ) となることをご考慮ください。

<補足情報：エラーを出力させない方法>
上述のとおり、本エラーが発生したとしても 1 分後のリトライでパスワード同期は正常に処理されますが、運用要件によってはエラーの発生自体を回避されたい管理者もいるかと思います。
そのような場合は、Identity Manager のサービス再起動に併せて、PCNS のサービス再起動も行うことで、本エラーの発生を回避することができます。

この情報は 2019/3/30 時点のものとなります。
今後予期せず変更される可能性がございますので、ご留意くださいますようお願い申し上げます。

元の記事
https://social.technet.microsoft.com/Forums/ja-JP/57239319-1aaf-4414-bffa-2d6c278f8b18/identity-manager-pcns-?forum=jpidentitymanager
