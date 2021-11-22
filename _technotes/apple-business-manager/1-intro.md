---
title: "Apple Businesss Managerとは"
permalink: /technotes/apple-business-manager/
sidebar:
    nav: "apple-business-manager"
---

組織のMDMサーバ（MobileIron Cloud）をApple Business Manager（ABM）と連携させることで以下が可能になります。
- 組織で購入したiOS(iPadOS), macOSデバイスを自動的に組織のMDMに登録する。DEP: Device Enrollment Program とも呼ばれる機能です。
- 仕事で利用するアプリを組織で一括購入し、MDMを通じて管理対象デバイスに配布する。VPP: Volume Purchase Program とも呼ばれる機能です。
- User Enrollmentの利用
- ビジネス向け共有iPadの利用

Apple Business Managerを利用するには登録が必要です。詳しくは以下リンク先のAppleの記事などを参照して下さい。
- [Apple Business Managerユーザーガイド](https://support.apple.com/ja-jp/guide/apple-business-manager/welcome/web)
- [自動デバイス登録を利用する](https://support.apple.com/ja-jp/HT204142)


## Apple Business Managerで管理するもの

### デバイス
組織（企業）で購入したデバイスをABMに登録し、それらを組織のMDMサーバに割り当てることができます。BYODで個人が組織に持ち込んでいるデバイスをABMに登録することはできません。組織がAppleの認定リセラー（アップルストアや通信キャリアなど）を通じて購入するデバイスは、事前にApple認定リセラーと必要な手続きを済ませておくことにより、組織のABMに自動的に認識されます。iPhoneやiPadはそれ以外の方法で購入した場合でも後からABMに登録する方法がありますが、MacについてはApple認定リセラーから法人としての購入時以外にABMに登録することはできません。

### MDMサーバ
ABMに登録したデバイスを、アクティベーション時に自動的に組織のMDMサーバへ登録させるために、ABMにMDMサーバを登録します。ABMと複数のMDMサーバを連携する場合、ABMでデバイス毎に登録先のMDMサーバを設定できます。またデフォルトのMDMサーバを設定し、新しく購入するデバイスを自動的割り当てることもできます。

### Appとブック
iTunes Storeで公開されているアプリのライセンスを、ABM内で組織としてまとめて購入できます。組織で購入したライセンスは、MDMサーバの設定によりユーザー（Apple ID）またはデバイス（ハードウェア）に割り当てることができます。業務で利用したいアプリがiTunes Store上で有料か無料かにかかわらず、ABMで購入し、MDMによってデバイスに対するライセンス割り当てを行うと、ユーザーがApple IDにサインインしていなくてもアプリをインストール・利用できて便利です。

**特定のユースケースにおけるライセンス割り当て** User Enrollmentではユーザー（Managed Apple ID）へのライセンス割り当て、共有iPadではデバイスへのライセンス割り当てのみが可能です。なおMobileIron Cloudにおいては、これらのユースケースでは自動的に適切なライセンス割り当てを行います。
{: .notice--info}

**Appとブックの地域性** ABM内で購入したアプリは、ユーザーやデバイスが異なる国や地域にいる場合でも、その地域のiTunes Storeで提供されているアプリであればインストールすることができます。
ただし管理者がABMでアプリを購入する際には地域の制約を受けます。例えば日本の組織としてABMに登録している場合、ABM内で購入できるのは日本のiTunes Storeで提供されているアプリのみです。
{: .notice--info}

### 場所
ABMにおける「場所」とは、Appとブックのライセンス購入と割り当てを行うための、組織内のあるグループを表す概念です。必ずしも物理的な場所によるグルーピングである必要はありません。例えば部門毎に必要な数のアプリライセンスをそれぞれ購入する目的で場所を分けることもあります。場所毎に対応するMDMサーバを通じてAppとブックのライセンス割り当てを行います。１つのMDMサーバで複数の場所を扱っても問題ありません。場所に割り当てているAppとブックのライセンスのうち、デバイスやユーザーで使用中でない空きライセンスを他の場所に転送することもできます。

### アカウント
アカウントとは組織で管理するユーザーのApple IDです。

**ABM管理者のアカウント：**  
ABMには最初に登録した１人の管理者アカウントの他に、管理者アカウントを追加することができます。場所ごとに管理者を配置して、それぞれの場所で必要になるアプリの購入権限を持たせるといった使い方ができます。 

**デバイスユーザーのアカウント：**  
個人のデバイスをUser Enrollmentで組織のMDMに登録するとき、あるいは共有iPadとして構成されたデバイスを利用するときには、デバイスのユーザーは組織が作成した「管理対象Apple ID」でサインインする必要があります。これらの管理モードを使用しない場合、デバイスユーザーのために管理対象Apple IDを作成する必要はありません。