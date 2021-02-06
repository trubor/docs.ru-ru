---
description: Дополнительные сведения см. в статье как выполнить параметризованный Entity SQL запрос с помощью команды EntityCommand.
title: Практическое руководство. Выполнение SQL-запроса к параметрическому объекту с использованием EntityCommand
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: c3eb9fdfbad986d54104e94aa719a57edfa14b19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650785"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="e7e30-103">Практическое руководство. Выполнение SQL-запроса к параметрическому объекту с использованием EntityCommand</span><span class="sxs-lookup"><span data-stu-id="e7e30-103">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>

<span data-ttu-id="e7e30-104">В этом разделе показано, как выполнить [!INCLUDE[esql](../../../../../includes/esql-md.md)] запрос, имеющий параметры, с помощью <xref:System.Data.EntityClient.EntityCommand> объекта.</span><span class="sxs-lookup"><span data-stu-id="e7e30-104">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="e7e30-105">Выполнение кода в этом примере</span><span class="sxs-lookup"><span data-stu-id="e7e30-105">To run the code in this example</span></span>  
  
1. <span data-ttu-id="e7e30-106">Добавьте [модель AdventureWorks Sales](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) в проект и настройте проект для использования Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="e7e30-106">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="e7e30-107">Дополнительные сведения см. в разделе [инструкции. Использование мастера EDM](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e7e30-107">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="e7e30-108">На странице кода приложения добавьте следующие инструкции `using` (`Imports` в Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="e7e30-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="e7e30-109">Пример</span><span class="sxs-lookup"><span data-stu-id="e7e30-109">Example</span></span>  

 <span data-ttu-id="e7e30-110">Следующий пример показывает, как создать строку запроса с двумя параметрами.</span><span class="sxs-lookup"><span data-stu-id="e7e30-110">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="e7e30-111">Затем создается объект <xref:System.Data.EntityClient.EntityCommand>, добавляются два параметра в коллекцию <xref:System.Data.EntityClient.EntityParameter> этого объекта <xref:System.Data.EntityClient.EntityCommand> и совершается проход по элементам коллекции объектов `Contact`.</span><span class="sxs-lookup"><span data-stu-id="e7e30-111">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="e7e30-112">См. также</span><span class="sxs-lookup"><span data-stu-id="e7e30-112">See also</span></span>

- <span data-ttu-id="e7e30-113">[Практическое руководство. Выполнение параметризованного запроса](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e7e30-113">[How to: Execute a Parameterized Query](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>
- [<span data-ttu-id="e7e30-114">Язык Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e7e30-114">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
