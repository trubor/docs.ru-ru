---
title: Практическое руководство. Получение сведений о типах и членах с помощью отражения
description: Узнайте, как использовать пространство имен System.Reflection для получения сведений о типах и членах с помощью отражения.
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: 771917bb2ae5cae56c775ae23119d5eda9701df1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266328"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="b4296-103">Практическое руководство. Получение сведений о типах и членах с помощью отражения</span><span class="sxs-lookup"><span data-stu-id="b4296-103">How to: Get type and member information by using reflection</span></span>

<span data-ttu-id="b4296-104">Пространство имен <xref:System.Reflection> содержит много методов для получения сведений о типах и их членах.</span><span class="sxs-lookup"><span data-stu-id="b4296-104">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="b4296-105">В этой статье демонстрируется один из этих методов — <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4296-105">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b4296-106">Дополнительные сведения см. в разделе [Общие сведения об отражении](reflection.md).</span><span class="sxs-lookup"><span data-stu-id="b4296-106">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="b4296-107">Пример</span><span class="sxs-lookup"><span data-stu-id="b4296-107">Example</span></span>

<span data-ttu-id="b4296-108">В следующем примере демонстрируется получение сведений о типах и членах с помощью отражения:</span><span class="sxs-lookup"><span data-stu-id="b4296-108">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="b4296-109">См. также</span><span class="sxs-lookup"><span data-stu-id="b4296-109">See also</span></span>

- [<span data-ttu-id="b4296-110">Программирование с использованием доменов приложений</span><span class="sxs-lookup"><span data-stu-id="b4296-110">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="b4296-111">Отражение</span><span class="sxs-lookup"><span data-stu-id="b4296-111">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="b4296-112">Использование доменов приложений</span><span class="sxs-lookup"><span data-stu-id="b4296-112">Use application domains</span></span>](../app-domains/use.md)
