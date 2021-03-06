---
uid: web-forms/overview/ajax-control-toolkit/dynamicpopulate/dynamically-populating-a-control-using-javascript-code-cs
title: "JavaScript コード (c#) を使用してコントロールを動的に作成する |Microsoft ドキュメント"
author: wenz
description: "ASP.NET AJAX コントロールのツールキットで DynamicPopulate コントロールは、メソッドを呼び出す web サービス (ページ) と、t の対象のコントロールに、結果の値を設定しています."
ms.author: aspnetcontent
manager: wpickett
ms.date: 06/02/2008
ms.topic: article
ms.assetid: cc4c2def-e88c-4456-ae8b-a6ae0ff8cc2d
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/dynamicpopulate/dynamically-populating-a-control-using-javascript-code-cs
msc.type: authoredcontent
ms.openlocfilehash: 5b3b23e16f2e4dd26f50eb3e07f35d078dd19a19
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2017
---
<a name="dynamically-populating-a-control-using-javascript-code-c"></a>JavaScript コード (c#) を使用してコントロールを動的に作成します。
====================
によって[Christian Wenz](https://github.com/wenz)

[コードをダウンロードする](http://download.microsoft.com/download/d/8/f/d8f2f6f9-1b7c-46ad-9252-e1fc81bdea3e/dynamicpopulate1.cs.zip)または[PDF のダウンロード](http://download.microsoft.com/download/b/6/a/b6ae89ee-df69-4c87-9bfb-ad1eb2b23373/dynamicpopulate1CS.pdf)

> ASP.NET AJAX コントロールのツールキットで DynamicPopulate コントロールは、メソッドを呼び出す web サービス (ページ) と、ターゲット コントロール ページで、ページの更新せずに、結果の値を入力します。 カスタムのクライアント側 JavaScript コードを使用してカタログの作成をトリガーすることもできます。


## <a name="overview"></a>概要

`DynamicPopulate` ASP.NET AJAX コントロール Toolkit でコントロールのメソッドを呼び出す web サービス (ページ) と [ページの更新なし] ページでターゲット コントロールに、結果の値を設定します。 カスタムのクライアント側 JavaScript コードを使用してカタログの作成をトリガーすることもできます。

## <a name="steps"></a>手順

まず、ASP.NET Web サービスによって呼び出されるメソッドを実装する必要があります、`DynamicPopulateExtender`コントロール。 Web サービス メソッドを実装する`getDate()`と呼ばれる、文字列型の引数を 1 つ指定する必要が`contextKey`、ので、`DynamicPopulate`コントロールは、web サービスの呼び出しごとに 2 つのコンテキスト情報を送信します。 次のコードは (ファイル`DynamicPopulate.cs.asmx`) 3 つの形式のいずれかで現在の日付を取得します。

[!code-aspx[Main](dynamically-populating-a-control-using-javascript-code-cs/samples/sample1.aspx)]

次の手順では、新しい ASP.NET サイトを作成し、ASP.NET AJAX ScriptManager コントロールと起動します。

[!code-aspx[Main](dynamically-populating-a-control-using-javascript-code-cs/samples/sample2.aspx)]

ラベル コントロールを追加し、(たとえば、同じ名前の HTML コントロールを使用して、または`<asp:Label />`web コントロール) web サービス呼び出しの結果は後で説明します。

[!code-aspx[Main](dynamically-populating-a-control-using-javascript-code-cs/samples/sample3.aspx)]

次に、含める、`DynamicPopulateExtender`制御し、web サービス情報、対象のコントロールがカスタム JavaScript を使用して、後で実行されます作成をトリガーするコントロールの名前ではなくを提供します。

[!code-aspx[Main](dynamically-populating-a-control-using-javascript-code-cs/samples/sample4.aspx)]

JavaScript の部分するようになりました。 `$find()` ASP.NET AJAX ライブラリによって定義された関数がなど、ASP.NET AJAX コントロール Toolkit のサーバー側オブジェクトへの参照を返します`DynamicPopulateExtender`です。 現在のファイル、`$find("dpe")`ものへの参照を返します`DynamicPopulateExtender`ページ内のコントロールです。 呼び出されるメソッドを公開`populate()`動的カタログの作成処理をトリガーします。 `populate()`メソッドには、1 つの引数が必要です。 コンテキスト キーへの引数となる、 `getDate()` web メソッド。 たとえば、`$find("dpe").populate("format1")`月-日-年の形式で現在の日付でラベルに表示します。

サンプルをより柔軟に行うには、いくつかの日付形式の間で、ユーザーが今すぐを選択します。 それぞれのうち、ラジオ ボタンが表示されます。 1 回クリックするオプション ボタンで、JavaScript コードが動的に追加、選択した日付の書式付きのラベル。 これらのオプション ボタンを次に示します。

[!code-aspx[Main](dynamically-populating-a-control-using-javascript-code-cs/samples/sample5.aspx)]

ラジオ ボタン、JavaScript 式のコンテキスト内でなお`this.value`まったく同じ情報である場合は、現在のボタンの値を参照、`getDate()`メソッドを使用できます。


[![ボタンをクリックしてからサーバーの指定された形式で日付を取得します。](dynamically-populating-a-control-using-javascript-code-cs/_static/image2.png)](dynamically-populating-a-control-using-javascript-code-cs/_static/image1.png)

ボタンをクリックしてからサーバーの指定された形式で日付を取得する ([フルサイズのイメージを表示するをクリックして](dynamically-populating-a-control-using-javascript-code-cs/_static/image3.png))

>[!div class="step-by-step"]
[前へ](dynamically-populating-a-control-cs.md)
[次へ](using-dynamicpopulate-with-a-user-control-and-javascript-cs.md)
