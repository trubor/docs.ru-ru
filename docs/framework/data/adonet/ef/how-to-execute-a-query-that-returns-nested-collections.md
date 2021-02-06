---
description: Дополнительные сведения см. в статье как выполнить запрос, возвращающий вложенные коллекции.
title: Практическое руководство. Выполнение запроса, возвращающего вложенные коллекции
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: 941b7471820c09224e6828fac6e17b92f70ff57e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650629"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a><span data-ttu-id="af5a9-103">Практическое руководство. Выполнение запроса, возвращающего вложенные коллекции</span><span class="sxs-lookup"><span data-stu-id="af5a9-103">How to: Execute a Query that Returns Nested Collections</span></span>

<span data-ttu-id="af5a9-104">Рассмотрим, как выполнить команду для концептуальной модели с использованием объекта <xref:System.Data.EntityClient.EntityCommand> и как получить результат с вложенной коллекцией при использовании <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="af5a9-104">This shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the nested collection results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="af5a9-105">Выполнение кода в этом примере</span><span class="sxs-lookup"><span data-stu-id="af5a9-105">To run the code in this example</span></span>  
  
1. <span data-ttu-id="af5a9-106">Добавьте [модель AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) в проект и настройте проект для использования Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="af5a9-106">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="af5a9-107">Дополнительные сведения см. в разделе [инструкции. Использование мастера EDM](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="af5a9-107">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="af5a9-108">На странице кода приложения добавьте следующие инструкции `using` (`Imports` в Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="af5a9-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="af5a9-109">Пример</span><span class="sxs-lookup"><span data-stu-id="af5a9-109">Example</span></span>  

 <span data-ttu-id="af5a9-110">*Вложенная коллекция* — это коллекция, которая находится внутри другой коллекции.</span><span class="sxs-lookup"><span data-stu-id="af5a9-110">A *nested collection* is a collection that is inside another collection.</span></span> <span data-ttu-id="af5a9-111">В следующем коде происходит получение коллекции `Contacts` и вложенных коллекций `SalesOrderHeaders`, которые связаны с каждым объектом `Contact`.</span><span class="sxs-lookup"><span data-stu-id="af5a9-111">The following code retrieves a collection of `Contacts` and the nested collections of `SalesOrderHeaders` that are associated with each `Contact`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="af5a9-112">См. также</span><span class="sxs-lookup"><span data-stu-id="af5a9-112">See also</span></span>

- [<span data-ttu-id="af5a9-113">Поставщик EntityClient для Entity Framework</span><span class="sxs-lookup"><span data-stu-id="af5a9-113">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
