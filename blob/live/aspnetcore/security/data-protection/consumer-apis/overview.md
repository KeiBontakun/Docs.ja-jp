---
title: "コンシューマー Api の概要"
author: rick-anderson
description: "このドキュメントでは、さまざまなコンシューマー ASP.NET Core data protection ライブラリ内で利用可能な Api の簡単な概要を説明します。"
ms.author: riande
manager: wpickett
ms.date: 10/14/2016
ms.topic: article
ms.technology: aspnet
ms.prod: asp.net-core
uid: security/data-protection/consumer-apis/overview
ms.openlocfilehash: 5ec11dce3ba485a84b6ce5f7ddaf16430162659c
ms.sourcegitcommit: 3e303620a125325bb9abd4b2d315c106fb8c47fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="consumer-apis-overview"></a><span data-ttu-id="89985-103">コンシューマー Api の概要</span><span class="sxs-lookup"><span data-stu-id="89985-103">Consumer APIs overview</span></span>

<span data-ttu-id="89985-104">`IDataProtectionProvider`と`IDataProtector`インターフェイスは、コンシューマーを使用するには、データ保護システムを使用して、基本インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="89985-104">The `IDataProtectionProvider` and `IDataProtector` interfaces are the basic interfaces through which consumers use the data protection system.</span></span> <span data-ttu-id="89985-105">内にある、 [Microsoft.AspNetCore.DataProtection.Abstractions](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.Abstractions/)パッケージです。</span><span class="sxs-lookup"><span data-stu-id="89985-105">They are located in the [Microsoft.AspNetCore.DataProtection.Abstractions](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.Abstractions/) package.</span></span>

## <a name="idataprotectionprovider"></a><span data-ttu-id="89985-106">IDataProtectionProvider</span><span class="sxs-lookup"><span data-stu-id="89985-106">IDataProtectionProvider</span></span>

<span data-ttu-id="89985-107">プロバイダーのインターフェイスでは、データ保護システムのルートを表します。</span><span class="sxs-lookup"><span data-stu-id="89985-107">The provider interface represents the root of the data protection system.</span></span> <span data-ttu-id="89985-108">保護やデータ保護の解除を直接使用できません。</span><span class="sxs-lookup"><span data-stu-id="89985-108">It cannot directly be used to protect or unprotect data.</span></span> <span data-ttu-id="89985-109">代わりに、コンシューマーがへの参照を取得する必要があります、`IDataProtector`を呼び出して`IDataProtectionProvider.CreateProtector(purpose)`ここで、目的は、目的のコンシューマーのユース ケースを説明する文字列。</span><span class="sxs-lookup"><span data-stu-id="89985-109">Instead, the consumer must get a reference to an `IDataProtector` by calling `IDataProtectionProvider.CreateProtector(purpose)`, where purpose is a string that describes the intended consumer use case.</span></span> <span data-ttu-id="89985-110">参照してください[目的文字列](purpose-strings.md)を目的として、このパラメーターの適切な値を選択する方法についてははるかにします。</span><span class="sxs-lookup"><span data-stu-id="89985-110">See [Purpose Strings](purpose-strings.md) for much more information on the intent of this parameter and how to choose an appropriate value.</span></span>

## <a name="idataprotector"></a><span data-ttu-id="89985-111">IDataProtector</span><span class="sxs-lookup"><span data-stu-id="89985-111">IDataProtector</span></span>

<span data-ttu-id="89985-112">保護機能のインターフェイスへの呼び出しによって返される`CreateProtector`であり、コンシューマーは、実行に使用できるこのインターフェイスは、保護し、操作の保護を解除します。</span><span class="sxs-lookup"><span data-stu-id="89985-112">The protector interface is returned by a call to `CreateProtector`, and it is this interface which consumers can use to perform protect and unprotect operations.</span></span>

<span data-ttu-id="89985-113">一部のデータを保護するデータの渡し、`Protect`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="89985-113">To protect a piece of data, pass the data to the `Protect` method.</span></span> <span data-ttu-id="89985-114">どの変換 byte[] -> byte[]、メソッドを定義する基本インターフェイスですがありますも、オーバー ロード (拡張メソッドとして提供) の文字列に変換する文字列]-> [です。</span><span class="sxs-lookup"><span data-stu-id="89985-114">The basic interface defines a method which converts byte[] -> byte[], but there is also an overload (provided as an extension method) which converts string -> string.</span></span> <span data-ttu-id="89985-115">2 つの方法で提供されるセキュリティは同じです。開発者は、いずれかのオーバー ロードは、ユース ケースに対して最も便利な方法を選択してください。</span><span class="sxs-lookup"><span data-stu-id="89985-115">The security offered by the two methods is identical; the developer should choose whichever overload is most convenient for their use case.</span></span> <span data-ttu-id="89985-116">選択すると、オーバー ロードの保護によって返される値に関係なくメソッドはようになりました (enciphered および不正使用防止機能も使用可能な)、および保護アプリケーションを使用すると、信頼されていないクライアントに送信できます。</span><span class="sxs-lookup"><span data-stu-id="89985-116">Irrespective of the overload chosen, the value returned by the Protect method is now protected (enciphered and tamper-proofed), and the application can send it to an untrusted client.</span></span>

<span data-ttu-id="89985-117">保護されていた一部のデータの保護を解除する保護されたデータの渡し、`Unprotect`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="89985-117">To unprotect a previously-protected piece of data, pass the protected data to the `Unprotect` method.</span></span> <span data-ttu-id="89985-118">(Byte[] がある-開発者の利便性のためのベースと文字列ベースのオーバー ロードします)。保護されたペイロードは、事前に呼び出したによって生成された場合`Protect`この同じ`IDataProtector`、`Unprotect`メソッドは、元の保護されていないペイロードを返します。</span><span class="sxs-lookup"><span data-stu-id="89985-118">(There are byte[]-based and string-based overloads for developer convenience.) If the protected payload was generated by an earlier call to `Protect` on this same `IDataProtector`, the `Unprotect` method will return the original unprotected payload.</span></span> <span data-ttu-id="89985-119">保護されたペイロードが改ざんされたまたは異なるによって生成されたかどうか`IDataProtector`、 `Unprotect` CryptographicException をスローします。</span><span class="sxs-lookup"><span data-stu-id="89985-119">If the protected payload has been tampered with or was produced by a different `IDataProtector`, the `Unprotect` method will throw CryptographicException.</span></span>

<span data-ttu-id="89985-120">異なると同じ概念`IDataProtector`ties が目的の概念をバックアップします。</span><span class="sxs-lookup"><span data-stu-id="89985-120">The concept of same vs. different `IDataProtector` ties back to the concept of purpose.</span></span> <span data-ttu-id="89985-121">場合は、次の 2 つ`IDataProtector`インスタンスが同じルートから生成された`IDataProtectionProvider`がへの呼び出しでそれぞれ異なる目的の文字列を使用して`IDataProtectionProvider.CreateProtector`と見なされますし、[異なるプロテクター](purpose-strings.md)、し、保護を解除する 1 つはできません他のによって生成されるペイロード。</span><span class="sxs-lookup"><span data-stu-id="89985-121">If two `IDataProtector` instances were generated from the same root `IDataProtectionProvider` but via different purpose strings in the call to `IDataProtectionProvider.CreateProtector`, then they are considered [different protectors](purpose-strings.md), and one will not be able to unprotect payloads generated by the other.</span></span>

## <a name="consuming-these-interfaces"></a><span data-ttu-id="89985-122">これらのインターフェイスを使用</span><span class="sxs-lookup"><span data-stu-id="89985-122">Consuming these interfaces</span></span>

<span data-ttu-id="89985-123">コンポーネントがかかることが目的の使用方法、DI に対応するコンポーネントです、`IDataProtectionProvider`コンス トラクターのパラメーターと、コンポーネントがインスタンス化されるとき、DI システムがそのこのサービスを自動的に提供します。</span><span class="sxs-lookup"><span data-stu-id="89985-123">For a DI-aware component, the intended usage is that the component take an `IDataProtectionProvider` parameter in its constructor and that the DI system automatically provides this service when the component is instantiated.</span></span>

> [!NOTE]
> <span data-ttu-id="89985-124">一部のアプリケーション (コンソール アプリケーション、ASP.NET 4.x アプリケーションなど) があります DI に対応するため、ここで説明する機構を使用できません。</span><span class="sxs-lookup"><span data-stu-id="89985-124">Some applications (such as console applications or ASP.NET 4.x applications) might not be DI-aware so cannot use the mechanism described here.</span></span> <span data-ttu-id="89985-125">これらのシナリオを参照してください、[非 DI 対応したシナリオ](../configuration/non-di-scenarios.md)のインスタンスの取得の詳細については、ドキュメント、 `IDataProtection` DI を経由せずプロバイダー。</span><span class="sxs-lookup"><span data-stu-id="89985-125">For these scenarios consult the [Non DI Aware Scenarios](../configuration/non-di-scenarios.md) document for more information on getting an instance of an `IDataProtection` provider without going through DI.</span></span>

<span data-ttu-id="89985-126">次の例では、3 つの概念を示しています。</span><span class="sxs-lookup"><span data-stu-id="89985-126">The following sample demonstrates three concepts:</span></span>

1. <span data-ttu-id="89985-127">[データ保護システムに追加する](../configuration/overview.md)サービス コンテナー</span><span class="sxs-lookup"><span data-stu-id="89985-127">[Adding the data protection system](../configuration/overview.md) to the service container,</span></span>

2. <span data-ttu-id="89985-128">インスタンスを受信する DI を使用して、 `IDataProtectionProvider`、および</span><span class="sxs-lookup"><span data-stu-id="89985-128">Using DI to receive an instance of an `IDataProtectionProvider`, and</span></span>

3. <span data-ttu-id="89985-129">作成する、`IDataProtector`から、`IDataProtectionProvider`を保護し、データ保護の解除に使用するとします。</span><span class="sxs-lookup"><span data-stu-id="89985-129">Creating an `IDataProtector` from an `IDataProtectionProvider` and using it to protect and unprotect data.</span></span>

[!code-csharp[Main](../using-data-protection/samples/protectunprotect.cs?highlight=26,34,35,36,37,38,39,40)]

<span data-ttu-id="89985-130">Microsoft.AspNetCore.DataProtection.Abstractions パッケージには、拡張メソッドが含まれています。`IServiceProvider.GetDataProtector`開発者便宜を図っています。</span><span class="sxs-lookup"><span data-stu-id="89985-130">The package Microsoft.AspNetCore.DataProtection.Abstractions contains an extension method `IServiceProvider.GetDataProtector` as a developer convenience.</span></span> <span data-ttu-id="89985-131">カプセル化単一の操作として両方を取得する、`IDataProtectionProvider`したサービス プロバイダーと呼び出し元から`IDataProtectionProvider.CreateProtector`です。</span><span class="sxs-lookup"><span data-stu-id="89985-131">It encapsulates as a single operation both retrieving an `IDataProtectionProvider` from the service provider and calling `IDataProtectionProvider.CreateProtector`.</span></span> <span data-ttu-id="89985-132">次の例では、その使用法を示します。</span><span class="sxs-lookup"><span data-stu-id="89985-132">The following sample demonstrates its usage.</span></span>

[!code-csharp[Main](./overview/samples/getdataprotector.cs?highlight=15)]

>[!TIP]
> <span data-ttu-id="89985-133">インスタンス`IDataProtectionProvider`と`IDataProtector`は複数の呼び出し元のスレッド セーフです。</span><span class="sxs-lookup"><span data-stu-id="89985-133">Instances of `IDataProtectionProvider` and `IDataProtector` are thread-safe for multiple callers.</span></span> <span data-ttu-id="89985-134">したらコンポーネントへの参照を取得するためのものを`IDataProtector`呼び出しを経由して`CreateProtector`、その参照に複数の呼び出しは使用`Protect`と`Unprotect`です。</span><span class="sxs-lookup"><span data-stu-id="89985-134">It is intended that once a component gets a reference to an `IDataProtector` via a call to `CreateProtector`, it will use that reference for multiple calls to `Protect` and `Unprotect`.</span></span> <span data-ttu-id="89985-135">呼び出し`Unprotect`保護されているペイロードを検証または解読できない場合 CryptographicException がスローされます。</span><span class="sxs-lookup"><span data-stu-id="89985-135">A call to `Unprotect` will throw CryptographicException if the protected payload cannot be verified or deciphered.</span></span> <span data-ttu-id="89985-136">一部のコンポーネントがエラーを無視することも中に保護を解除します。認証 cookie が読み取られますコンポーネント可能性がありますこのエラーを処理およびこれがなかった cookie まったくかのように、要求を処理ではなく完全要求に失敗します。</span><span class="sxs-lookup"><span data-stu-id="89985-136">Some components may wish to ignore errors during unprotect operations; a component which reads authentication cookies might handle this error and treat the request as if it had no cookie at all rather than fail the request outright.</span></span> <span data-ttu-id="89985-137">この動作をするコンポーネントは、すべての例外を受け入れるではなく CryptographicException をキャッチする必要があります具体的には。</span><span class="sxs-lookup"><span data-stu-id="89985-137">Components which want this behavior should specifically catch CryptographicException instead of swallowing all exceptions.</span></span>