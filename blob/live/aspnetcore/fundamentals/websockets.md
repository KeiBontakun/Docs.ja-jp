---
title: "ASP.NET Core での Websocket のサポート"
author: tdykstra
description: "ASP.NET Core で Websocket を開始する方法を説明します。"
ms.author: tdykstra
manager: wpickett
ms.date: 03/25/2017
ms.topic: article
ms.technology: aspnet
ms.prod: aspnet-core
uid: fundamentals/websockets
ms.openlocfilehash: 46c1f42b925a43df470d7491a1e259ab51ea5f50
ms.sourcegitcommit: 3e303620a125325bb9abd4b2d315c106fb8c47fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="introduction-to-websockets-in-aspnet-core"></a><span data-ttu-id="47d9d-103">Websocket の ASP.NET Core の概要</span><span class="sxs-lookup"><span data-stu-id="47d9d-103">Introduction to WebSockets in ASP.NET Core</span></span>

<span data-ttu-id="47d9d-104">によって[Tom Dykstra](https://github.com/tdykstra)と[Andrew スタントン-看護師](https://github.com/anurse)</span><span class="sxs-lookup"><span data-stu-id="47d9d-104">By [Tom Dykstra](https://github.com/tdykstra) and [Andrew Stanton-Nurse](https://github.com/anurse)</span></span>

<span data-ttu-id="47d9d-105">この記事では、ASP.NET Core で Websocket を開始する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="47d9d-105">This article explains how to get started with WebSockets in ASP.NET Core.</span></span> <span data-ttu-id="47d9d-106">[WebSocket](https://wikipedia.org/wiki/WebSocket) は TCP 接続を使用した双方向の永続的通信チャネルを有効にするプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="47d9d-106">[WebSocket](https://wikipedia.org/wiki/WebSocket) is a protocol that enables two-way persistent communication channels over TCP connections.</span></span> <span data-ttu-id="47d9d-107">チャット、株価情報、ゲームなどのアプリケーションの使用は、web アプリケーションでのリアルタイムの機能を使用する任意の場所。</span><span class="sxs-lookup"><span data-stu-id="47d9d-107">It is used for applications such as chat, stock tickers, games, anywhere you want real-time functionality in a web application.</span></span>

<span data-ttu-id="47d9d-108">[表示またはダウンロードするサンプル コード](https://github.com/aspnet/Docs/tree/master/aspnetcore/fundamentals/websockets/sample)([をダウンロードする方法](xref:tutorials/index#how-to-download-a-sample))。</span><span class="sxs-lookup"><span data-stu-id="47d9d-108">[View or download sample code](https://github.com/aspnet/Docs/tree/master/aspnetcore/fundamentals/websockets/sample) ([how to download](xref:tutorials/index#how-to-download-a-sample)).</span></span> <span data-ttu-id="47d9d-109">参照してください、[次の手順](#next-steps)詳細についてはします。</span><span class="sxs-lookup"><span data-stu-id="47d9d-109">See the [Next Steps](#next-steps) section for more information.</span></span>


## <a name="prerequisites"></a><span data-ttu-id="47d9d-110">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="47d9d-110">Prerequisites</span></span>

* <span data-ttu-id="47d9d-111">ASP.NET Core 1.1 (は実行されません 1.0)</span><span class="sxs-lookup"><span data-stu-id="47d9d-111">ASP.NET Core 1.1 (does not run on 1.0)</span></span>
* <span data-ttu-id="47d9d-112">ASP.NET Core 上で実行される OS:</span><span class="sxs-lookup"><span data-stu-id="47d9d-112">Any OS that ASP.NET Core runs on:</span></span>
  
  * <span data-ttu-id="47d9d-113">Windows 7/Windows Server 2008 以降</span><span class="sxs-lookup"><span data-stu-id="47d9d-113">Windows 7 / Windows Server 2008 and later</span></span>
  * <span data-ttu-id="47d9d-114">Linux</span><span class="sxs-lookup"><span data-stu-id="47d9d-114">Linux</span></span>
  * <span data-ttu-id="47d9d-115">macOS</span><span class="sxs-lookup"><span data-stu-id="47d9d-115">macOS</span></span>

* <span data-ttu-id="47d9d-116">**例外**: 場合は、IIS での windows アプリの実行中または WebListener で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47d9d-116">**Exception**: If your app runs on Windows with IIS, or with WebListener, you must use:</span></span>

  * <span data-ttu-id="47d9d-117">Windows 8/Windows Server 2012 以降</span><span class="sxs-lookup"><span data-stu-id="47d9d-117">Windows 8 / Windows Server 2012 or later</span></span>
  * <span data-ttu-id="47d9d-118">IIS 8 IIS 8 Express/</span><span class="sxs-lookup"><span data-stu-id="47d9d-118">IIS 8 / IIS 8 Express</span></span>
  * <span data-ttu-id="47d9d-119">IIS で WebSocket を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="47d9d-119">WebSocket must be enabled in IIS</span></span>

* <span data-ttu-id="47d9d-120">サポートされるブラウザー http://caniuse.com/#feat=websockets を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47d9d-120">For supported browsers, see http://caniuse.com/#feat=websockets.</span></span>

## <a name="when-to-use-it"></a><span data-ttu-id="47d9d-121">使用する状況</span><span class="sxs-lookup"><span data-stu-id="47d9d-121">When to use it</span></span>

<span data-ttu-id="47d9d-122">ソケット接続で直接作業する必要がある場合は、Websocket を使用します。</span><span class="sxs-lookup"><span data-stu-id="47d9d-122">Use WebSockets when you need to work directly with a socket connection.</span></span> <span data-ttu-id="47d9d-123">たとえば、リアルタイムのゲームを最高のパフォーマンスを必要があります。</span><span class="sxs-lookup"><span data-stu-id="47d9d-123">For example, you might need the best possible performance for a real-time game.</span></span>

<span data-ttu-id="47d9d-124">[ASP.NET SignalR](https://docs.microsoft.com/aspnet/signalr/overview/getting-started/introduction-to-signalr)充実したは、リアルタイムの機能はアプリケーション モデルは、ASP.NET、ASP.NET Core いない上でのみ実行します。</span><span class="sxs-lookup"><span data-stu-id="47d9d-124">[ASP.NET SignalR](https://docs.microsoft.com/aspnet/signalr/overview/getting-started/introduction-to-signalr) provides a richer application model for real-time functionality, but it runs only on ASP.NET, not ASP.NET Core.</span></span> <span data-ttu-id="47d9d-125">SignalR の中核となるバージョンがあるが開発です。を実行する、進行状況を参照してください、 [SignalR Core の GitHub リポジトリ](https://github.com/aspnet/SignalR)です。</span><span class="sxs-lookup"><span data-stu-id="47d9d-125">A Core version of SignalR is under development; to follow its progress, see the [GitHub repository for SignalR Core](https://github.com/aspnet/SignalR).</span></span>

<span data-ttu-id="47d9d-126">SignalR Core を待機しない場合は、できる Websocket を直接使用するようになりました。</span><span class="sxs-lookup"><span data-stu-id="47d9d-126">If you don't want to wait for SignalR Core, you can use WebSockets directly now.</span></span> <span data-ttu-id="47d9d-127">ただし、SignalR 提供するなどの機能を開発する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47d9d-127">But you might have to develop features that SignalR would provide, such as:</span></span>

* <span data-ttu-id="47d9d-128">広い範囲の自動フォールバックを代替トランスポート メソッドを使用して、ブラウザーのバージョンをサポートします。</span><span class="sxs-lookup"><span data-stu-id="47d9d-128">Support for a broader range of browser versions by using automatic fallback to alternative transport methods.</span></span>
* <span data-ttu-id="47d9d-129">接続のドロップと自動再接続します。</span><span class="sxs-lookup"><span data-stu-id="47d9d-129">Automatic reconnection when a connection drops.</span></span>
* <span data-ttu-id="47d9d-130">サーバー上またはその逆のメソッドを呼び出すクライアントをサポートします。</span><span class="sxs-lookup"><span data-stu-id="47d9d-130">Support for clients calling methods on the server or vice versa.</span></span>
* <span data-ttu-id="47d9d-131">複数のサーバーに合わせたスケーリングのサポート。</span><span class="sxs-lookup"><span data-stu-id="47d9d-131">Support for scaling to multiple servers.</span></span>

## <a name="how-to-use-it"></a><span data-ttu-id="47d9d-132">使用方法</span><span class="sxs-lookup"><span data-stu-id="47d9d-132">How to use it</span></span>

* <span data-ttu-id="47d9d-133">インストール、 [Microsoft.AspNetCore.WebSockets](https://www.nuget.org/packages/Microsoft.AspNetCore.WebSockets/)パッケージです。</span><span class="sxs-lookup"><span data-stu-id="47d9d-133">Install the [Microsoft.AspNetCore.WebSockets](https://www.nuget.org/packages/Microsoft.AspNetCore.WebSockets/) package.</span></span>
* <span data-ttu-id="47d9d-134">ミドルウェアを構成します。</span><span class="sxs-lookup"><span data-stu-id="47d9d-134">Configure the middleware.</span></span>
* <span data-ttu-id="47d9d-135">WebSocket 要求を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="47d9d-135">Accept WebSocket requests.</span></span>
* <span data-ttu-id="47d9d-136">メッセージを送受信します。</span><span class="sxs-lookup"><span data-stu-id="47d9d-136">Send and receive messages.</span></span>

### <a name="configure-the-middleware"></a><span data-ttu-id="47d9d-137">ミドルウェアを構成します。</span><span class="sxs-lookup"><span data-stu-id="47d9d-137">Configure the middleware</span></span>

<span data-ttu-id="47d9d-138">内で Websocket ミドルウェアを追加、`Configure`のメソッド、`Startup`クラスです。</span><span class="sxs-lookup"><span data-stu-id="47d9d-138">Add the WebSockets middleware in the `Configure` method of the `Startup` class.</span></span>

[!code-csharp[](websockets/sample/Startup.cs?name=UseWebSockets)]

<span data-ttu-id="47d9d-139">次の設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="47d9d-139">The following settings can be configured:</span></span>

* <span data-ttu-id="47d9d-140">`KeepAliveInterval`-方法プロキシ接続を維持しておくため、クライアントに"ping"フレームを送信する頻度。</span><span class="sxs-lookup"><span data-stu-id="47d9d-140">`KeepAliveInterval` - How frequently to send "ping" frames to the client, to ensure proxies keep the connection open.</span></span>
* <span data-ttu-id="47d9d-141">`ReceiveBufferSize`-データの受信に使用するバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="47d9d-141">`ReceiveBufferSize` - The size of the buffer used to receive data.</span></span> <span data-ttu-id="47d9d-142">上級ユーザーだけは、そのデータのサイズに基づくパフォーマンス チューニングのため、これを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47d9d-142">Only advanced users would need to change this, for performance tuning based on the size of their data.</span></span>

[!code-csharp[](websockets/sample/Startup.cs?name=UseWebSocketsOptions)]

### <a name="accept-websocket-requests"></a><span data-ttu-id="47d9d-143">WebSocket 要求を受け入れる</span><span class="sxs-lookup"><span data-stu-id="47d9d-143">Accept WebSocket requests</span></span>

<span data-ttu-id="47d9d-144">要求のライフ サイクルの後 (後半、`Configure`メソッドまたは例については、MVC アクション内で) かどうかは WebSocket 要求を確認し、WebSocket 要求を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="47d9d-144">Somewhere later in the request life cycle (later in the `Configure` method or in an MVC action, for example) check if it's a WebSocket request and accept the WebSocket request.</span></span>

<span data-ttu-id="47d9d-145">この例は後で、`Configure`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="47d9d-145">This example is from later in the `Configure` method.</span></span>

[!code-csharp[](websockets/sample/Startup.cs?name=AcceptWebSocket&highlight=7)]

<span data-ttu-id="47d9d-146">WebSocket 要求は、任意の URL でものがありますが、このサンプル コードの要求のみを受け付けます`/ws`です。</span><span class="sxs-lookup"><span data-stu-id="47d9d-146">A WebSocket request could come in on any URL, but this sample code only accepts requests for `/ws`.</span></span>

### <a name="send-and-receive-messages"></a><span data-ttu-id="47d9d-147">メッセージの送受信を行う</span><span class="sxs-lookup"><span data-stu-id="47d9d-147">Send and receive messages</span></span>

<span data-ttu-id="47d9d-148">`AcceptWebSocketAsync`メソッドは WebSocket 接続への TCP 接続をアップグレードし、使用する、 [WebSocket](https://docs.microsoft.com/dotnet/core/api/system.net.websockets.websocket)オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="47d9d-148">The `AcceptWebSocketAsync` method upgrades the TCP connection to a WebSocket connection and gives you a [WebSocket](https://docs.microsoft.com/dotnet/core/api/system.net.websockets.websocket) object.</span></span> <span data-ttu-id="47d9d-149">メッセージを送受信するには、WebSocket オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="47d9d-149">Use the WebSocket object to send and receive messages.</span></span>

<span data-ttu-id="47d9d-150">WebSocket 要求を受け入れる前に示したコード渡し、`WebSocket`オブジェクトを`Echo`メソッドです。 ここでの、`Echo`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="47d9d-150">The code shown earlier that accepts the WebSocket request passes the `WebSocket` object to an `Echo` method; here's the `Echo` method.</span></span> <span data-ttu-id="47d9d-151">コードでは、メッセージを受信し、すぐに、同じメッセージを返信します。</span><span class="sxs-lookup"><span data-stu-id="47d9d-151">The code receives a message and immediately sends back the same message.</span></span> <span data-ttu-id="47d9d-152">クライアントが接続を閉じるまでこれを行うループ内に保持します。</span><span class="sxs-lookup"><span data-stu-id="47d9d-152">It stays in a loop doing that until the client closes the connection.</span></span> 

[!code-csharp[](websockets/sample/Startup.cs?name=Echo)]

<span data-ttu-id="47d9d-153">このループを開始する前に、WebSocket を承諾するとミドルウェア パイプラインを終了します。</span><span class="sxs-lookup"><span data-stu-id="47d9d-153">When you accept the WebSocket before beginning this loop, the middleware pipeline ends.</span></span>  <span data-ttu-id="47d9d-154">ソケットを閉じると、パイプラインをアンワインドします。</span><span class="sxs-lookup"><span data-stu-id="47d9d-154">Upon closing the socket, the pipeline unwinds.</span></span> <span data-ttu-id="47d9d-155">つまりと同様、WebSocket を承諾すると、パイプラインに進むと、要求が停止は、たとえば MVC アクションをヒットしたときに。</span><span class="sxs-lookup"><span data-stu-id="47d9d-155">That is, the request stops moving forward in the pipeline when you accept a WebSocket, just as it would when you hit an MVC action, for example.</span></span>  <span data-ttu-id="47d9d-156">ただし、このループを終了し、ソケットを閉じると場合、に、パイプラインをバックアップする要求が行われます。</span><span class="sxs-lookup"><span data-stu-id="47d9d-156">But when you finish this loop and close the socket, the request proceeds back up the pipeline.</span></span>

## <a name="next-steps"></a><span data-ttu-id="47d9d-157">次の手順</span><span class="sxs-lookup"><span data-stu-id="47d9d-157">Next steps</span></span>

<span data-ttu-id="47d9d-158">[サンプル アプリケーション](https://github.com/aspnet/Docs/tree/master/aspnetcore/fundamentals/websockets/sample)に付属しているこの記事では、単純なエコー アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="47d9d-158">The [sample application](https://github.com/aspnet/Docs/tree/master/aspnetcore/fundamentals/websockets/sample) that accompanies this article is a simple echo application.</span></span> <span data-ttu-id="47d9d-159">WebSocket 接続を作成する web ページがあり、サーバーを再クライアントに受信したメッセージ。</span><span class="sxs-lookup"><span data-stu-id="47d9d-159">It has a web page that makes WebSocket connections, and the server just resends back to the client any messages it receives.</span></span> <span data-ttu-id="47d9d-160">(これがいない設定を IIS Express で Visual Studio を実行する)、コマンド プロンプトから実行し、http://localhost:5000 に移動します。</span><span class="sxs-lookup"><span data-stu-id="47d9d-160">Run it from a command prompt (it's not set up to run from Visual Studio with IIS Express) and navigate to http://localhost:5000.</span></span> <span data-ttu-id="47d9d-161">Web ページは、左上にある接続の状態を示しています。</span><span class="sxs-lookup"><span data-stu-id="47d9d-161">The web page shows connection status at the upper left:</span></span>

![Web ページの初期状態](websockets/_static/start.png)

<span data-ttu-id="47d9d-163">選択**接続**表示される URL に WebSocket 要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="47d9d-163">Select **Connect** to send a WebSocket request to the URL shown.</span></span>  <span data-ttu-id="47d9d-164">テスト メッセージを入力し、選択**送信**です。</span><span class="sxs-lookup"><span data-stu-id="47d9d-164">Enter a test message and select **Send**.</span></span> <span data-ttu-id="47d9d-165">終了したら、選択**閉じるソケット**です。</span><span class="sxs-lookup"><span data-stu-id="47d9d-165">When done, select **Close Socket**.</span></span> <span data-ttu-id="47d9d-166">**通信ログ**セクションは、各 open、send をレポートでありは閉じたときの操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="47d9d-166">The **Communication Log** section reports each open, send, and close action as it happens.</span></span>

![Web ページの初期状態](websockets/_static/end.png)