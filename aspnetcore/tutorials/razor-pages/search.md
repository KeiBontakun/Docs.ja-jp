---
title: "ASP.NET Core Razor ページへの検索の追加"
author: rick-anderson
description: "ASP.NET Core Razor ページに検索を追加する方法を紹介します"
ms.author: riande
manager: wpickett
ms.date: 08/07/2017
ms.topic: get-started-article
ms.technology: aspnet
ms.prod: asp.net-core
uid: tutorials/razor-pages/search
ms.openlocfilehash: 7a9287dedf75530dc1345a54e24c3bfe6fb50bbe
ms.sourcegitcommit: 060879fcf3f73d2366b5c811986f8695fff65db8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="adding-search-to-a-razor-pages-app"></a>Razor ページ アプリへの検索の追加

作成者: [Rick Anderson](https://twitter.com/RickAndMSFT)

この記事では、ムービーを*ジャンル*や*題名*で検索できるように検索機能を索引ページに追加しています。

索引ページの `OnGetAsync` メソッドを次のコードに変更します。

[!code-csharp[Main](razor-pages-start/sample/RazorPagesMovie/Pages/Movies/Index.cshtml.cs?name=snippet_1stSearch)]

`OnGetAsync` メソッドの最初の行により、ムービーを選択する [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/) クエリが作成されます。

```csharp
var movies = from m in _context.Movie
             select m;
```

このクエリはこの時点で*のみ*定義されます。データベースに対して**実行されていません**。

`searchString` パラメーターに文字列が含まれる場合、検索文字列で絞り込むようにムービークエリが変更されます。

[!code-csharp[Main](razor-pages-start/sample/RazorPagesMovie/Pages/Movies/Index.cshtml.cs?name=snippet_SearchNull)]

`s => s.Title.Contains()` コードは[ラムダ式](https://docs.microsoft.com/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions)です。 ラムダは、メソッド ベースの [LINQ](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/) クエリで、[Where](https://docs.microsoft.com/dotnet/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq) メソッドや `Contains` (先のコードで使用されています) など、標準クエリ演算子メソッドの引数として使用されます。 LINQ クエリは、`Where`、`Contains`、`OrderBy` などのメソッドの呼び出しで定義または変更されたときには実行されません。 クエリ実行は先送りされます。 つまり、その具体値が繰り返されるか、`ToListAsync` メソッドが呼び出されるまで、式の評価が延ばされます。 詳細については、「[クエリ実行](https://docs.microsoft.com/dotnet/framework/data/adonet/ef/language-reference/query-execution)」を参照してください。

**注:** [Contains](https://docs.microsoft.com//dotnet/api/system.data.objects.dataclasses.entitycollection-1.contains) メソッドは C# コードではなく、データベースで実行されます。 クエリの大文字と小文字の区別は、データベースや照合順序に依存します。 SQL Server では、`Contains` は大文字/小文字の区別がない [SQL LIKE](https://docs.microsoft.com/sql/t-sql/language-elements/like-transact-sql) にマッピングされます。 SQLite では、既定の照合順序で、大文字と小文字が区別されます。

ムービーページに移動し、`?searchString=Ghost` のようなクエリ文字列を URL に追加します (例: `http://localhost:5000/Movies?searchString=Ghost`)。 フィルターされたムービーが表示されます。

![インデックス ビュー](search/_static/ghost.png)

次のルート テンプレートが索引ページに追加される場合、検索文字列を URL セグメントとして渡すことができます (例: `http://localhost:5000/Movies/ghost`)。

```cshtml
@page "{searchString?}"
```

先のルート制約では、クエリ文字列値の代わりに、ルート データ (URL セグメント) として題名を検索できます。  `"{searchString?}"` の `?` は、これが任意のルート パラメーターであることを意味します。

![ghost という単語が URL に追加された索引ビュー。Ghostbusters と Ghostbusters 2 という 2 本のムービーからなるムービーリストが返されています。](search/_static/g2.png)

ただし、URL を変更してムービーを検索することをユーザーに求めることはできません。 この手順では、ムービーを絞り込むための UI を追加します。 ルート制約 `"{searchString?}"` を追加した場合、それを削除します。

*Pages/Movies/Index.cshtml* ファイルを開き、次のコードで強調表示されている `<form>` マークアップを追加します。

[!code-cshtml[Main](razor-pages-start/sample/RazorPagesMovie/Pages/Movies/Index2.cshtml?highlight=14-19&range=1-22)]

HTML `<form>` タグは[フォーム タグ ヘルパー](xref:mvc/views/working-with-forms#the-form-tag-helper)を使用します。 フォームが提出されると、フィルター文字列が*ページ/ムービー/索引*ページに送信されます。 変更を保存し、フィルターをテストします。

![タイトル フィルター テキストボックスに ghost という単語が入力されたインデックス ビュー](search/_static/filter.png)

## <a name="search-by-genre"></a>ジャンルで検索する

強調表示されている次のプロパティを *Pages/Movies/Index.cshtml.cs* に追加します。

[!code-csharp[Main](razor-pages-start/sample/RazorPagesMovie/Pages/Movies/Index.cshtml.cs?name=snippet_newProps&highlight=11-)]

`SelectList Genres` には、ジャンル一覧が含まれます。 これにより、ユーザーは一覧からジャンルを選択できます。

`MovieGenre` プロパティには、"Western (西部劇)" など、ユーザーが選択する特定のジャンルが含まれます。

`OnGetAsync` メソッドを次のコードで更新します。

[!code-csharp[Main](razor-pages-start/sample/RazorPagesMovie/Pages/Movies/Index.cshtml.cs?name=snippet_SearchGenre)]

次のコードは、データベースからすべてのジャンルを取得する LINQ クエリです。

[!code-csharp[Main](razor-pages-start/sample/RazorPagesMovie/Pages/Movies/Index.cshtml.cs?name=snippet_LINQ)]

ジャンルの `SelectList` は、別個のジャンルを推定することで作成されます。

<!-- BUG in OPS
Tag snippet_selectlist's start line '75' should be less than end line '29' when resolving "[!code-csharp[Main](razor-pages-start/sample/RazorPagesMovie/Pages/Movies/Index.cshtml.cs?name=snippet_SelectList)]"

There's no start line.

[!code-csharp[Main](razor-pages-start/sample/RazorPagesMovie/Pages/Movies/Index.cshtml.cs?name=snippet_SelectList)]
-->

```csharp
Genres = new SelectList(await genreQuery.Distinct().ToListAsync());
```

### <a name="adding-search-by-genre"></a>ジャンルによる検索の追加

*Index.cshtml* を次のように変更します。

[!code-cshtml[Main](razor-pages-start/sample/RazorPagesMovie/Pages/Movies/IndexFormGenreNoRating.cshtml?highlight=16-18&range=1-26)]

ジャンルまたはムービーのタイトル、あるいはその両方で検索して、アプリをテストします。

>[!div class="step-by-step"]
[前: ページの更新](xref:tutorials/razor-pages/da1)
[次: 新しいフィールドの追加](xref:tutorials/razor-pages/new-field)
