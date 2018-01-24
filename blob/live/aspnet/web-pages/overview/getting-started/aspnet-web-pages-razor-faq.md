---
uid: web-pages/overview/getting-started/aspnet-web-pages-razor-faq
title: "ASP.NET Web Pages (Razor) FAQ |Microsoft ドキュメント"
author: tfitzmac
description: "この記事は、WebMatrix と ASP.NET Web Pages (Razor) に関するいくつかのよく寄せられる質問を一覧表示します。 ソフトウェアのバージョンが、チュートリアル ASP.NET Web Pages で使用 (R..."
ms.author: aspnetcontent
manager: wpickett
ms.date: 02/07/2014
ms.topic: article
ms.assetid: b137bd04-25e1-47cb-9d96-ef2e179ecf1f
ms.technology: dotnet-webpages
ms.prod: .net-framework
msc.legacyurl: /web-pages/overview/getting-started/aspnet-web-pages-razor-faq
msc.type: authoredcontent
ms.openlocfilehash: 7f6dc3b56a33bcbe3e1e4086681ca1ba76d7d153
ms.sourcegitcommit: 9a9483aceb34591c97451997036a9120c3fe2baf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2017
---
<a name="aspnet-web-pages-razor-faq"></a><span data-ttu-id="7eaf7-104">ASP.NET Web Pages (Razor) FAQ</span><span class="sxs-lookup"><span data-stu-id="7eaf7-104">ASP.NET Web Pages (Razor) FAQ</span></span>
====================
<span data-ttu-id="7eaf7-105">によって[Tom FitzMacken](https://github.com/tfitzmac)</span><span class="sxs-lookup"><span data-stu-id="7eaf7-105">by [Tom FitzMacken](https://github.com/tfitzmac)</span></span>

> > [!NOTE] 
> > <span data-ttu-id="7eaf7-106">WebMatrix は推奨されなくなりました統合開発環境として ASP.NET Web Pages のです。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-106">WebMatrix is no longer recommended as an integrated development environment for ASP.NET Web Pages.</span></span> <span data-ttu-id="7eaf7-107">使用して[Visual Studio](xref:aspnet/web-pages/overview/getting-started/program-asp-net-web-pages-in-visual-studio)または[Visual Studio Code](https://code.visualstudio.com/)です。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-107">Use [Visual Studio](xref:aspnet/web-pages/overview/getting-started/program-asp-net-web-pages-in-visual-studio) or [Visual Studio Code](https://code.visualstudio.com/).</span></span>
>
> <span data-ttu-id="7eaf7-108">この記事は、WebMatrix と ASP.NET Web Pages (Razor) に関するいくつかのよく寄せられる質問を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-108">This article lists some frequently asked questions about ASP.NET Web Pages (Razor) and WebMatrix.</span></span>
> 
> ## <a name="software-versions-used-in-the-tutorial"></a><span data-ttu-id="7eaf7-109">このチュートリアルで使用されているソフトウェアのバージョン</span><span class="sxs-lookup"><span data-stu-id="7eaf7-109">Software versions used in the tutorial</span></span>
> 
> 
> - <span data-ttu-id="7eaf7-110">ASP.NET Web Pages (Razor) 3</span><span class="sxs-lookup"><span data-stu-id="7eaf7-110">ASP.NET Web Pages (Razor) 3</span></span>
> - <span data-ttu-id="7eaf7-111">Visual Studio 2013</span><span class="sxs-lookup"><span data-stu-id="7eaf7-111">Visual Studio 2013</span></span>
> - <span data-ttu-id="7eaf7-112">WebMatrix 3</span><span class="sxs-lookup"><span data-stu-id="7eaf7-112">WebMatrix 3</span></span>
>   
> 
> <span data-ttu-id="7eaf7-113">このチュートリアルは、ASP.NET Web Pages 2、WebMatrix 2、および Visual Studio 2012 でも動作します。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-113">This tutorial also works with ASP.NET Web Pages 2, WebMatrix 2, and Visual Studio 2012.</span></span>


- [<span data-ttu-id="7eaf7-114">ASP.NET Web ページ、ASP.NET Web フォーム、ASP.NET MVC の違いは何ですか。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-114">What's the difference between ASP.NET Web Pages, ASP.NET Web Forms, and ASP.NET MVC?</span></span>](#Whats_the_difference_between_ASP.NET_Web_Pages,_ASP.NET_Web_Forms,_and_ASP.NET_MVC)
- [<span data-ttu-id="7eaf7-115">Web ページを使用するために WebMatrix ですか。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-115">Do I need WebMatrix in order to work with Web Pages?</span></span>](#Do_I_need_WebMatrix_in_order_to_work_with_Web_Pages)
- [<span data-ttu-id="7eaf7-116">ASP.NET Web フォーム ページのコントロールを Web ページを使用できますか。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-116">Can I use ASP.NET Web Forms controls on a Web Pages page?</span></span>](#Can_I_use_ASP.NET_Web_Forms_controls_on_a_Web_Pages_page)
- [<span data-ttu-id="7eaf7-117">WebMatrix を使用せず、ASP.NET Web Pages サイトを配置できますか。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-117">Can I deploy an ASP.NET Web Pages site without using WebMatrix?</span></span>](#Can_I_deploy_an_ASP.NET_Web_Pages_site_without_using_WebMatrix)
- [<span data-ttu-id="7eaf7-118">ログインをサポートするために、WebSecurity ヘルパーを使用する必要がありますは?</span><span class="sxs-lookup"><span data-stu-id="7eaf7-118">Do I have to use the WebSecurity helper to support logins?</span></span>](#Do_I_have_to_use_the_WebSecurity_helper_to_support_logins)
- [<span data-ttu-id="7eaf7-119">ASP.NET Web Pages は HTML5 をサポートしますか。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-119">Does ASP.NET Web Pages support HTML5?</span></span>](#Does_ASP.NET_Web_Pages_support_HTML5)
- [<span data-ttu-id="7eaf7-120">Web ページで JavaScript と jQuery を使用できますか。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-120">Can I use JavaScript and jQuery with Web Pages?</span></span>](#Can_I_use_JavaScript_and_jQuery_with_Web_Pages)
- [<span data-ttu-id="7eaf7-121">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="7eaf7-121">Additional Resources</span></span>](#AdditionalResources)

<span data-ttu-id="7eaf7-122">エラーおよびその他の問題に関する質問については、次を参照してください。、 [ASP.NET Web Pages (Razor) トラブルシューティング ガイド](https://go.microsoft.com/fwlink/?LinkId=253001)です。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-122">For questions about errors and other issues, see the [ASP.NET Web Pages (Razor) Troubleshooting Guide](https://go.microsoft.com/fwlink/?LinkId=253001).</span></span>

<a id="Whats_the_difference_between_ASP.NET_Web_Pages,_ASP.NET_Web_Forms,_and_ASP.NET_MVC"></a>
## <a name="whats-the-difference-between-aspnet-web-pages-aspnet-web-forms-and-aspnet-mvc"></a><span data-ttu-id="7eaf7-123">ASP.NET Web ページ、ASP.NET Web フォーム、ASP.NET MVC の違いは何ですか。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-123">What's the difference between ASP.NET Web Pages, ASP.NET Web Forms, and ASP.NET MVC?</span></span>

<span data-ttu-id="7eaf7-124">3 つすべては、動的な web アプリケーションを作成するための ASP.NET テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-124">All three are ASP.NET technologies for creating dynamic web applications:</span></span>

- <span data-ttu-id="7eaf7-125">ASP.NET Web ページは、HTML ページ、および機能の簡単、軽量構文を動的 (サーバー側) コードとデータベースへのアクセスを追加することについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-125">ASP.NET Web Pages focuses on adding dynamic (server-side) code and database access to HTML pages, and features simple and lightweight syntax.</span></span>
- <span data-ttu-id="7eaf7-126">ASP.NET Web フォームは、ページのオブジェクト モデルと従来のウィンドウ タイプ コントロール (ボタン、リストなど) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-126">ASP.NET Web Forms is based on a page object model and traditional window-type controls (buttons, lists, etc.).</span></span> <span data-ttu-id="7eaf7-127">Web フォームでは、クライアント ベース (Windows フォーム) の開発で作業したユーザーになじみのあるイベントに基づくモデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-127">Web Forms uses an event-based model that's familiar to those who've worked with client-based (Windows forms) development.</span></span>
- <span data-ttu-id="7eaf7-128">ASP.NET MVC では、ASP.NET のモデル ビュー コント ローラー パターンを実装します。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-128">ASP.NET MVC implements the model-view-controller pattern for ASP.NET.</span></span> <span data-ttu-id="7eaf7-129">「関心の分離」が強調 (処理、データ、および UI レイヤー)。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-129">The emphasis is on "separation of concerns" (processing, data, and UI layers).</span></span>

<span data-ttu-id="7eaf7-130">次の 3 つすべてのフレームワークは完全にサポートし、ASP.NET チームによって開発に進みます。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-130">All three frameworks are fully supported and continue to be developed by the ASP.NET team.</span></span> <span data-ttu-id="7eaf7-131">一般に、使用するには、どのフレームワークの選択によって異なります、バック グラウンドで ASP.NET のエクスペリエンスとします。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-131">In general, the choice of which framework to use depends on your background and experience with ASP.NET.</span></span>

<span data-ttu-id="7eaf7-132">具体的には、ASP.NET Web ページは、ページにサーバーの処理を追加する HTML を既に知っているユーザーを簡単に設計されました。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-132">ASP.NET Web Pages in particular was designed to make it easy for people who already know HTML to add server processing to their pages.</span></span> <span data-ttu-id="7eaf7-133">受講者、趣味はプログラミングの経験となっている人一般に、適切な選択であります。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-133">It's a good choice for students, hobbyists, people in general who are new to programming.</span></span> <span data-ttu-id="7eaf7-134">ASP.NET 以外の web テクノロジの使用経験を持つ開発者に適してことができます。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-134">It can also be a good choice for developers who have experience with non-ASP.NET web technologies.</span></span>

<a id="Do_I_need_WebMatrix_in_order_to_work_with_Web_Pages"></a>
## <a name="do-i-need-webmatrix-in-order-to-work-with-web-pages"></a><span data-ttu-id="7eaf7-135">Web ページを使用するために WebMatrix ですか。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-135">Do I need WebMatrix in order to work with Web Pages?</span></span>

<span data-ttu-id="7eaf7-136">いいえ。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-136">No.</span></span> <span data-ttu-id="7eaf7-137">WebMatrix は推奨されなくなりました統合開発環境として ASP.NET Web Pages のです。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-137">WebMatrix is no longer recommended as an integrated development environment for ASP.NET Web Pages.</span></span> <span data-ttu-id="7eaf7-138">使用して[Visual Studio](program-asp-net-web-pages-in-visual-studio.md)または[Visual Studio Code](https://code.visualstudio.com/)です。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-138">Use [Visual Studio](program-asp-net-web-pages-in-visual-studio.md) or [Visual Studio Code](https://code.visualstudio.com/).</span></span>

<span data-ttu-id="7eaf7-139">使用して個別のコンポーネント製品をインストールするには Visual Studio または Visual Studio のコードを使用しない場合は、 [Microsoft Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-139">If you don't want to use either Visual Studio or Visual Studio Code, you can install the component products individually using [Microsoft Web Platform Installer](https://www.microsoft.com/web/downloads/platform.aspx).</span></span> <span data-ttu-id="7eaf7-140">次の製品が必要です。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-140">You need the following products:</span></span>

- <span data-ttu-id="7eaf7-141">Microsoft .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="7eaf7-141">Microsoft .NET Framework 4.5</span></span>
- <span data-ttu-id="7eaf7-142">ASP.NET MVC 5 をインストールします (同様に、ASP.NET Web Pages framework)</span><span class="sxs-lookup"><span data-stu-id="7eaf7-142">ASP.NET MVC 5 (which installs the ASP.NET Web Pages framework as well)</span></span>
- <span data-ttu-id="7eaf7-143">IIS Express (web サーバー)</span><span class="sxs-lookup"><span data-stu-id="7eaf7-143">IIS Express (the web server)</span></span>
- <span data-ttu-id="7eaf7-144">Microsoft SQL Server Compact 4.0 (データベース)</span><span class="sxs-lookup"><span data-stu-id="7eaf7-144">Microsoft SQL Server Compact 4.0 (the database)</span></span>

<span data-ttu-id="7eaf7-145">テキスト エディターを使用して編集する*.cshtml* (または*.vbhtml*) ページ。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-145">You can use a text editor to edit *.cshtml* (or *.vbhtml*) pages.</span></span>

<span data-ttu-id="7eaf7-146">SQL Server Compact データベースの管理 (*.sdf*ファイル) を含まないツールは少し難しくなります。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-146">Managing SQL Server Compact databases (*.sdf* files) without a tool is a bit harder.</span></span> <span data-ttu-id="7eaf7-147">管理するための visual Studio containds ツール*.sdf*データベース。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-147">Visual Studio containds tools for managing *.sdf* databases.</span></span> <span data-ttu-id="7eaf7-148">多くの SQL Server 管理タスクを実行するコードでの SQL コマンドを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-148">You can also run SQL commands in code to perform many SQL Server management tasks.</span></span>

<span data-ttu-id="7eaf7-149">テストする*.cshtml*ページ統合開発環境 (IDE) を使用せず、展開したりできますライブ サーバーにします。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-149">To test *.cshtml* pages without using an integrated development environment (IDE), you can deploy them to a live server.</span></span> <span data-ttu-id="7eaf7-150">(を参照してください[WebMatrix を使用せず、ASP.NET Web Pages サイトを展開できますか](#Can_I_deploy_an_ASP.NET_Web_Pages_site_without_using_WebMatrix))。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-150">(See [Can I deploy an ASP.NET Web Pages site without using WebMatrix?](#Can_I_deploy_an_ASP.NET_Web_Pages_site_without_using_WebMatrix))</span></span>

### <a name="running-iis-express-without-using-an-ide"></a><span data-ttu-id="7eaf7-151">IIS Express、IDE を使用せずに実行します。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-151">Running IIS Express without using an IDE</span></span>

<span data-ttu-id="7eaf7-152">Web サーバーとしてコンピューターに IIS Express をインストールする場合は、ページをテストすることを使用できます。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-152">If you install IIS Express on your computer as a web server, you can use that to test the pages.</span></span> <span data-ttu-id="7eaf7-153">コマンドラインからの IIS Express の実行し、特定のポート番号を関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-153">You can run IIS Express from the command line and associate it with a specific port number.</span></span> <span data-ttu-id="7eaf7-154">要求するときに、そのポートを指定する*.cshtml*お使いのブラウザー内のファイルです。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-154">You then specify that port when you request *.cshtml* files in your browser.</span></span>

<span data-ttu-id="7eaf7-155">Windows では、管理者特権でコマンド プロンプトを開くし、変更*C:\Program Files\IIS Express です。*</span><span class="sxs-lookup"><span data-stu-id="7eaf7-155">In Windows, open a command prompt with administrator privileges and change to *C:\Program Files\IIS Express.*</span></span> <span data-ttu-id="7eaf7-156">(64 ビット システムでは、フォルダーを使用して*C:\Program Files (x86) \IIS Express です)。*サイトに実際のパスを使用して、次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-156">(For 64-bit systems, use the folder *C:\Program Files (x86)\IIS Express.)* Then enter the following command, using the actual path to your site:</span></span>

`iisexpress.exe /port:35896 /path:C:\BasicWebSite`

<span data-ttu-id="7eaf7-157">他のプロセスによって予約されていない任意のポート番号を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-157">You can use any port number that isn't already reserved by some other process.</span></span> <span data-ttu-id="7eaf7-158">(1024 より上のポート番号は、通常無料)。`path`値、web サイト フォルダーのパスを使用して場所、 *.cshtml*ファイルします。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-158">(Port numbers above 1024 are typically free.) For the `path` value, use the path of the website folder where the *.cshtml* files are.</span></span>

<span data-ttu-id="7eaf7-159">ページに提供する IIS Express をセットアップするには、このコマンドを実行した後は、ブラウザーを開きを参照、 *.cshtml*ファイル。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-159">After you run this command to set up IIS Express to serve your pages, you can open a browser and browse to a *.cshtml* file.</span></span> <span data-ttu-id="7eaf7-160">次のように URL を使用します。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-160">Use a URL like the following:</span></span>

`http://localhost:35896/default.cshtml`

<span data-ttu-id="7eaf7-161">IIS Express のコマンド ライン オプションについては、次のように入力します。`iisexpress.exe /?`コマンドライン。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-161">For help with IIS Express command line options, enter `iisexpress.exe /?` at the command line.</span></span>

<a id="Can_I_use_ASP.NET_Web_Forms_controls_on_a_Web_Pages_page"></a>
## <a name="can-i-use-aspnet-web-forms-controls-on-a-web-pages-page"></a><span data-ttu-id="7eaf7-162">ASP.NET Web フォーム ページのコントロールを Web ページを使用できますか。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-162">Can I use ASP.NET Web Forms controls on a Web Pages page?</span></span>

<span data-ttu-id="7eaf7-163">いいえ。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-163">No.</span></span> <span data-ttu-id="7eaf7-164">Web フォーム コントロールと同様に、 [ チェック ボックス](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.checkbox)コントロール、[検証コントロール](https://msdn.microsoft.com/en-us/library/bwd43d0x)、および[GridView](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.gridview) Web フォーム ページでのみ動作を制御 (*.aspx*ファイル)。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-164">Web Forms controls like the [CheckBox](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.checkbox) control, the [validation controls](https://msdn.microsoft.com/en-us/library/bwd43d0x), and the [GridView](https://msdn.microsoft.com/en-us/library/system.web.ui.webcontrols.gridview) control only work in Web Forms pages (*.aspx* files).</span></span> <span data-ttu-id="7eaf7-165">これらのコントロールでは、Web フォーム ページのフレームワークが必要です。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-165">These controls require the Web Forms page framework.</span></span>

<a id="Can_I_deploy_an_ASP.NET_Web_Pages_site_without_using_WebMatrix"></a>
## <a name="can-i-deploy-an-aspnet-web-pages-site-without-using-webmatrix"></a><span data-ttu-id="7eaf7-166">WebMatrix を使用せず、ASP.NET Web Pages サイトを配置できますか。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-166">Can I deploy an ASP.NET Web Pages site without using WebMatrix?</span></span>

<span data-ttu-id="7eaf7-167">はい。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-167">Yes.</span></span> <span data-ttu-id="7eaf7-168">(通常 FTP を使用して、サーバーに web サイトのファイルを手動でコピーすることができます。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-168">You can manually copy website files to a server (typically by using FTP).</span></span> <span data-ttu-id="7eaf7-169">手動でコピーを実行する場合は、SQL Server Compact (データベース) をサポートするファイルをコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-169">If you perform a manual copy, you also have to copy the files that support SQL Server Compact (the database).</span></span> <span data-ttu-id="7eaf7-170">詳細については、ブログ記事を参照してください。[ツールを使用せずに Web ページを展開するアプリケーション](http://mikepope.com/blog/DisplayBlog.aspx?permalink=2317)です。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-170">For details, see the blog entry [Deploying Web Pages applications without a tool](http://mikepope.com/blog/DisplayBlog.aspx?permalink=2317).</span></span>

<a id="Do_I_have_to_use_the_WebSecurity_helper_to_support_logins"></a>
## <a name="do-i-have-to-use-the-websecurity-helper-to-support-logins"></a><span data-ttu-id="7eaf7-171">ログインをサポートするために、WebSecurity ヘルパーを使用する必要がありますは?</span><span class="sxs-lookup"><span data-stu-id="7eaf7-171">Do I have to use the WebSecurity helper to support logins?</span></span>

<span data-ttu-id="7eaf7-172">いいえ。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-172">No.</span></span> <span data-ttu-id="7eaf7-173">`SimpleMembership` ASP.NET Web Pages の一部であるプロバイダーが 1 つのオプションです。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-173">The `SimpleMembership` provider that is part of ASP.NET Web Pages is one option.</span></span> <span data-ttu-id="7eaf7-174">ASP.NET (Web フォームでの操作に使用した可能性があります) の一部であるセキュリティ プロバイダーも使用できます。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-174">The security providers that are part of ASP.NET (that you might be used to working with in Web Forms) are also available.</span></span> <span data-ttu-id="7eaf7-175">たとえば、できます認証を使用するフォーム ASP.NET Web Pages で Web フォームのと同様です。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-175">For example, you can use forms authentication in ASP.NET Web Pages just as you would in Web Forms.</span></span> <span data-ttu-id="7eaf7-176">使用する方法の 1 つの例ではフォーム認証、Microsoft サポートの記事を参照してください[How To Implement Forms-Based 認証を使用して C# .NET、ASP.NET アプリケーションで](https://support.microsoft.com/kb/301240)です。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-176">For one example of how to use forms authentication, see the Microsoft Support article [How To Implement Forms-Based Authentication in Your ASP.NET Application by Using C#.NET](https://support.microsoft.com/kb/301240).</span></span> <span data-ttu-id="7eaf7-177">単純な例をダウンロードするを参照してください。[の ASP.NET のバージョン"ログイン&amp;パスワード](http://www.codeguru.com/csharp/.net/net_asp/scripting/article.php/c19295/ASPNET-version-of-Login--Password.htm)です。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-177">To download a simple example, see [ASP.NET version of "Login &amp; Password](http://www.codeguru.com/csharp/.net/net_asp/scripting/article.php/c19295/ASPNET-version-of-Login--Password.htm).</span></span>

<span data-ttu-id="7eaf7-178">Windows 認証を使用する方法については、ブログの投稿を参照してください。[を使用して Windows 認証では、ASP.NET Web Pages](http://mikepope.com/blog/DisplayBlog.aspx?permalink=2298)です。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-178">For information about how to use Windows authentication, see the blog post [Using Windows authentication in ASP.NET Web Pages](http://mikepope.com/blog/DisplayBlog.aspx?permalink=2298).</span></span>

<a id="Does_ASP.NET_Web_Pages_support_HTML5"></a>
## <a name="does-aspnet-web-pages-support-html5"></a><span data-ttu-id="7eaf7-179">ASP.NET Web Pages は HTML5 をサポートしますか。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-179">Does ASP.NET Web Pages support HTML5?</span></span>

<span data-ttu-id="7eaf7-180">はい。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-180">Yes.</span></span> <span data-ttu-id="7eaf7-181">ASP.NET Web Pages を作成するページ (*.cshtml*または*.vbhtml*ページ) も、ページが表示される前に、サーバー上で実行されるコードが含まれる HTML ページは基本的にします。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-181">The pages you create with ASP.NET Web Pages (*.cshtml* or *.vbhtml* pages) are essentially HTML pages that also contain code that runs on the server, before the page is rendered.</span></span> <span data-ttu-id="7eaf7-182">HTML5 の要素を使用して、ユーザーのブラウザーが HTML5 をサポートしている限り、 *.cshtml*または*.vbhtml*ページ。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-182">As long as the user's browser supports HTML5, you can use HTML5 elements in a *.cshtml* or *.vbhtml* page.</span></span>

<a id="Can_I_use_JavaScript_and_jQuery_with_Web_Pages"></a>
## <a name="can-i-use-javascript-and-jquery-with-web-pages"></a><span data-ttu-id="7eaf7-183">Web ページで JavaScript と jQuery を使用できますか。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-183">Can I use JavaScript and jQuery with Web Pages?</span></span>

<span data-ttu-id="7eaf7-184">もちろん、できます。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-184">Absolutely.</span></span> <span data-ttu-id="7eaf7-185">ASP.NET Web Pages を作成するページ (*.cshtml*または*.vbhtml*ページ) にサーバー コードで HTML ページだけです。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-185">The pages you create with ASP.NET Web Pages (*.cshtml* or *.vbhtml* pages) are just HTML pages with server code in them.</span></span> <span data-ttu-id="7eaf7-186">そのため、何も行うことができます、標準の HTML ページに JavaScript または jQuery を使用して行うことができますも、 *.cshtml*または*.vbhtml*ページ。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-186">Therefore, anything you can do in a normal HTML page by using JavaScript or jQuery you can also do in a *.cshtml* or *.vbhtml* page.</span></span>

<span data-ttu-id="7eaf7-187">**スターター サイト**WebMatrix でテンプレートには、多く jQuery ライブラリにはが含まれています。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-187">The **Starter Site** template in WebMatrix contains a number of jQuery libraries.</span></span> <span data-ttu-id="7eaf7-188">そのテンプレートを使用して、サイトを作成する場合、*スクリプト*フォルダーには、jQuery コア ライブラリが含まれています (*jquery 1.6.2.js)*および jQuery 検証のためのライブラリ (*jquery.validate.js*, などです。)。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-188">If you create a site by using that template, the *Scripts* folder contains a jQuery core library (*jquery-1.6.2.js)* and libraries for jQuery validation (*jquery.validate.js*, etc.).</span></span>

<span data-ttu-id="7eaf7-189">ASP.NET Web Pages を jQuery を使用する方法を説明した一部のブログ投稿を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7eaf7-189">Here are some blog posts that illustrate ways to use jQuery with ASP.NET Web Pages:</span></span>

- <span data-ttu-id="7eaf7-190">[ASP.NET Web Pages に WebMatrix を使用して jQuery 適合度を追加する](http://rachelappel.com/jquery/adding-jquery-goodness-to-asp-net-web-pages-using-webmatrix/)Rachel Appel によって</span><span class="sxs-lookup"><span data-stu-id="7eaf7-190">[Adding jQuery Goodness to ASP.NET Web Pages using WebMatrix](http://rachelappel.com/jquery/adding-jquery-goodness-to-asp-net-web-pages-using-webmatrix/) by Rachel Appel</span></span>
- <span data-ttu-id="7eaf7-191">[5 分: WebMatrix + jQuery UI + json + jQuery テンプレート](http://joeriks.com/2011/01/30/5-min-webmatrix-jquery-ui-json-jquery-templates/)Jonas Eriksson によって</span><span class="sxs-lookup"><span data-stu-id="7eaf7-191">[5 min: WebMatrix + jQuery UI + json + jQuery templates](http://joeriks.com/2011/01/30/5-min-webmatrix-jquery-ui-json-jquery-templates/) by Jonas Eriksson</span></span>
- <span data-ttu-id="7eaf7-192">[WebMatrix および jQuery フォーム](http://mikesdotnetting.com/Article/155/WebMatrix-And-jQuery-Forms)Mike Brind によって</span><span class="sxs-lookup"><span data-stu-id="7eaf7-192">[WebMatrix And jQuery Forms](http://mikesdotnetting.com/Article/155/WebMatrix-And-jQuery-Forms) by Mike Brind</span></span>

<a id="AdditionalResources"></a>
## <a name="additional-resources"></a><span data-ttu-id="7eaf7-193">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="7eaf7-193">Additional Resources</span></span>


[<span data-ttu-id="7eaf7-194">ASP.NET Web Pages (Razor) トラブルシューティング ガイド</span><span class="sxs-lookup"><span data-stu-id="7eaf7-194">ASP.NET Web Pages (Razor) Troubleshooting Guide</span></span>](https://go.microsoft.com/fwlink/?LinkId=253001)

<span data-ttu-id="7eaf7-195">[WebMatrix と ASP.NET Web Pages のフォーラム](https://forums.asp.net/1224.aspx/1?WebMatrix)ASP.NET web サイト</span><span class="sxs-lookup"><span data-stu-id="7eaf7-195">[WebMatrix and ASP.NET Web Pages forum](https://forums.asp.net/1224.aspx/1?WebMatrix) on the ASP.NET website</span></span>