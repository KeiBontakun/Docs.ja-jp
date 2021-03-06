---
uid: web-forms/overview/ajax-control-toolkit/dropshadow/adjusting-the-z-index-of-a-dropshadow-cs
title: "(C#)、DropShadow の Z インデックスを調整する |Microsoft ドキュメント"
author: wenz
description: "AJAX コントロール ツールキットの DropShadow コントロールは、ドロップ シャドウ付きパネルを拡張します。 ただしこのシャドウは、insta の他のコントロールを持つ場合があります競合しています."
ms.author: aspnetcontent
manager: wpickett
ms.date: 06/02/2008
ms.topic: article
ms.assetid: 14133833-e518-4347-87b9-6b6f71f14a77
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/dropshadow/adjusting-the-z-index-of-a-dropshadow-cs
msc.type: authoredcontent
ms.openlocfilehash: 161f02daa5dd1f0e21853c1b7c1a65c1a9aa5d03
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2017
---
<a name="adjusting-the-z-index-of-a-dropshadow-c"></a>(C#)、DropShadow の Z インデックスを調整します。
====================
によって[Christian Wenz](https://github.com/wenz)

[コードをダウンロードする](http://download.microsoft.com/download/5/1/6/51652a81-500b-4f6b-88d3-617103e7941e/DropShadow1.cs.zip)または[PDF のダウンロード](http://download.microsoft.com/download/b/6/a/b6ae89ee-df69-4c87-9bfb-ad1eb2b23373/dropshadow1CS.pdf)

> AJAX コントロール ツールキットの DropShadow コントロールは、ドロップ シャドウ付きパネルを拡張します。 ただしこのシャドウは、他のコントロールでは、ASP.NET メニュー コントロールのインスタンスとも競合しています。 ときにメニュー項目が表示されます、ドロップ シャドウの背後に表示されます。


## <a name="overview"></a>概要

AJAX コントロール ツールキットの DropShadow コントロールは、ドロップ シャドウ付きパネルを拡張します。 ただしこのシャドウは、他のコントロールでは、ASP.NET メニュー コントロールのインスタンスとも競合しています。 ときにメニュー項目が表示されます、ドロップ シャドウの背後に表示されます。

## <a name="steps"></a>手順

パネルが影響を表示するのに十分なテキストが含まれるように、十分なテキストを含む自体、パネルを使用したコードの開始します。

[!code-aspx[Main](adjusting-the-z-index-of-a-dropshadow-cs/samples/sample1.aspx)]

別のパネルが直前に配置されて、`panelShadow`パネルです。 含まれている水平方向のメニューにメニュー項目が表示されるように (または: の下)、`dropShadow`パネル)。

[!code-aspx[Main](adjusting-the-z-index-of-a-dropshadow-cs/samples/sample2.aspx)]

次に、`DropShadowExtender`を拡張する追加の`panelShadow`ドロップ シャドウ効果のあるパネル。

[!code-aspx[Main](adjusting-the-z-index-of-a-dropshadow-cs/samples/sample3.aspx)]

最後に、ASP.NET AJAX`ScriptManager`コントロール動作を制御ツールキットを有効にします。

[!code-aspx[Main](adjusting-the-z-index-of-a-dropshadow-cs/samples/sample4.aspx)]

このスクリプトを実行すると、パネルの下にあるメニュー項目が表示されます。 ただし、メニューは、CSS クラスを使用`panel`だけがある要素がもう一方のパネルの前に表示する 2 つの処理を定義します。

- 相対配置
- 正の z インデックス

[!code-css[Main](adjusting-the-z-index-of-a-dropshadow-cs/samples/sample5.css)]

次に、`DropShadowExtender`コントロールはメニュー コントロールを使用できなくなった場合は競合しません。


[![前: に、メニュー項目が表示されていません。](adjusting-the-z-index-of-a-dropshadow-cs/_static/image2.png)](adjusting-the-z-index-of-a-dropshadow-cs/_static/image1.png)

前: に、メニュー エントリは表示されません ([フルサイズのイメージを表示するをクリックして](adjusting-the-z-index-of-a-dropshadow-cs/_static/image3.png))


[![メニュー項目の表示後。](adjusting-the-z-index-of-a-dropshadow-cs/_static/image5.png)](adjusting-the-z-index-of-a-dropshadow-cs/_static/image4.png)

後: メニュー項目が表示されます ([フルサイズのイメージを表示するをクリックして](adjusting-the-z-index-of-a-dropshadow-cs/_static/image6.png))

>[!div class="step-by-step"]
[次へ](manipulating-dropshadow-properties-from-client-code-cs.md)
