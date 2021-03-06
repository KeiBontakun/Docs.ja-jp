---
uid: web-forms/overview/ajax-control-toolkit/confirmbutton/using-a-confirmbutton-in-a-repeater-cs
title: "リピータ (c#) で、ConfirmButton の使用 |Microsoft ドキュメント"
author: wenz
description: "AJAX コントロールのツールキットで ConfirmButton extender は、[はい] を作成、ユーザーがボタンをクリックするとポップアップも含め LinkButton コントロール)/です。 場合にのみが [はい] がしています."
ms.author: aspnetcontent
manager: wpickett
ms.date: 06/02/2008
ms.topic: article
ms.assetid: a973ed3e-400c-4925-ace2-0b086b479301
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/confirmbutton/using-a-confirmbutton-in-a-repeater-cs
msc.type: authoredcontent
ms.openlocfilehash: 12fd3e4e58e6a73720ade38372caff496f7f2c97
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2017
---
<a name="using-a-confirmbutton-in-a-repeater-c"></a>リピータ (c#) で、ConfirmButton の使用
====================
によって[Christian Wenz](https://github.com/wenz)

[コードをダウンロードする](http://download.microsoft.com/download/8/6/d/86dea6c6-bb92-4fa6-aa14-f8c0f82100f5/ConfirmButton1.cs.zip)または[PDF のダウンロード](http://download.microsoft.com/download/b/6/a/b6ae89ee-df69-4c87-9bfb-ad1eb2b23373/confirmbutton1CS.pdf)

> AJAX コントロールのツールキットで ConfirmButton extender は、[はい] を作成、ユーザーがボタンをクリックするとポップアップも含め LinkButton コントロール)/です。 のみ [はい] をクリックしたボタンの操作が実行、それ以外の場合はキャンセルされます。 リピータでこれもできます。


## <a name="overview"></a>概要

AJAX コントロールのツールキットで ConfirmButton extender は、[はい] を作成、ユーザーがボタンをクリックするとポップアップも含め LinkButton コントロール)/です。 のみ [はい] をクリックしたボタンの操作が実行、それ以外の場合はキャンセルされます。 リピータでこれもできます。

## <a name="steps"></a>手順

まず、データ ソースが必要です。 このサンプルでは、AdventureWorks データベースと、Microsoft SQL Server 2005 Express Edition を使用します。 データベース (express エディションを含む)、Visual Studio のインストールのオプションの一部であるし、下にある個別のダウンロードとしても利用[https://go.microsoft.com/fwlink/?LinkId=64064](https://go.microsoft.com/fwlink/?LinkId=64064)です。 AdventureWorks データベースが SQL Server 2005 サンプルとサンプル データベースの一部 (でダウンロード[https://www.microsoft.com/downloads/details.aspx?FamilyID=e719ecf7-9f46-4312-af89-6ad8702e4e6e&amp;DisplayLang = en](https://www.microsoft.com/downloads/details.aspx?FamilyID=e719ecf7-9f46-4312-af89-6ad8702e4e6e&amp;DisplayLang=en))。 データベースをセットアップする最も簡単な方法は、Microsoft SQL Server Management Studio Express を使用する ([https://www.microsoft.com/downloads/details.aspx?表示 = c243a5ae-4bd1-4e3d-94b8-5a0f62bf7796&amp;DisplayLang = en](https://www.microsoft.com/downloads/details.aspx?FamilyID=c243a5ae-4bd1-4e3d-94b8-5a0f62bf7796&amp;DisplayLang=en)) をアタッチし、`AdventureWorks.mdf`データベース ファイル。

このサンプルのものと、SQL Server 2005 Express Edition のインスタンスが呼び出される`SQLEXPRESS`web サーバーと同じコンピューター上に存在し、これは既定の設定にもします。 セットアップが異なっている場合は、データベースの接続情報を調整する必要です。

ASP.NET AJAX とコントロール Toolkit の機能をアクティブ化するために、`ScriptManager`コントロールを任意の場所 ページで配置する必要があります (ただし内、`<form>`要素)。

[!code-aspx[Main](using-a-confirmbutton-in-a-repeater-cs/samples/sample1.aspx)]

次に、データ ソースが必要です。 わかりやすくするために、AdventureWorks の仕入先のテーブルの最初の 5 つのエントリのみが取得されます。 Visual Studio のウィザードを使用して、データ ソースにテーブル名を作成するときに注意してください (`Vendors`) は、現在正しくプレフィックスが付いていない`Purchasing`です。 次のマークアップでは、正しいの 1 つです。

[!code-aspx[Main](using-a-confirmbutton-in-a-repeater-cs/samples/sample2.aspx)]

このデータ ソースは、リピータ内で使用できます。 通常どおり、`DataBinder.Eval()`メソッドは、データ ソースからデータを取得します。 `ConfirmButtonExtender`内でコントロールを配置し、必要があります、`<ItemTemplate>`データ ソース内のすべてのエントリに対して表示されるように中継ぎ局のセクションでします。

[!code-aspx[Main](using-a-confirmbutton-in-a-repeater-cs/samples/sample3.aspx)]


[![データ ソースからの各エントリの横にある [確認] ボタンが表示されます。](using-a-confirmbutton-in-a-repeater-cs/_static/image2.png)](using-a-confirmbutton-in-a-repeater-cs/_static/image1.png)

データ ソースからの各エントリの横にある [確認] ボタンが表示されます ([フルサイズのイメージを表示するをクリックして](using-a-confirmbutton-in-a-repeater-cs/_static/image3.png))

>[!div class="step-by-step"]
[次へ](using-a-confirmbutton-in-a-repeater-vb.md)
