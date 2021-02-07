---
description: 'Дополнительные сведения: выражения инициализации'
title: Выражения инициализации
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 02f2ea6953291641516b1daffbb2b75931ffb3cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748561"
---
# <a name="initialization-expressions"></a><span data-ttu-id="0365c-103">Выражения инициализации</span><span class="sxs-lookup"><span data-stu-id="0365c-103">Initialization Expressions</span></span>

<span data-ttu-id="0365c-104">Выражения инициализации инициализируют новый объект.</span><span class="sxs-lookup"><span data-stu-id="0365c-104">An initialization expression initializes a new object.</span></span> <span data-ttu-id="0365c-105">Поддерживается большинство выражений инициализации, в том числе большинство новых выражений инициализации языков C# 3.0 и Visual Basic 9.0.</span><span class="sxs-lookup"><span data-stu-id="0365c-105">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="0365c-106">Следующие типы могут быть инициализированы и возвращены запросом LINQ to Entities:</span><span class="sxs-lookup"><span data-stu-id="0365c-106">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
- <span data-ttu-id="0365c-107">Коллекция, которая включает ноль или больше типизированных объектов сущностей, или проекция сложных типов, которая определена в концептуальной модели.</span><span class="sxs-lookup"><span data-stu-id="0365c-107">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
- <span data-ttu-id="0365c-108">Типы CLR, поддерживаемые Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="0365c-108">CLR types supported by the Entity Framework.</span></span>
  
- <span data-ttu-id="0365c-109">Встроенные коллекции.</span><span class="sxs-lookup"><span data-stu-id="0365c-109">Inline collections.</span></span>  
  
- <span data-ttu-id="0365c-110">Анонимные типы.</span><span class="sxs-lookup"><span data-stu-id="0365c-110">Anonymous types.</span></span>  
  
 <span data-ttu-id="0365c-111">В следующем примере с синтаксисом выражения запроса показана инициализация анонимного типа:</span><span class="sxs-lookup"><span data-stu-id="0365c-111">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="0365c-112">Следующий пример с синтаксисом запроса на основе метода показывает инициализацию анонимного типа:</span><span class="sxs-lookup"><span data-stu-id="0365c-112">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="0365c-113">Также поддерживается инициализация определяемого пользователем класса.</span><span class="sxs-lookup"><span data-stu-id="0365c-113">User-defined class initialization is also supported.</span></span> <span data-ttu-id="0365c-114">Поддерживается модель инициализации языков C# 3.0 и Visual Basic 9.0 и предполагается, что метод считывания и метод задания свойства симметричны.</span><span class="sxs-lookup"><span data-stu-id="0365c-114">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="0365c-115">В следующем примере синтаксис выражения запроса показывает пользовательский класс, инициализируемый в запросе:</span><span class="sxs-lookup"><span data-stu-id="0365c-115">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="0365c-116">В следующем примере синтаксис запроса на основе метода показывает пользовательский класс, инициализируемый в запросе:</span><span class="sxs-lookup"><span data-stu-id="0365c-116">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="0365c-117">См. также</span><span class="sxs-lookup"><span data-stu-id="0365c-117">See also</span></span>

- [<span data-ttu-id="0365c-118">Выражения в запросах LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="0365c-118">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
