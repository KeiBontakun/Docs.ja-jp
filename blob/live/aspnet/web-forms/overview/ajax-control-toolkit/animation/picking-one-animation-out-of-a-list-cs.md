---
uid: web-forms/overview/ajax-control-toolkit/animation/picking-one-animation-out-of-a-list-cs
title: "(C#) リストから 1 つのアニメーションをピッキング |Microsoft ドキュメント"
author: wenz
description: "アニメーション コントロール、ASP.NET AJAX コントロール Toolkit ではなくコントロールだけアニメーションをコントロールに追加するために全体のフレームワークです。 フレームワークも許可しています."
ms.author: aspnetcontent
manager: wpickett
ms.date: 06/02/2008
ms.topic: article
ms.assetid: 06a776fe-7c73-4ca7-8e02-5260a86edc03
ms.technology: dotnet-webforms
ms.prod: .net-framework
msc.legacyurl: /web-forms/overview/ajax-control-toolkit/animation/picking-one-animation-out-of-a-list-cs
msc.type: authoredcontent
ms.openlocfilehash: a24c4ffe49df4eb663f833eb1814f7cbcf15e07e
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2017
---
<a name="picking-one-animation-out-of-a-list-c"></a><span data-ttu-id="02c9d-104">選択リスト (c#) から 1 つのアニメーション</span><span class="sxs-lookup"><span data-stu-id="02c9d-104">Picking One Animation Out Of a List (C#)</span></span>
====================
<span data-ttu-id="02c9d-105">によって[Christian Wenz](https://github.com/wenz)</span><span class="sxs-lookup"><span data-stu-id="02c9d-105">by [Christian Wenz](https://github.com/wenz)</span></span>

<span data-ttu-id="02c9d-106">[コードをダウンロードする](http://download.microsoft.com/download/f/9/a/f9a26acd-8df4-4484-8a18-199e4598f411/Animation5.cs.zip)または[PDF のダウンロード](http://download.microsoft.com/download/6/7/1/6718d452-ff89-4d3f-a90e-c74ec2d636a3/animation5CS.pdf)</span><span class="sxs-lookup"><span data-stu-id="02c9d-106">[Download Code](http://download.microsoft.com/download/f/9/a/f9a26acd-8df4-4484-8a18-199e4598f411/Animation5.cs.zip) or [Download PDF](http://download.microsoft.com/download/6/7/1/6718d452-ff89-4d3f-a90e-c74ec2d636a3/animation5CS.pdf)</span></span>

> <span data-ttu-id="02c9d-107">アニメーション コントロール、ASP.NET AJAX コントロール Toolkit ではなくコントロールだけアニメーションをコントロールに追加するために全体のフレームワークです。</span><span class="sxs-lookup"><span data-stu-id="02c9d-107">The Animation control in the ASP.NET AJAX Control Toolkit is not just a control but a whole framework to add animations to a control.</span></span> <span data-ttu-id="02c9d-108">フレームワークでは、プログラマによっては一部の JavaScript コードの評価、アニメーションのリストから 1 つのアニメーションを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="02c9d-108">The framework also allows the programmer to pick one animation out of a list of animations, depending on the evaluation of some JavaScript code.</span></span>


## <a name="overview"></a><span data-ttu-id="02c9d-109">概要</span><span class="sxs-lookup"><span data-stu-id="02c9d-109">Overview</span></span>

<span data-ttu-id="02c9d-110">アニメーション コントロール、ASP.NET AJAX コントロール Toolkit ではなくコントロールだけアニメーションをコントロールに追加するために全体のフレームワークです。</span><span class="sxs-lookup"><span data-stu-id="02c9d-110">The Animation control in the ASP.NET AJAX Control Toolkit is not just a control but a whole framework to add animations to a control.</span></span> <span data-ttu-id="02c9d-111">フレームワークでは、プログラマによっては一部の JavaScript コードの評価、アニメーションのリストから 1 つのアニメーションを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="02c9d-111">The framework also allows the programmer to pick one animation out of a list of animations, depending on the evaluation of some JavaScript code.</span></span>

## <a name="steps"></a><span data-ttu-id="02c9d-112">手順</span><span class="sxs-lookup"><span data-stu-id="02c9d-112">Steps</span></span>

<span data-ttu-id="02c9d-113">まず、含める、 `ScriptManager` ; ページで次に、ASP.NET AJAX ライブラリが読み込まれるコントロール ツールキットを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="02c9d-113">First of all, include the `ScriptManager` in the page; then, the ASP.NET AJAX library is loaded, making it possible to use the Control Toolkit:</span></span>

[!code-aspx[Main](picking-one-animation-out-of-a-list-cs/samples/sample1.aspx)]

<span data-ttu-id="02c9d-114">アニメーションは、次のようなテキストのパネルに適用されます。</span><span class="sxs-lookup"><span data-stu-id="02c9d-114">The animation will be applied to a panel of text which looks like this:</span></span>

[!code-aspx[Main](picking-one-animation-out-of-a-list-cs/samples/sample2.aspx)]

<span data-ttu-id="02c9d-115">パネルの関連付けられている CSS クラス、nice の背景色を定義し、パネルの固定幅を設定します。</span><span class="sxs-lookup"><span data-stu-id="02c9d-115">In the associated CSS class for the panel, define a nice background color and also set a fixed width for the panel:</span></span>

[!code-css[Main](picking-one-animation-out-of-a-list-cs/samples/sample3.css)]

<span data-ttu-id="02c9d-116">次に、追加、`AnimationExtender`のページを提供する、 `ID`、`TargetControlID`属性と、任意`runat="server":`</span><span class="sxs-lookup"><span data-stu-id="02c9d-116">Then, add the `AnimationExtender` to the page, providing an `ID`, the `TargetControlID` attribute and the obligatory `runat="server":`</span></span>

[!code-aspx[Main](picking-one-animation-out-of-a-list-cs/samples/sample4.aspx)]

<span data-ttu-id="02c9d-117">内で、`<Animations>`ノードを使用して`<OnLoad>`ページが完全に読み込まれた後に、アニメーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="02c9d-117">Within the `<Animations>` node, use `<OnLoad>` to run the animations once the page has been fully loaded.</span></span> <span data-ttu-id="02c9d-118">正規のアニメーションでは、いずれかではなく、`<Case>`要素が関係します。</span><span class="sxs-lookup"><span data-stu-id="02c9d-118">Instead of one of the regular animations, the `<Case>` element comes into play.</span></span> <span data-ttu-id="02c9d-119">その SelectScript 属性の値が評価されます。戻り値を数値にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="02c9d-119">The value of its SelectScript attribute is evaluated; the return value must be numerical.</span></span> <span data-ttu-id="02c9d-120">この数は、サブアニメーション内のいずれかによって&lt;ケース&gt;を実行します。</span><span class="sxs-lookup"><span data-stu-id="02c9d-120">Depending on this number, one of the subanimations within &lt;Case&gt; is executed.</span></span> <span data-ttu-id="02c9d-121">たとえば、SelectScript は 2 に評価されると、コントロール Toolkit の実行内で 3 番目のアニメーション&lt;ケース&gt;(カウント 0 から始まる)。</span><span class="sxs-lookup"><span data-stu-id="02c9d-121">For instance, if SelectScript evaluates to 2, the Control Toolkit runs the third animation within &lt;Case&gt; (counting starts at 0).</span></span>

<span data-ttu-id="02c9d-122">次のマークアップを次の 3 つサブアニメーションを定義します。 幅をサイズ変更、サイズの高さを変更するとフェードアウトします。JavaScript コード (`Math.floor(3 * Math.random())`) 3 つのアニメーションのいずれかが実行されるため、0 ~ 2 の数値を取得します。</span><span class="sxs-lookup"><span data-stu-id="02c9d-122">The following markup defines three subanimations: Resizing the width, resizing the height, and fading out. The JavaScript code (`Math.floor(3 * Math.random())`) then picks a number between 0 and 2, so that one of the three animations is run:</span></span>

[!code-aspx[Main](picking-one-animation-out-of-a-list-cs/samples/sample5.aspx)]


<span data-ttu-id="02c9d-123">[![考えられる 3 つのアニメーションのいずれかの: パネルが広くなります。](picking-one-animation-out-of-a-list-cs/_static/image2.png)](picking-one-animation-out-of-a-list-cs/_static/image1.png)</span><span class="sxs-lookup"><span data-stu-id="02c9d-123">[![One of the possible three animations: The panel gets wider](picking-one-animation-out-of-a-list-cs/_static/image2.png)](picking-one-animation-out-of-a-list-cs/_static/image1.png)</span></span>

<span data-ttu-id="02c9d-124">考えられる 3 つのアニメーションのいずれかの: パネルが広くなる ([フルサイズのイメージを表示するをクリックして](picking-one-animation-out-of-a-list-cs/_static/image3.png))</span><span class="sxs-lookup"><span data-stu-id="02c9d-124">One of the possible three animations: The panel gets wider ([Click to view full-size image](picking-one-animation-out-of-a-list-cs/_static/image3.png))</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="02c9d-125">[前へ](animation-depending-on-a-condition-cs.md)
[次へ](animating-in-response-to-user-interaction-cs.md)</span><span class="sxs-lookup"><span data-stu-id="02c9d-125">[Previous](animation-depending-on-a-condition-cs.md)
[Next](animating-in-response-to-user-interaction-cs.md)</span></span>