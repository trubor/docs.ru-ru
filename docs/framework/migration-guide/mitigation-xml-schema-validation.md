---
title: Устранение рисков. Проверка схемы XML
description: В .NET Framework 4.6 в ходе проверки XSD-схемы выявляется нарушение ограничения уникальности, если используется составной ключ и один ключ является пустым.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b73dd4f4-f2dc-47a2-9425-3896e92321fb
ms.openlocfilehash: 0744a703c1e9dc35a8accc448d34f1a736e77e4d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253535"
---
# <a name="mitigation-xml-schema-validation"></a><span data-ttu-id="94986-103">Устранение рисков. Проверка схемы XML</span><span class="sxs-lookup"><span data-stu-id="94986-103">Mitigation: XML Schema Validation</span></span>

<span data-ttu-id="94986-104">В .NET Framework 4.6 в ходе проверки XSD-схемы выявляется нарушение ограничения уникальности, если используется составной ключ и один ключ является пустым.</span><span class="sxs-lookup"><span data-stu-id="94986-104">In the .NET Framework 4.6, XSD schema validation detects a violation of the unique constraint if a compound key is used and one key is empty.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="94986-105">Последствия</span><span class="sxs-lookup"><span data-stu-id="94986-105">Impact</span></span>  

 <span data-ttu-id="94986-106">Влияние этого изменения должно быть минимальным: в зависимости от спецификации схемы ожидается ошибка проверки схемы в случае нарушения ограничения `xsd:unique` при использовании составного ключа с пустым ключом.</span><span class="sxs-lookup"><span data-stu-id="94986-106">The impact of this change should be minimal: based on the schema specification, a schema validation error is expected if `xsd:unique` is violated by using a compound key with an empty key.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="94986-107">Устранение рисков</span><span class="sxs-lookup"><span data-stu-id="94986-107">Mitigation</span></span>  

 <span data-ttu-id="94986-108">Обнаружение ошибки проверки схемы при наличии одного пустого ключа в составном ключе — это настраиваемая функция.</span><span class="sxs-lookup"><span data-stu-id="94986-108">Whether a schema validation error is detected if a compound key has one empty key is a configurable feature:</span></span>  
  
- <span data-ttu-id="94986-109">Начиная с приложений, ориентированных на .NET Framework 4.6, функция обнаружения ошибок проверки схемы включена по умолчанию, однако ее можно отключить, чтобы не выполнять обнаружение ошибок проверки схемы.</span><span class="sxs-lookup"><span data-stu-id="94986-109">Starting with the apps that target the .NET Framework 4.6, detection of the schema validation error is enabled by default; however, it is possible to opt out of it, so that the schema validation error will not be detected.</span></span>  
  
- <span data-ttu-id="94986-110">В приложениях, выполняющихся в .NET Framework 4.6, но ориентированных на .NET Framework 4.5.2 и более ранние версии платформы, обнаружение ошибок проверки схемы не выполняется по умолчанию, однако его можно включить, чтобы выполнять обнаружение ошибок проверки схемы.</span><span class="sxs-lookup"><span data-stu-id="94986-110">In apps that run under the .NET Framework 4.6 but target the .NET Framework 4.5.2 and earlier versions, a schema validation error is not detected by default; however, it is possible to opt into it, so that the schema validation error will be detected.</span></span>  
  
 <span data-ttu-id="94986-111">Это поведение можно настроить, используя класс <xref:System.AppContext> для определения значения параметра `System.Xml.IgnoreEmptyKeySequences`.</span><span class="sxs-lookup"><span data-stu-id="94986-111">This behavior can be configured by using the <xref:System.AppContext> class to define the value of the `System.Xml.IgnoreEmptyKeySequences` switch.</span></span> <span data-ttu-id="94986-112">Так как значение параметра по умолчанию — `false` (пустые последовательности ключей не игнорируются), для приложений, предназначенных для .NET Framework 4.6, можно отключить это поведение, используя следующий код для задания значения параметра `true`:</span><span class="sxs-lookup"><span data-stu-id="94986-112">Because the switch's default value is `false` (empty key sequences are not ignored), apps that target the .NET Framework 4.6 can opt out of the behavior by using the following code to set the switch's value to `true`:</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#1)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#1)]  
  
 <span data-ttu-id="94986-113">Для приложений, предназначенных для .NET Framework 4.5.2 и более ранних версий, поскольку значение параметра по умолчанию — `true` (пустые последовательности ключей игнорируются), можно гарантировать, что составной ключ с пустым ключом будет создавать ошибку проверки схемы, используя следующий код для задания значения параметра `false`.</span><span class="sxs-lookup"><span data-stu-id="94986-113">For apps that target the .NET Framework 4.5.2 and earlier versions, because the switch's default value is `true` (empty key sequences are ignored), it is possible to ensure that a compound key with an empty key does generate a schema validation error by using the following code to set the switch's value to `false`.</span></span>  
  
 [!code-csharp[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/cs/program.cs#2)]
 [!code-vb[AppCompat.IgnoreEmptyKeySequences#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.ignoreemptykeysequences/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="94986-114">См. также</span><span class="sxs-lookup"><span data-stu-id="94986-114">See also</span></span>

- [<span data-ttu-id="94986-115">Совместимость приложений</span><span class="sxs-lookup"><span data-stu-id="94986-115">Application compatibility</span></span>](application-compatibility.md)
