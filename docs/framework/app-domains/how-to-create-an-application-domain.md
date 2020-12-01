---
title: Практическое руководство. Создание домена приложения
description: Узнайте о том, как создать домен приложения в .NET. Вы можете создать домен приложения, чтобы загрузить сборки и управлять ими лично, или создать сборку для выполнения кода.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
ms.openlocfilehash: fb022511ee395a9312e4dbaf7c0beee03c9b4569
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264092"
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="dcee6-104">Практическое руководство. Создание домена приложения</span><span class="sxs-lookup"><span data-stu-id="dcee6-104">How to: Create an Application Domain</span></span>

<span data-ttu-id="dcee6-105">Хост-приложение CLR автоматически создает домены приложений в нужный момент.</span><span class="sxs-lookup"><span data-stu-id="dcee6-105">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="dcee6-106">Но можно создать собственные домены приложений и загрузить их в те сборки, которыми требуется управлять отдельно.</span><span class="sxs-lookup"><span data-stu-id="dcee6-106">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="dcee6-107">Кроме того, домены приложений можно создать из доменов, выполняющих код.</span><span class="sxs-lookup"><span data-stu-id="dcee6-107">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="dcee6-108">Создать домен приложения можно с помощью одного из перегруженных методов **CreateDomain** в классе <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dcee6-108">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="dcee6-109">Для домена приложения можно назначить имя и использовать его в ссылках на домен.</span><span class="sxs-lookup"><span data-stu-id="dcee6-109">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="dcee6-110">В следующем примере создается новый домен приложения, которому назначается имя `MyDomain`, после чего на консоль выводятся имя основного домена и нового созданного дочернего домена приложения.</span><span class="sxs-lookup"><span data-stu-id="dcee6-110">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcee6-111">Пример</span><span class="sxs-lookup"><span data-stu-id="dcee6-111">Example</span></span>  

 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="dcee6-112">См. также</span><span class="sxs-lookup"><span data-stu-id="dcee6-112">See also</span></span>

- [<span data-ttu-id="dcee6-113">Программирование с использованием доменов приложений</span><span class="sxs-lookup"><span data-stu-id="dcee6-113">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="dcee6-114">Использование доменов приложений</span><span class="sxs-lookup"><span data-stu-id="dcee6-114">Using Application Domains</span></span>](use.md)
